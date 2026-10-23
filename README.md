# OS T2 Exam Master Preparation (Units 6 to 10)

This master document is fully rebuilt and aligned with your **L.J. Institute Official Notes & Practice Books**.

🔗 **[Open Standalone Mobile-Optimized HTML Portal](file:///C:/Users/Rahil.Maiyani/.gemini/antigravity/scratch/os_t2_exam_prep.html)**

---

## 📊 Exam Blueprint & Marks Distribution (Total: 50 Marks)

| Chapter | Title | Weightage | Target Marks | High-Yield Coverage |
| :---: | :--- | :---: | :---: | :--- |
| **Unit 6** | **Memory Management Policies** | **15% (15M)** | 12–14M | First/Best/Worst/Next-Fit, Starting Addr, TLB EMAT, Fragmentation, Paging vs Segmentation |
| **Unit 7** | **Basics of Virtual Memory** | **10% (10M)** | 8–10M | FIFO, LRU, Optimal, Belady's Anomaly, NRU Matrix, Second Chance, Demand Paging, Thrashing |
| **Unit 8** | **Secondary Storage & I/O Management** | **8% (8M)** | 7–8M | Disk Scheduling (FCFS, SSTF, SCAN, LOOK, C-SCAN, C-LOOK), Seek Time & Rotational Latency, DMA |
| **Unit 9** | **Security & Protection Mechanism** | **5% (5M)** | 4–5M | 8 Design Principles of Security, Domain Protection, Access Matrix, ACL vs C-List, Malware |
| **Unit 10** | **Unix / Linux Operating System** | **12% (12M)** | 10–12M | Kernel Subsystems, Unix vs Windows, Elementary Commands, Shell Scripts (Practicals 1–28) |
| **Total** | | **50 Marks** | **40–48M** | **25 MCQs (25M) + 15 Numericals (15M) + 10 Theory (10M)** |

---

## 🧮 ALL NUMERICALS & CHEAT CODES

### 1. Memory Partition Allocation (Unit 6)
* **First-Fit:** Searches sequentially from beginning; allocates the first block $\ge$ request.
* **Best-Fit:** Searches entire memory; allocates the smallest block $\ge$ request. Leaves smallest leftover hole.
* **Worst-Fit:** Searches entire memory; allocates the largest available block.
* **Next-Fit:** Searches like First-Fit, but resumes scanning from the location of the *last allocated block*.
* **Standard Exam Problem (PB Q219/Q220):**
  * Partitions: `100K, 500K, 200K, 300K, 600K`
  * Processes: `212K, 417K, 112K, 426K`
  * **Best-Fit** is the ONLY algorithm that accommodates all 4 processes! First-Fit, Worst-Fit, and Next-Fit all fail to allocate $426\text{K}$.

### 2. Paging with TLB & Effective Memory Access Time (Unit 6)
* **Without TLB lookup overhead:**
  $$\text{EMAT} = \alpha \cdot t_{\text{mem}} + (1 - \alpha) \cdot (t_{\text{pt}} + t_{\text{mem}})$$
* **With TLB lookup overhead ($t_{\text{tlb}}$):**
  $$\text{EMAT} = \alpha \cdot (t_{\text{tlb}} + t_{\text{mem}}) + (1 - \alpha) \cdot (t_{\text{tlb}} + t_{\text{pt}} + t_{\text{mem}})$$
* **Quick Exam Solutions:**
  * PB Q223: $\alpha=0.75, t_{\text{mem}}=100, t_{\text{pt}}=100 \implies \mathbf{125\text{ ns}}$
  * PB Q224: $\alpha=0.85, t_{\text{mem}}=100, t_{\text{pt}}=50 \implies \mathbf{107.5\text{ ns}}$
  * PB Q227: $\alpha=0.75, t_{\text{mem}}=100, t_{\text{pt}}=100, t_{\text{tlb}}=20 \implies \mathbf{145\text{ ns}}$

### 3. Page Replacement Algorithms (Unit 7)
* **FIFO:** Replace oldest loaded page in frame. (Susceptible to Belady's Anomaly).
* **LRU:** Look left (into the past); replace page not referenced for longest time.
* **Optimal (OPT):** Look right (into the future); replace page not needed for longest time.
* **NRU (4 Classes):**
  * Class 0: $R=0, M=0$
  * Class 1: $R=0, M=1$
  * Class 2: $R=1, M=0$
  * Class 3: $R=1, M=1$
  * Replaces random page from the lowest non-empty class.
* **Second Chance (Clock):** Inspect FIFO pointer with bit $R$. If $R=1$, clear to $0$ and advance; if $R=0$, evict.

### 4. Disk Arm Scheduling (Unit 8)
* **Total Head Movement (THM):** Sum of absolute cylinder steps $\sum |C_{\text{curr}} - C_{\text{next}}|$.
* **5000-Cylinder Problem (Notes Pg 16–19 & PB Q305):** Head at 143, moving down towards 0:
  * **FCFS:** $7081\text{ cyl}$
  * **SSTF:** $\mathbf{1745\text{ cyl}}$ (Optimal)
  * **SCAN:** $1917\text{ cyl}$ (Touches boundary 0)
  * **LOOK:** $1745\text{ cyl}$ (Reverses at lowest request 86)
  * **C-SCAN:** $9228\text{ cyl}$
  * **C-LOOK:** $2606\text{ cyl}$

---

## 📚 CORE HIGH-YIELD THEORY (CH 6 TO 10)

1. **Fragmentation & Compaction (Ch 6):**
   * *Internal Fragmentation:* Wasted memory within an allocated partition (Fixed partitioning & Paging).
   * *External Fragmentation:* Total free space exists, but scattered in non-contiguous fragments (Variable partitioning & Segmentation).
   * *Compaction:* Shuffling memory to group free space into a contiguous hole.
2. **Paging vs Segmentation (Ch 6):**
   * *Paging:* Divides memory into fixed-size physical frames and pages. Transparent to user. Internal fragmentation only.
   * *Segmentation:* Divides memory into variable-sized logical segments (Code, Stack, Data) representing the programmer's view. External fragmentation only.
3. **Page Fault & Thrashing (Ch 7):**
   * *Page Fault:* Hardware trap triggered when a process requests a page not currently resident in RAM.
   * *Thrashing:* State where the system spends more time swapping pages in/out than executing user instructions due to overcommitting multiprogramming beyond working set limits.
4. **Disk Latencies & DMA (Ch 8):**
   * *Seek Time:* Arm travel time to track.
   * *Rotational Delay:* Platter spin time to sector.
   * *Direct Memory Access (DMA):* Dedicated controller moving blocks directly between I/O and RAM with zero CPU intervention during transfer.
5. **The 8 Design Principles of Security (Ch 9):**
   * Least Privilege, Fail-Safe Defaults, Economy of Mechanism, Complete Mediation, Open Design, Separation of Privilege, Least Common Mechanism, User Acceptability.
6. **Access Matrix vs ACL vs C-List (Ch 9):**
   * *ACL (Column-slice):* Attached to Object/File. Easy to revoke access for specific files.
   * *Capability List (Row-slice):* Attached to Subject/Process. Fast access checks.
7. **Linux Kernel Subsystems (Ch 10):**
   * System Call Interface $\to$ Process Management Subsystem, Memory Management Subsystem, I/O Subsystem (VFS, Character/Block drivers).
