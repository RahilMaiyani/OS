# OS T2 Exam Master Preparation (Units 6 to 10)

This master review is tailored for your **50-mark exam** covering **Chapters 6 through 10**. It concentrates on the **35–40+ marks** target by locking 15/15 in Numericals, 20+ in MCQs, and 5–8 marks in core high-yield theory and shell scripts.

The standalone interactive file with a **dark Vercel theme** is available here:
🔗 **[Open Standalone Dark Vercel HTML Prep Guide](file:///C:/Users/Rahil.Maiyani/.gemini/antigravity/scratch/os_t2_exam_prep.html)**

---

## 📊 Exam Blueprint & Weightage Breakdown

| Chapter | Title | Weightage | Scoring Focus |
| :---: | :--- | :---: | :--- |
| **Unit 6** | **Memory Management Policies** | **15% (15M)** | Allocation Numericals (First/Best/Worst Fit), TLB EMAT Math, Paging vs Segmentation |
| **Unit 7** | **Basics of Virtual Memory** | **10% (10M)** | Page Replacement (FIFO, LRU, Optimal), Belady's Anomaly, Demand Paging & Thrashing |
| **Unit 8** | **Secondary Storage & I/O Management** | **8% (8M)** | Disk Scheduling Algorithms (FCFS, SSTF, SCAN, LOOK, C-SCAN, C-LOOK), Seek/Rotational Time, DMA |
| **Unit 9** | **Security and Protection Mechanism** | **5% (5M)** | High-probability MCQs, Malware definitions (Worm vs Virus vs Trojan), Access Matrix/ACL |
| **Unit 10** | **Unix / Linux Operating System** | **12% (12M)** | Command MCQs (`chmod`, `rm -r`, `grep`, `ps`, `df`), Roles of Shell & Kernel, Basic Shell Scripts |
| **Total** | | **50 Marks** | **25 MCQs (25M) + 15 Numericals (15M) + 10 Theory (10M)** |

---

## 🎯 The Guaranteed 35–40 Marks Strategy

```
  ┌──────────────────────────────┐
  │  Numericals (Units 6, 7, 8)  │ ──► 15 / 15 Marks (100% predictable)
  └──────────────┬───────────────┘
                 │
  ┌──────────────▼──────────────┐
  │ Practice Book MCQs (75 total)│ ──► 18 - 22 Marks (Direct hits)
  └──────────────┬───────────────┘
                 │
  ┌──────────────▼──────────────┐
  │ 5 Short Theory & 1-2 Scripts │ ──► 5 - 8 Marks
  └─────────────────────────────┘
  ──────────────────────────────────────────────────────────
  TOTAL SCORE ESTIMATE: 38 - 43 / 50 Marks
```

---

## 🧮 Section 1: All Practice Book Numericals Solved

### 1. Contiguous Allocation (Unit 6: Q219, Q220, Q228)
* **Given Partitions:** `100K, 500K, 200K, 300K, 600K` (in order).
* **Incoming Processes:** `212K, 417K, 112K, 426K` (in order).
* **First-Fit:**
  * P1 (212K) &rarr; `500K` (leaving 288K)
  * P2 (417K) &rarr; `600K` (leaving 183K)
  * P3 (112K) &rarr; `288K` (leaving 176K)
  * P4 (426K) &rarr; **FAILS (Must wait)** because remaining holes are `100K, 176K, 200K, 300K, 183K` (largest is only 300K).
* **Best-Fit:**
  * P1 (212K) &rarr; `300K` (leaving 88K)
  * P2 (417K) &rarr; `500K` (leaving 83K)
  * P3 (112K) &rarr; `200K` (leaving 88K)
  * P4 (426K) &rarr; `600K` (leaving 174K)
  * **Result:** All 4 processes fit! **Best-Fit is the most efficient**.
* **Worst-Fit:**
  * P1 &rarr; `600K` (388K left), P2 &rarr; `500K` (83K left), P3 &rarr; `388K` (276K left), P4 (426K) **FAILS**.

---

### 2. Effective Memory Access Time (EMAT) with TLB (Unit 6: Q223, Q224, Q227)
* **General Formula:**
  $$\text{EMAT} = t_{TLB} + \left[\alpha \times t_{mem}\right] + \left[(1 - \alpha) \times (t_{page\_table} + t_{mem})\right]$$
* **Q223 (No TLB search overhead):**
  * $\alpha = 0.75$, $t_{mem} = 100\text{ ns}$, $t_{pt} = 100\text{ ns}$.
  * $\text{EMAT} = 0.75 \times 100 + 0.25 \times (100 + 100) = 75 + 50 = \mathbf{125\text{ ns}}$.
* **Q224 (No TLB search overhead):**
  * $\alpha = 0.85$, $t_{mem} = 100\text{ ns}$, $t_{pt} = 50\text{ ns}$.
  * $\text{EMAT} = 0.85 \times 100 + 0.15 \times (50 + 100) = 85 + 22.5 = \mathbf{107.5\text{ ns}}$.
* **Q227 (With 20ns TLB search overhead):**
  * $\alpha = 0.75$, $t_{mem} = 100\text{ ns}$, $t_{pt} = 100\text{ ns}$, $t_{TLB} = 20\text{ ns}$.
  * $\text{EMAT} = 0.75 \times (20 + 100) + 0.25 \times (20 + 100 + 100) = 90 + 55 = \mathbf{145\text{ ns}}$.

---

### 3. Page Replacement Algorithms (Unit 7: Q267, Q268, Q269, Q273)
* **Reference String:** `7, 0, 1, 2, 0, 3, 0, 4, 2, 3` with **3 frames** (initially empty).
  * **FIFO:** Replaces oldest loaded page &rarr; **9 Page Faults**, 1 Hit.
  * **LRU:** Replaces least recently used page (look backward) &rarr; **8 Page Faults**, 2 Hits.
  * **Optimal (OPT):** Replaces page not used for longest in future (look forward) &rarr; **6 Page Faults**, 4 Hits.
* **Belady's Anomaly (Q277):**
  * String: `5, 4, 3, 2, 5, 4, 6, 5, 4, 3, 2, 6`.
  * With 3 frames: **9 Faults**.
  * With 4 frames: **10 Faults** (Faults increase when frames increase &rarr; proves Belady's Anomaly in FIFO).

---

### 4. Disk Scheduling Algorithms (Unit 8: Q303)
* **Setup:** 200 Cylinders (0 to 199). Head initially at **53**, moving in **increasing** direction.
* **Request Queue:** `98, 183, 37, 122, 14, 124, 65, 67`.
* **Total Head Movements (THM):**
  * **FCFS:** Strict queue order &rarr; **640 Cylinders**.
  * **SSTF:** Closest track next ($53 \to 65 \to 67 \to 37 \to 14 \to 98 \to 122 \to 124 \to 183$) &rarr; **236 Cylinders** (Optimal).
  * **SCAN:** Goes up to boundary 199, then reverses ($53 \to 199 \to 14$) &rarr; $(199 - 53) + (199 - 14) = \mathbf{331\text{ Cylinders}}$.
  * **LOOK:** Goes up only to last request 183, then reverses ($53 \to 183 \to 14$) &rarr; $(183 - 53) + (183 - 14) = \mathbf{299\text{ Cylinders}}$.
  * **C-SCAN:** Goes up to 199, jumps to 0 without servicing, scans up to 37 &rarr; $(199 - 53) + (199 - 0) + (37 - 0) = \mathbf{382\text{ Cylinders}}$.
  * **C-LOOK:** Goes up to 183, jumps to 14 without servicing, scans up to 37 &rarr; $(183 - 53) + (183 - 14) + (37 - 14) = \mathbf{322\text{ Cylinders}}$.
* **Seek Time Conversion:** $\text{Seek Time} = \text{THM} \times (\text{time per cylinder})$. E.g., at 5ms/cyl for SSTF: $236 \times 5 = 1180\text{ ms} = 1.18\text{ s}$.

---

## 💡 Section 2: High-Yield Short Theory Points

1. **Internal vs External Fragmentation (Unit 6):**
   * *Internal:* Unused space within an allocated partition (Fixed Partitioning, Paging).
   * *External:* Total free memory exists but is fragmented into scattered unusable non-contiguous holes (Variable Partitioning, Segmentation). Paging eliminates external fragmentation.
2. **Paging vs Segmentation (Unit 6):**
   * Paging divides memory into fixed-size blocks (Pages/Frames; hardware view).
   * Segmentation divides memory into variable-sized logical modules (Code, Stack, Heap; programmer view).
3. **Demand Paging & Page Fault (Unit 7):**
   * Pages are loaded only on demand when referenced.
   * A Page Fault is a hardware interrupt triggered when accessing an unmapped/unloaded page.
4. **Thrashing (Unit 7):**
   * A system condition where processes spend more time swapping pages than executing instructions. Caused by overcommitting degree of multiprogramming. Controlled using the **Working Set Model** and **Page Fault Frequency (PFF)**.
5. **Seek Time vs Rotational Latency (Unit 8):**
   * *Seek Time:* Time for disk arm to travel to the designated track/cylinder.
   * *Rotational Latency:* Time for the target sector on the platter to rotate under the read/write head.
6. **Direct Memory Access - DMA (Unit 8):**
   * Allows high-speed I/O devices to transfer data directly to/from main memory without continuous CPU intervention, freeing the CPU for compute tasks.
7. **Malware Taxonomy (Unit 9):**
   * *Virus:* Code fragment attaching to legitimate host files.
   * *Worm:* Standalone self-replicating network program.
   * *Trojan Horse:* Malicious software disguised as genuine/useful.
   * *Trapdoor:* Secret intentional bypass in code authentication.
8. **Unix Shell & Kernel (Unit 10):**
   * *Kernel:* Heart of Unix running in privileged mode, managing CPU, memory, and devices.
   * *Shell:* User interface/command interpreter translating user commands into kernel system calls.

---

## 💻 Section 3: Essential Shell Scripts (Unit 10)

* **Multiplication Table:**
  ```bash
  read -p "Enter number: " n
  for i in {1..10}; do
    echo "$n x $i = $(( n * i ))"
  done
  ```
* **Reverse a Number:**
  ```bash
  read -p "Enter number: " n
  rev=0
  while [ $n -gt 0 ]; do
    rem=$(( n % 10 ))
    rev=$(( rev * 10 + rem ))
    n=$(( n / 10 ))
  done
  echo "Reversed: $rev"
  ```
* **Check Palindrome String:**
  ```bash
  read -p "Enter string: " s
  if [ "$s" = "$(echo "$s" | rev)" ]; then
    echo "Palindrome"
  else
    echo "Not Palindrome"
  fi
  ```
* **Greatest of Three Numbers:**
  ```bash
  read a b c
  if [ $a -ge $b ] && [ $a -ge $c ]; then echo "Max: $a"
  elif [ $b -ge $a ] && [ $b -ge $c ]; then echo "Max: $b"
  else echo "Max: $c"; fi
  ```
