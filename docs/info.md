<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->


## ## How it works

The system is a **Synchronous Mod-10 Counter** (BCD Counter) that processes a clock signal to cycle through ten distinct states (0 to 9) before resetting.

**State Control:** The design uses **4 Flip-Flops** (2^4 = 16 states) to handle the decimal range. A reset logic AND gate is connected to Q3 and Q1 (representing binary 1010 or decimal 10) to force the counter back to `0000` immediately after state 9.

**Decoding Logic:** The BCD outputs (D0 through D3) are fed into a series of **AND, OR, and NOT gates**. These gates implement the Boolean expressions required to drive a **Seven-Segment Display**. 


## ## How to test

To verify the counter and the decoder logic, set the inputs and check the outputs match with the expected BCD-to-7-segment results:

  Decimal	| Q3 | Q2	| Q1 | Q0
      0	  | 0	 | 0	| 0	 | 0
      1	  | 0	 | 0	| 0	 | 1
      2	  | 0	 | 0	| 1	 | 0
      3	  | 0	 | 0	| 1	 | 1
      4	  | 0	 | 1	| 0	 | 0
      5	  | 0	 | 1	| 0	 | 1
      6	  | 0	 | 1	| 1	 | 0
      7	  | 0	 | 1	| 1	 | 1
      8	  | 1	 | 0	| 0	 | 0
      9	  | 1	 | 0	| 0	 | 1
   RESET	| 0	 | 0	| 0  | 0

### Operational Verification
1.  **Clock Setup:** Set the input clock frequency to **3Hz**.
2.  **Display Check:** Observe the Seven-Segment Display; it should cycle through digits `0` through `9` sequentially.
3.  **Frequency Observation:** You should see the **5th output flashing quickly** (higher clock division) and the **4th output flashing slowly** (lower clock division), confirming the internal timing chain is active.

## ## Limitations
not compulsory working, got bugs
