# Noterm - The First Notes-as-Code Tool

Noterm is a desktop application that turns notes into executable commands. Write once, execute anytime, and share with your team. It consolidates multiple tools, including text editors, file explorers, terminals, and API clients, helping you stay focused and work more efficiently.

## Why Noterm?

🚀 **Executable Documentation** – Run commands directly from your notes and keep documentation up to date.

🔄 **Workflow Automation** – Reduce repetitive tasks and minimize human error.

📚 **Knowledge Sharing** – Share working examples and onboard team members faster.

🛠 **Efficiency** – All essential tools in one place, reducing context switching.

## The Interface

Noterm's interface consists of three main components:

1. **Buffer** – A specialized text editor where you:
   - Write and organize your notes.
   - Execute commands directly from notes.
   - Save files with the `.n` extension.
   - View command outputs on the left side.
   - Monitor multiple command executions simultaneously.

2. **Finder** – A file system explorer that:
   - Activates when entering a directory path.
   - Allows file system manipulation.
   - Supports bookmarks for quick access.

3. **Viewer** – A simple image display component that:
   - Shows images when an image file is selected.

## Executing Units

Units in Noterm can be executed in two ways:
- Click on the line number of the unit you want to execute.
- Position the cursor on the unit and press `Cmd+Enter` (or `Ctrl+Enter` on other OS).

## Navigation & Controls

### Essential Keyboard Shortcuts
- `Cmd+.` – Focus prompt
- `ESC` – Reset prompt input
- `Cmd+N` – Open a new page
- `Cmd+B` – Navigate backward
- `Cmd+Shift+B` – Navigate forward
- `Cmd+K` – Toggle sidebar
- `Cmd+Shift+ESC` – Close page

## Note Structure

### Units

Notes in Noterm are structured into **units**, which can be written in two ways:

#### Inline Unit Syntax
```
@<verb> [<alias>] [<parameter>] [<modifiers>] [<banner>] : <content>
```

#### Annotation Unit Syntax
```
@<verb> [<alias>] [<parameter>] [<modifiers>] [<banner>]
<content>
```

> In the annotation format, everything following the unit is considered `content` until another unit begins.

#### **1. Verbs (Unit Types)**
Specify the type of action to perform. Common verbs include:

#### **2. Alias**
An optional identifier for the unit. If provided, the unit is **cached** and can be referenced later using placeholders (`$alias` or `${alias}`). The alias can include a **bundle** (similar to a package) in the format `[bundle.]slug`.

**Examples**:
- `list_files` (simple alias).
- `utils.list_files` (alias with a bundle).

#### **3. Parameter**
Optional context for the unit, such as a directory path or connection details. If no parameter is needed, omit it entirely.

#### **4. Modifiers**
Customize the behavior of the unit. They are prefixed with `#` and placed after the alias (if any).

#### **5. Banner**
An optional description or label for the unit.

#### **6. Context**
The actual command, query, or text to execute or display. This is always the last part of the unit.


### Verbs (Unit Types)

1. **@cmd** – Execute shell commands
   ```
   @cmd "backup" : ./backup-script.sh
   @cmd "long process" #run : ./long-running-task.sh
   ```
   > `#run` modifier allows the command to run independently from stdin and stderr.

2. **@sql** – Execute database queries
   ```
   @sql ($mysql_db) "Active Users"
   SELECT * FROM users WHERE active = 1
   ```

3. **@api** – Make HTTP/HTTPS requests
   ```
   @api "get users" : GET https://api.example.com/users
   ```

4. **@var** – Declare variables
   ```
   @var mysql_db #mysql : user:password@host/dbname
   ```

5. **@rem** – Add documentation sections
   ```
   @rem "Database Operations"
   # The following commands handle database maintenance.
   ```

### Placeholder System

Use placeholders for dynamic values:
```
@cmd "commit" : git commit -m "${message}"
@var db #mysql : ${credentials}@<host>/<dbname>
```

## Cookie Mode

When a manifest is saved, Noterm can leverage the file's location as a relative path. This means commands can use the working directory of the manifest file. Example:
```
@cmd (.) : ls -al
```
Before executing the command, Noterm sets the working directory accordingly. This also allows for using paths like:
```
@cmd (.) : ./temp
```
## Database Integration

### Connection Variables

#### MySQL:
```
@var mysql_db #mysql : <user>:<password>@<host>/<dbname>
```

#### PostgreSQL:
```
@var pg_db #postgres : <user>:<password>@/<database>
```

#### SQLite:
```
@var local_db #sqlite : </path/to/database-sqlite>
```

### Query Execution
```
@sql ($mysql_db) "User Analysis"
SELECT 
    user_id,
    COUNT(*) AS login_count,
    MAX(login_time) AS last_login
FROM user_logins
GROUP BY user_id
ORDER BY login_count DESC;
```

## Expressions for the Buffer

Expressions must be entered and transmitted (press Enter) in the prompt.

### Find Text
```
:f|word
:f|word|1..10
:f|word|..10
:f|word|10..
:r|word|3,7
```

### Replace Text
```
:s|word|new word
:s|word|new word|1..10
:s|word|new word|..10
:s|word|new word|1..
:s|word|new word|3,7
```

### Delete Lines
```
:d|1
:d|1..10
:d|..10
:d|10..
:d|3,7
```

### Change Case
```
:u|word[|rows-pattern]   # Uppercase
:l|word[|rows-pattern]   # Lowercase
```

### Save File

1. `<file-path> :w`
2. Use **Cmd+S** (if the file is a draft, use syntax 1).

## File System Expressions

Expressions allow file system manipulation directly within the Finder (use prompt).

### Delete Files/Directories
```
:d|rows-pattern
```

### Move Files
```
:m|rows-pattern|directory
```

### Copy Files
```
:c|rows-pattern|directory
```

### Rename Files
```
:r|row|file
```

### Create New Directory
```
<new-directory-path> :nd
```

### Create Empty File
```
<new-file-path> :nf
```

### Bookmarks
- Create: `<path> :nb`
- Access: Enter `://bookmarks` in the prompt

## Getting Started

1. Download Noterm.
2. Create your first `.n` file.
3. Start documenting your workflows.
4. Share with your team.

**Tip:** Start with small tasks, document common commands, and gradually build a complete command library. Noterm helps you streamline your workflow and keep everything in one place!
