# How to Use the `top` Command in Linux: A Comprehensive Guide

The `top` (table of processes) command is one of the most widely used built-in utilities in Linux. It provides a real-time, dynamic view of running system processes, CPU consumption, memory utilization, swap usage, and system load.

---

## 1. Basic Syntax and Launching `top`

To launch the utility with default settings, simply run:

```bash
top
```

To exit the interface at any time, press **`q`** or **`Ctrl + C`**.

---

## 2. Understanding the Interface

When you run `top`, the output is divided into two main areas:
1. **Summary Area (Header / Dashboard)**
2. **Process List (Task Table)**

```text
top - 14:10:05 up 3 days,  4:12,  2 users,  load average: 0.15, 0.08, 0.06
Tasks: 215 total,   1 running, 214 sleeping,   0 stopped,   0 zombie
%Cpu(s):  2.3 us,  1.0 sy,  0.0 ni, 96.2 id,  0.2 wa,  0.0 hi,  0.3 si,  0.0 st
MiB Mem :   7824.2 total,   2150.4 free,   3412.1 used,   2261.7 buff/cache
MiB Swap:   2048.0 total,   2048.0 free,      0.0 used.   4112.5 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
   1245 root      20   0  812340  94120  42100 S   3.3   1.2   4:12.35 dockerd
   1890 user1     20   0  452100  51200  28400 S   1.0   0.6   0:45.12 node
```

### Breakdown of the Summary Area

* **Line 1: System Time & Uptime**
  * `14:10:05`: Current system time.
  * `up 3 days, 4:12`: System uptime.
  * `2 users`: Number of currently logged-in users.
  * `load average: 0.15, 0.08, 0.06`: Average system load over the last 1, 5, and 15 minutes. *(Load values relative to CPU core count indicate system saturation).*

* **Line 2: Tasks (Processes)**
  * Displays total tasks, and how many are `running`, `sleeping`, `stopped`, or `zombie` (dead processes waiting for their exit status to be read by parents).

* **Line 3: CPU States**
  * `us` (User): CPU time spent on user processes (un-niced).
  * `sy` (System): CPU time spent on kernel operations.
  * `ni` (Nice): CPU time spent on low-priority (niced) processes.
  * `id` (Idle): Percentage of idle CPU time.
  * `wa` (I/O Wait): Time spent waiting for disk/network I/O.
  * `hi` (Hardware Interrupts): Servicing hardware IRQs.
  * `si` (Software Interrupts): Servicing network or soft IRQs.
  * `st` (Steal): Virtual CPU time stolen by the hypervisor.

* **Lines 4 & 5: Memory and Swap Usage**
  * Displays total, free, used, and buffered/cached RAM and Swap.
  * `avail Mem`: An estimate of how much memory is available for starting new applications without swapping.

---

### Column Descriptions in the Process List

| Column | Description |
| :--- | :--- |
| **PID** | Process ID (unique numerical identifier). |
| **USER** | Username owning the process. |
| **PR** | Priority of the task (kernel view). |
| **NI** | Nice value ($-20$ = highest priority, $19$ = lowest priority). |
| **VIRT** | Total virtual memory used by the task (code, data, shared libs). |
| **RES** | Resident memory (non-swapped physical RAM currently used). |
| **SHR** | Shared memory used by the process. |
| **S** | Process status (`R` = Running, `S` = Sleeping, `D` = Uninterruptible sleep, `Z` = Zombie, `T` = Traced/Stopped). |
| **%CPU** | Share of CPU time used since last screen refresh. |
| **%MEM** | Percentage of physical memory (RES) used. |
| **TIME+** | Total cumulative CPU time consumed by the process. |
| **COMMAND**| Name of the executable or command line used to launch it. |

---

## 3. Essential Interactive Commands

While `top` is running, you can press single keys to modify how it sorts and presents information.

### Sorting & Filtering
* **`P`** *(Shift + p)*: Sort by **%CPU** usage (default).
* **`M`** *(Shift + m)*: Sort by **%MEM** (Memory usage).
* **`T`** *(Shift + t)*: Sort by **TIME+** (Running time).
* **`N`** *(Shift + n)*: Sort by **PID** numerically.
* **`R`**: Reverse current sorting order.
* **`u`**: Filter by a specific username (type the username and hit Enter, or leave blank to clear).

### Display Tweaks
* **`1`**: Toggle display of individual CPU cores vs. combined CPU load.
* **`c`**: Toggle showing the full command path and arguments vs. just the program name.
* **`V`**: Display processes in a **forest/tree view** showing parent-child hierarchy.
* **`z`**: Toggle color highlights on/off.
* **`b`**: Toggle bold/reverse-video highlighting on running tasks.
* **`d`** or **`s`**: Change the screen refresh interval (e.g., enter `1` for 1-second refreshes).
* **`k`**: Kill a process (prompts for PID, then signal, e.g., `15` for SIGTERM or `9` for SIGKILL).
* **`r`**: Renice a process (change process priority).
* **`h`** or **`?`**: Open the built-in help manual.
* **`q`**: Quit `top`.

---

## 4. Useful Command-Line Flags

You can specify arguments when starting `top` directly from the terminal:

### 1. Monitor a Specific Process ID (PID)
```bash
top -p 1234
```
*(To track multiple PIDs, separate them with commas: `top -p 1234,5678`)*

### 2. Monitor a Specific User
```bash
top -u www-data
```

### 3. Change Refresh Rate on Launch
Refresh the screen every 2 seconds:
```bash
top -d 2
```

### 4. Batch Mode (Export to File / Scripting)
Run `top` non-interactively for a set number of iterations and save the output to a text file:
```bash
# Capture 3 iterations (-n 3) in batch mode (-b)
top -b -n 3 > top_report.txt
```

---

## 5. Practical Troubleshooting Scenarios

### Scenario A: Identifying Memory Leaks
1. Start `top`.
2. Press **`M`** to sort tasks by `%MEM`.
3. Check the **`RES`** column: if a single process keeps climbing over time without dropping, it may have a memory leak.

### Scenario B: Identifying High CPU Spikes
1. Start `top`.
2. Press **`1`** to see whether a single core is pegged at $100\%$ while others are idle (single-threaded bottleneck).
3. Press **`P`** to identify the process utilizing the core.
4. Press **`c`** to see the exact script or binary executing.

---

## 6. Summary Cheat Sheet

| Key / Flag | Action |
| :--- | :--- |
| `top` | Launch top |
| `top -u [user]` | Filter by user on startup |
| `top -p [pid]` | Filter by process ID |
| `top -b -n 1` | Run once in batch mode (for scripts) |
| `P` / `M` / `T` | Sort by CPU / Memory / Time |
| `1` | Show all CPU cores |
| `c` | Toggle full command line |
| `k` | Kill a process |
| `q` | Quit |