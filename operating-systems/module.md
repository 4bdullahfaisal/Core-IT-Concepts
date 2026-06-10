# OPERATING SYSTEMS — (Processes, memory, file systems)
---

## WHAT IS AN OPERATING SYSTEM

Software that manages hardware and lets you run programs.

## REAL LIFE ANALOGY

A manager of a building:
- Assigns rooms (memory)
- Schedules workers (processes)
- Organizes files (file system)

## EXAMPLES OF OPERATING SYSTEMS

| OS | Made by | Used on |
|----|---------|---------|
| Windows | Microsoft | Most PCs |
| macOS | Apple | Mac computers |
| Linux | Open source | Servers, developers |
| iOS | Apple | iPhones |
| Android | Google | Most phones |

---

## PART 2: PROCESSES

### What is a process

A program that is currently running.

### Real life analogy

A recipe book (program) vs actually cooking (process).

### Program vs Process

| Program | Process |
|---------|---------|
| Stored on disk (saved) | Loaded in memory (running) |
| Not active | Active |
| Example: chrome.exe file | Chrome browser open with 5 tabs |

### How to see running processes

- Windows: Task Manager (Ctrl + Shift + Esc)

- Mac/Linux: Activity Monitor or "top" command in terminal

### Process states

| State | What it means |
|-------|---------------|
| Running | Actively using CPU |
| Ready | Waiting for CPU |
| Blocked | Waiting for something (file, network) |
| Terminated | Finished |

### Process ID (PID)

Every process has a unique number.

### Linux/Mac - see processes with PIDs

```
ps aux
```

### Windows - see processes with PIDs

```
tasklist
```

### Multi-tasking

OS runs many processes by switching between them very fast.

```
Visual:
Time: 0-0.1s: Chrome runs
      0.1-0.2s: Spotify runs
      0.2-0.3s: VS Code runs
      Repeats many times per second

You don't notice the switching. It feels like everything runs at once.
```

---

## PART 3: MEMORY (RAM)

### What is RAM (Random Access Memory)

Temporary, fast storage. Holds currently running programs and data.

### Real life analogy

Your desk:
- RAM = desk surface (fast, but limited space)
- Hard drive = filing cabinet (slow, but lots of space)

### Memory hierarchy (speed vs size)

| Type | Speed | Size | Persists after power off? |
|------|-------|------|---------------------------|
| CPU Cache | Fastest | Very small (MB) | No |
| RAM | Fast | Medium (GB) | No |
| SSD | Medium | Large (hundreds GB) | Yes |
| HDD | Slow | Largest (TB) | Yes |

### What happens when RAM fills up

- Computer slows down dramatically
- OS starts using hard drive as "virtual memory" (very slow)
- Programs may crash

### How much RAM do you need

| Usage | Recommended RAM |
|-------|-----------------|
| Basic web browsing | 4-8 GB |
| Gaming | 16 GB |
| Video editing / Development | 32 GB |
| Servers | 64 GB+ |

### Memory in task manager

Windows Task Manager > Performance tab > Memory

Shows: Total RAM, Used RAM, Available RAM

---

## PART 4: MEMORY MANAGEMENT

### How OS manages memory

1. Allocation: OS gives memory to programs when they ask.

2. Deallocation: OS takes memory back when programs finish.

3. Protection: One program cannot access another program's memory.

Example:

Program A tries to read Program B's memory -> OS blocks it -> "Access Violation" error

### Virtual Memory

OS tricks programs into thinking they have unlimited memory.

Visual:

- Program thinks it has: Address 0 to 4GB

- Actual RAM: Address 1000 to 2000

- OS maps (translates) between them

### Swap / Page file

When RAM is full, OS moves some data to hard drive.

| Term | Same as |
|------|---------|
| Swap | Linux term |
| Page file | Windows term |
| Virtual memory | General term |

Downside: Hard drive is 1000x slower than RAM

---

## PART 5: FILE SYSTEMS

### What is a file system

