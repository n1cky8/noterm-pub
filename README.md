### Introduction to Noterm

Noterm (short for "notes + terminal") is a notes-as-code tool that allows you to manage notes and execute OS and SQL commands from a single point, directly within a text file without the need for manual copying and pasting.

### Installation

To install and run Noterm on your system download the latest release, extract the contents of the ZIP file to a directory on your system and run the executable :
  - On Windows: `noterm.exe`
  - On MacOS: `Noterm.app`

### Terminology and syntax

Noterm incorporates specific terminology to improve understanding and functionality within the application:

- **@verb** Denotes an action or verb.
- **alias** Represents an alias (a short, user-defined name).
- **"banner"** Indicates a banner, enclosed in double quotes.
- **(parameter)** Encloses a parameter within parentheses.
- **#tag** Specifies a tag name or flag preceded by a hash symbol.
- **:** Separates the preceding elements from the content or operation.
- **content or operation** Contains additional information, content, or an operation.

#### Syntax 1: Embed - Single Line Format

```
<% `@verb` `alias` `"banner"` `(parameter)` `#tagname` : `content or operation` %>
```

#### Syntax 2: Embed - Multi Line Format

```
<% `@verb` `alias` `"banner"` `(parameter)` `#tagname` :
    `content or operation`
%>
```

#### Syntax 3: Annotations

```
<% `@verb` `alias` `"banner"` `(parameter)` `#tagname` %>
`content or operation`
```

### Command Execution in Noterm

Noterm allows for executing commands directly within the editor interface using specific syntax. Below are examples of command execution syntax in Noterm:

#### General Command Execution

To execute a general command with a specific directory path in Noterm, use the following syntax:

```
<% @cmd (/path/to/directory) : git status %>
```

Replace `/path/to/directory` with the desired directory path where the `git status` command should be executed.

#### Kubernetes Command Execution

For executing Kubernetes commands in Noterm, use the following syntax without specifying a directory parameter:

```
<% @cmd : kubectl get pods %>
```

This command executes `kubectl get pods` at the current directory location.

#### SQL Command Execution

To execute SQL commands with a defined database connection in Noterm, use the following syntax:

```
<% @var db #postgres : postgres://username:password@localhost:5432/dbname %>
<% @sql ($db) : SELECT * FROM table_name %>
```

Replace `postgres://username:password@localhost:5432/dbname` with your database connection URL.

Use the #postgres tag to specify the PostgreSQL driver. Other supported database drivers include #mysql #clickhouse and #sqlite3.

#### Using Variables for Commands

Noterm supports using variables to define parameters for commands. For example, defining a database connection as a variable and using it in an SQL command:

```
<% @var db #postgres : "postgres://username:password@localhost:5432/dbname" %>
<% @sql ($db) : SELECT * FROM table_name; %>
```

#### Using @cmd Directive with Tags

The `@cmd` directive in Noterm supports additional tags to customize command execution:

- **#run**: Executes the command in the background without piping standard output. Example:

  ```
  <% @cmd #run : long-running-command %>
  ```

#### Using @sql Directive with Tags

When executing SQL commands (`@sql`) in Noterm, specific tags can be used based on the expected outcome:

- **#retrieve**: Use when the command is expected to return records, such as `SELECT` statements. Example:

  ```
  <% @sql #retrieve ($db) : SELECT * FROM table_name; %>
  ```

- **Forcing Fetch**: Certain operations like `DESC <table>` or calling stored procedures may require forcing the fetch (`#retrieve`) tag if the outcome is uncertain. Example:

  ```
  <% @sql #retrieve ($db) : DESC table_name; %>
  ```

Using these tags and directives with the `@cmd` and `@sql` directives allows for precise control and behavior when executing commands within Noterm, optimizing command execution for various scenarios and outcomes. Experiment with these tags to streamline your workflow and handle command execution effectively.

---

### Using Cookie Files

The key feature of "cookie" files is the ability to dynamically leverage the file path (`.`) within snippets.

#### How It Works

When writing a code snippet in a "cookie" file, you can use the dot (`.`) as a placeholder to represent the path of the file where the "cookie" file is being used. This allows you to write generic and reusable code snippets that automatically adapt to the current file's location.

#### Example

Here's an example of how you might use the file path (`.`) in a Noterm "cookie" file:

```
<% @cmd (.) : git status %>
```

This Git command example (`git status`) will be executed in the current file's location.

#### Advantages

- **Flexibility**: Reusable code snippets that automatically adapt to the file's location.
- **Ease of Use**: Intuitive use of the file path to write more dynamic code snippets.
- **Efficiency**: Increased adaptability of code snippets based on the current file's location.

---

## Using Noterm Snippets for Command Execution

In Noterm, you can easily execute commands embedded within snippets directly from a text file. Here's how you can execute commands using keyboard shortcuts or by clicking on line numbers:

### Keyboard Shortcut Execution

1. **Navigate to Snippet**: Position your cursor within the snippet containing the command you wish to execute.
   
2. **Execute Command**: Press `Command + Enter` (Mac) or `Ctrl + Enter` (Windows/Linux) to execute the command.

This keyboard shortcut allows you to quickly execute commands without leaving the editor interface, enhancing your workflow efficiency.

### Click-to-Execute (Line Numbers)

1. **Identify Command**: Locate the line number corresponding to the command you want to execute within the snippet.

2. **Execute Command**: Click on the line number associated with the command to execute it directly.

---

## Important UI Features

Below are key UI features that users should be aware of for efficient navigation and file management.

## Opening Files in a New Directory

To open a file in a different directory, use a **long-click** action on the file. Follow these steps:

1. Navigate to the file you want to open.
2. Perform a **long-click** (press and hold) on the file icon or name.
3. A new page will open displaying the file's contents in the selected directory.

## Displaying the Sidebar

Access the sidebar by performing a **long-click** on the **back button**. Here's how:

1. Press and hold (long-click) the **back button** of your device.
2. The sidebar will slide in, providing navigation links without leaving the current page.

### Keyboard Shortcuts

Noterm provides convenient keyboard shortcuts to streamline your workflow:

- **Command/Ctrl + .**: Prompts focus.
- **Command/Ctrl + Escape**: Closes the page.
- **Command/Ctrl + n**: Appends an editor.
- **Command/Ctrl + t**: Appends a new page.
- **Command/Ctrl + s**: Saves the page.
- **Command/Ctrl + e**: Erases the page (in an editor, clears the terminal).
- **Command/Ctrl + l**: Switches the layout (show/hide terminal).
- **Command/Ctrl + k**: Toggles the aside.
- **Command/Ctrl + b**: Switches the page backward (with an optional Shift modifier to switch forward).
- **Command/Ctrl + z**: Toggles zoom.

### Prompt Functionality

Noterm's prompt allows for loading pages that manage different file types within the editor interface:

- **Directory Input**: Entering a directory path loads a file system manager page, enabling navigation and interaction with files and directories.
  
- **Text File Input**: Inputting a text file path opens an integrated text editor page for note-taking and content editing.
  
- **Image File Input**: Providing an image file path displays the image within the Noterm interface, allowing visual content viewing directly in the editor.

Additionally, using specific options with the prompt allows for file and folder management:

- **Create File**: Use `<file> :nf` to create a new file with the specified name.
  
- **Create Directory**: Use `<path> :nd` to create a new directory at the specified path.
  
- **Delete File or Directory**: Utilize `<file/path> :d` to delete a specified file or directory.
