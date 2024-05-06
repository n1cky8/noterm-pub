## Noterm: Notes as Code

Noterm is a unique text editor that integrates note-taking with an embedded terminal, enabling seamless execution of OS commands and SQL queries directly within the editor interface. Discover the efficiency of treating notes as executable code with Noterm's powerful features.

### Key Features

- **Text Editing**: Write and edit notes using a familiar and intuitive text editor interface.
- **Integrated Terminal**: Execute operating system commands and SQL queries without leaving the editor.
- **Efficient Workflow**: Combine note-taking and command execution within the same environment.
- **Cross-Platform**: Works on various operating systems without complex dependencies.
- **Portable Installation**: Easily launch Noterm from a downloaded executable.

### Installation

1. **Download and Unzip**:
   - Obtain the latest release of Noterm.
   - Extract the downloaded ZIP file to a directory on your system.

2. **Run Noterm**:
   - Navigate to the extracted directory.
   - Launch Noterm by running the executable file (`noterm.exe` on Windows or `noterm` on Linux/macOS).

### Usage

1. **Opening Noterm**:
   - Double-click the Noterm executable to start the application.

2. **Text Editing**:
   - Use the integrated text editor to create, view, and modify notes.

3. **Executing Commands**:
   - Execute OS commands or SQL queries directly from the editor:
     - Click on a line number to execute the entire line as a command.
     - Alternatively, position the cursor within a snippet and press `Ctrl + Enter` to execute.

4. **Terminal and Editor Interface**:
   - Noterm features a split-screen interface with the text editor and terminal side by side.
   - Quickly switch between editing notes and running commands without switching applications.

5. **User Interface (UI)**:
   - **Sidebar**: Functions like a tab bar, displaying a list of pages for easy switching.
   - **Page Area**: Contains an editable prompt at the top, displaying the path of the current page (directory, file, or unsaved buffer).
     - **Navigation Buttons**: Located beside the prompt, these buttons allow browsing pages (backward only) and closing the current page.
     - **Long-Press Action**: Long-clicking the back button toggles the visibility of the sidebar.

6. **Opening Pages**:
   - Enter a path in the prompt and press `Enter` to load the page.
   - If a directory is entered, the file system browser (referred to as "Finder") is displayed.
   - Text files are opened in the editor automatically (only recognized file types; unrecognized files prompt for opening mode).
   - Long-pressing an item in the Finder (both directory and file) opens it in a new page.

7. **Supported File Types**:
   - Currently displays text files and images (future versions may support ZIP file handling).

### Terminology

- **@verb**: Denotes an action or verb.
- **alias**: Represents an alias (a short, user-defined name).
- **"banner"**: Indicates a banner, enclosed in double quotes.
- **(parameter)**: Encloses a parameter within parentheses.
- **#tag**: Specifies a tagname (or flag) preceded by a hash symbol.
- **:**: Separates the preceding elements from the content or operation.
- **content or operation**: Contains additional information, content, or an operation.

### Syntax Examples

**Embed - Single Line Format**
```
<% @verb alias "banner" (parameter) #tag : content or operation %>
```

**Embed - Multi Line Format**
```
<% @verb alias "banner" (parameter) #tag :
content or operation
%>
```

**Annotation Format**
```
<% @verb alias "banner" (parameter) #tag %>
content or operation
```

### Keyboard Shortcuts

- `Command/Ctrl + .`: Prompts focus.
- `Command/Ctrl + Escape`: Closes the page.
- `Command/Ctrl + n`: Appends an editor.
- `Command/Ctrl + t`: Appends a new page.
- `Command/Ctrl + s`: Saves the page.
- `Command/Ctrl + e`: Erases the page (in an editor, clears the terminal).
- `Command/Ctrl + l`: Switches the layout (show/hide terminal).
- `Command/Ctrl + k`: Toggles the aside.
- `Command/Ctrl + b`: Switches the page backward (with an optional Shift modifier to switch forward).
- `Command/Ctrl + z`: Toggles zoom.

## Prompt Functionality

Noterm's prompt offers powerful functionalities for managing files and performing actions within the editor interface. Here's a summary of its capabilities:

- **Delete File or Directory**: Use `<file/path> :d` to delete a specified file or directory.
  
- **Create New File**: Use `<file> :nf` to create a new file with the specified name.
  
- **Create New Directory**: Use `<path> :nd` to create a new directory at the specified path.
  
- **Save Buffer to New File**: Use `<file> :w` to save the content of the buffer to a new file with the specified name.

These prompt commands enable efficient file management and operations directly from the Noterm editor interface, streamlining your workflow for note-taking and file manipulation.

### Example Usage

Here are examples demonstrating how to use these prompt functionalities:

- `file.txt :d` deletes the `file.txt` from the filesystem.
  
- `newfile.txt :nf` creates a new file named `newfile.txt`.
  
- `newdirectory :nd` creates a new directory named `newdirectory`.
  
- `newfile.txt :w` saves the content of the editor buffer to a new file named `newfile.txt`.

These commands enhance the versatility of Noterm, providing users with intuitive ways to manage files and perform actions directly within the editor environment.

---

Enhance your productivity with Noterm by seamlessly integrating note-taking with OS command and SQL query execution. Explore the capabilities of "notes as code" with this versatile text editor!