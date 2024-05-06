### Introduction to Noterm

Noterm is a unique text editor that integrates note-taking with an embedded terminal, enabling seamless execution of OS commands and SQL queries directly within the editor interface. Embrace the efficiency of treating notes as executable code with Noterm's powerful features.

Key aspects of Noterm include:

- **Text Editing**: Enjoy a familiar and intuitive text editor interface for creating and modifying notes.
- **Integrated Terminal**: Execute operating system commands and SQL queries without leaving the editor.
- **Efficient Workflow**: Combine note-taking and command execution within the same environment.

With Noterm, users can transition seamlessly between writing notes and executing commands, enhancing productivity and workflow integration. Explore the capabilities of "notes as code" with this versatile text editor!

### Installation

To install and run Noterm on your system, follow these steps:

1. **Download Noterm**:
   - Visit the official Noterm website to download the latest release.

2. **Extract the ZIP File**:
   - Once downloaded, extract the contents of the ZIP file to a directory on your system.

3. **Navigate to the Directory**:
   - Open a terminal or command prompt.

4. **Launch Noterm**:
   - Change directory (`cd`) to the location where you extracted the Noterm files.
   - Run the executable:
     - On Windows: Execute `noterm.exe`
     - On Linux/macOS: Run `./noterm`

### Terminology

Noterm incorporates specific terminology to improve understanding and functionality within the application:

- **@verb** Denotes an action or verb.
- **alias** Represents an alias (a short, user-defined name).
- **"banner"** Indicates a banner, enclosed in double quotes.
- **(parameter)** Encloses a parameter within parentheses.
- **#tag** Specifies a tag name or flag preceded by a hash symbol.
- **:** Separates the preceding elements from the content or operation.
- **content or operation** Contains additional information, content, or an operation.

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