The way OS organizes and stores files on a disk.

### Real life analogy

A filing cabinet with folders and documents.

### Common file systems

| File system | OS | Features |
|-------------|-----|----------|
| NTFS | Windows | Permissions, encryption, journaling |
| FAT32 | USB drives | Compatible with everything, 4GB file limit |
| exFAT | USB drives (large files) | No 4GB limit |
| APFS | macOS | Encryption, snapshots |
| ext4 | Linux | Most common Linux file system |

### File system structure (hierarchy)

```
Root (C:\ on Windows, / on Mac/Linux)
    |
    |-- Users/
    |      |-- Alice/
    |      |      |-- Documents/
    |      |      |-- Downloads/
    |      |-- Bob/
    |
    |-- Program Files/ (Windows) or Applications/ (Mac)
    |
    |-- Windows/ or System/
```

### Paths (how to find a file)

Windows:

`C:\Users\Alice\Documents\resume.pdf`

Mac/Linux:

`/home/alice/Documents/resume.pdf`

### Path types

| Type | Windows | Mac/Linux |
|------|---------|-----------|
| Absolute path | C:\Users\Alice\file.txt | /home/alice/file.txt |
| Relative path | Documents\file.txt | Documents/file.txt |

Relative path is from where you currently are.

### File permissions (who can access)

| Permission | What it allows | Number (Linux) |
|------------|---------------|----------------|
| Read (r) | View file contents | 4 |
| Write (w) | Modify file | 2 |
| Execute (x) | Run as program | 1 |

Permission example (Linux): rwxr-xr--

- Owner: read, write, execute
- Group: read, execute
- Others: read only

### Common file operations (commands)

| Operation | Windows (cmd) | Mac/Linux (terminal) |
|-----------|---------------|----------------------|
| List files | dir | ls |
| Change directory | cd folder | cd folder |
| Create directory | mkdir folder | mkdir folder |
| Delete file | del file.txt | rm file.txt |
| Delete directory | rmdir folder | rm -r folder |
| Copy file | copy source dest | cp source dest |
| Move file | move source dest | mv source dest |
| Show current path | cd | pwd |

---

## PART 6: PROCESS VS THREAD

### Thread (smaller than process)

A single sequence of execution inside a process.

### Visual

```
Process (Chrome)
    |
    |-- Thread 1: Tab 1 (reddit.com)
    |-- Thread 2: Tab 2 (youtube.com)
    |-- Thread 3: Tab 3 (github.com)
```

### Process vs Thread

| Feature | Process | Thread |
|---------|---------|--------|
| Has its own memory | Yes | No (shares with process) |
| Crash affects | Only this process | Entire process (all threads) |
| Creation time | Slow | Fast |
| Communication | Hard (needs IPC) | Easy (share memory) |
| Resource usage | High | Low |

---

## PART 7: BOOT PROCESS (What happens when you turn on computer)

> Step 1: Power on

> Step 2: BIOS/UEFI starts (basic input/output system)

> Step 3: BIOS checks hardware (POST - Power On Self Test)

> Step 4: BIOS loads bootloader from disk

>Step 5: Bootloader loads operating system kernel

> Step 6: Kernel initializes devices and drivers

> Step 7: Kernel starts first process (init on Linux, wininit.exe on Windows)

> Step 8: You see login screen or desktop

Time: Usually 10-60 seconds

---

## QUICK REFERENCE CARD

| Term | One sentence |
|------|--------------|
| OS | Manages hardware and runs programs |
| Process | A running program |
| PID | Unique number for each process |
| RAM | Fast, temporary memory |
| Virtual memory | Using disk as extra RAM |
| File system | How files are organized on disk |
| Path | Address of a file or folder |
| Thread | A sequence of work inside a process |

---

## SUMMARY DIAGRAM

```
Computer Hardware (CPU, RAM, Disk)
        |
        v
Operating System (manages everything)
        |
        v
Programs (Chrome, VSCode, Games)
        |
        v
You (the user)

```
