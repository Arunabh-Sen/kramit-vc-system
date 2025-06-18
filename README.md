# Kramit VCS

**Kramit** is a lightweight, Git-inspired version control system built using modern JavaScript (Node.js). Designed to replicate the core functionalities of Git, it provides a simplified and educational look into how version control systems manage file history, commits, and diffs.

---

## Features

- Initialize a repository with `.kramit/` directory
- Track and hash files using SHA-1
- Stage files and manage a custom index
- Commit changes with metadata (timestamp, message, parent)
- View commit history in reverse chronological order
- Show diff between a commit and its parent with line-level changes

---

## Why "Kramit"?

“Kram” (क्रम) is a Sanskrit word meaning *order* or *sequence*, which directly reflects the nature of version control systems.  
“Kramit” suggests the act of ordering or sequencing, perfectly suited to a tool that tracks the history of file changes in a structured way.

---

## Installation

```bash
git clone https://github.com/your-username/kramit.git
cd kramit
npm install
```
---

# Usage

## Initialise a repository

```bash
node Kramit.mjs init
```

Creates a .kramit/ folder with:

- objects/ for storing file and commit data
- HEAD file to track the latest commit
- index file to track staged files

## Add files to staging:

```bash
node Kramit.mjs add <filename>
```

Reads the file, creates a SHA-1 hash, stores the contents, and updates the staging area (index).

## Commit staged changes:

```bash
node Kramit.mjs commit "Your commit message"
```

Creates a commit object with:

- Timestamp
- Commit message
- Staged file list
- Parent commit hash (if exists)

Also updates HEAD and clears the index.

## View commit history:

```bash
node Kramit.mjs log
```

Displays the commit history from latest to earliest.

## Show chages in a commit:

```bash
node Kramit.mjs show <commitHash>
```

Shows the files included in the commit and displays line-by-line diffs compared to the parent commit.

# Sample Output

```text
-------------------------------
Commit: 5e2f8ab4fbb8f9f7a6...

Date: 2025-06-17T12:30:10.254Z

Initial commit

File is: sample.txt

+ Added line
- Removed line
```

# Internals

Kramit is a simplified Git-like engine that mimics:

- Staging area (index)
- SHA-1 hashing of file contents
- Content-addressable storage (.kramit/objects)
- Commit trees with parent linkage
- Diff viewing using diff and chalk libraries

# Screenshots

![image](https://github.com/user-attachments/assets/3db69c30-bcb6-46b7-b57b-a4a839a28388)
![Screenshot 2025-06-18 110246](https://github.com/user-attachments/assets/1a1f95d9-f5ed-44ab-b03d-732377500d16)
![Screenshot 2025-06-18 110309](https://github.com/user-attachments/assets/22a7c60e-85b3-4fd9-9ee2-a1f9f19db03d)
![Screenshot 2025-06-18 110343](https://github.com/user-attachments/assets/887a275a-4727-4ab2-941f-2af4bee26e86)

# Tech Stack

- Node.js (ES Modules)
- Filesystem API for object storage
- Crypto (SHA-1) for hashing
- diff for computing changes
- chalk for colored CLI output
- Commander for CLI command parsing

# Limitations (to be added soon)

- No support for branches, remote repositories, or merges
- Does not track file deletions or renames
- Commits are linear (no DAG)

  ### Contributions are always welcomed, fork the repo to get started.
