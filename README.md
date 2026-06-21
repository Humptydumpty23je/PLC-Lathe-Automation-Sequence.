

https://github.com/user-attachments/assets/0498ae8e-9773-4c64-b287-5e58c1e565b4

## Semi-Automatic Lathe Control System (RSLogix 500 & Wonderware InTouch)

### System Overview
This project presents a fully simulated industrial control system for a semi-automatic turning machine (Lathe) used to machine cylindrical parts. The control architecture handles automated dual-motor synchronization through precise timing intervals and cycle-limit counting.

### Process Workflow
1. **System Start:** Activating the **START Push Button (PB1)** triggers the **Spindle Motor (M1)**.
2. **Interlocking Delay:** A 3-second **TON** timer delays the activation of the **Cutting Tool Motor (M2)**.
3. **Execution Phase:** The cutting phase runs continuously for 10 seconds. Once the timer completes, M2 drops out, marking one full cycle.
4. **Recycling Logic:** The system resets its timing relays automatically to begin the second cycle.
5. **Count Limit:** An accumulation count of 2 cycles on the **CTU** instruction instantly de-energizes both **M1 and M2**, turning on the **FINISHED Indicator (L1)**.
6. **Safety Stop:** A master **STOP Push Button (PB2)** cuts system power instantly at any point during operation.

### Technical Stack & Software
* **PLC Programming Software:** Rockwell Automation RSLogix 500
* **HMI Software:** Wonderware InTouch (ArchestrA/AVEVA)
* **Core Instructions:** Timer On-Delay (TON), Counter Up (CTU), Latch/Unlatch (OTL/OTU), and data bit interlocking.
