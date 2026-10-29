# EXPT 2 - Verification of Logic Gates
### SIMULATION AND VERIFICATION OF AND, OR, AND NOT GATES
## Aim
To design, implement, and verify the functionality of basic AND, OR, and NOT logic gates using Verilog HDL, and verify the functionality using Synopsys VCS and DVE.
# Software Required
•	Synopsys VCS
•	Synopsys DVE
•	Linux Terminal
•	Verilog HDL
# Boolean Function
The basic logic gates realize the following Boolean functions:

•	AND: Y_AND = A . B
•	OR: Y_OR = A + B
•	NOT: Y_NOT = A'

# Theory / Synopsis
Logic gates are the basic building blocks of digital systems. NAND and NOR are universal gates. XOR produces 1 when its inputs differ, while XNOR produces 1 when its inputs are equal.
# Files to be Created
File name	Purpose
logic_gates.v	Logic-gate RTL
logic_gates_tb.v	All input combinations and VCD generation
 # Verilog  Program
 ```
 module basic_gates (
    input  wire a,
    input  wire b,
    output wire y_nand,
    output wire y_nor,
    output wire y_xor
);
    assign y_nand = ~(a & b);
    assign y_nor  = ~(a | b);
    assign y_xor  =  a ^ b;
endmodule
 ```

# **Test Bench Program**
```
module tb2;
    reg  a, b;
    wire y_nand, y_nor, y_xor;

    basic_gates uut (
        .a(a),
        .b(b),
        .y_nand(y_nand),
        .y_nor(y_nor),
        .y_xor(y_xor)
    );

    initial begin
        $dumpfile("basic_gates.vcd");
        $dumpvars(0, tb2);

        $monitor("Time=%0t a=%b b=%b | NAND=%b NOR=%b XOR=%b",
                 $time, a, b, y_nand, y_nor, y_xor);

        a = 0; b = 0; #10;
        a = 0; b = 1; #10;
        a = 1; b = 0; #10;
        a = 1; b = 1; #10;

        $finish;
    end
endmodule

```
 
<img width="1237" height="497" alt="image_1c91cbf3 (1)" src="https://github.com/user-attachments/assets/b9069348-d593-40f4-acb8-2d0a45fd630d" />


# Simulation Procedure
STEP 1 – Open Terminal
Open a terminal in the experiment folder.
bash

STEP 2 – Load Synopsys Environment
source /synopsys/start.sh

STEP 3 – Compile Using VCS
vcs logic_gates.v logic_gates_tb.v -full64
If compilation is successful, VCS generates the simulation executable:
simv

STEP 4 – Run Simulation
./simv
The terminal displays the input combinations and corresponding output F.
A VCD waveform file is also generated:
exp1_boolean_min.vcd

STEP 5 – Open DVE
dve -full64
Other option
dve -full64 &
A DVE environment will open.

DVE Waveform Verification
In DVE:
Open the testbench hierarchy.
Locate the signals: 
a
b
y_and
y_or
y_not
Add the signals to the waveform window.
Run/inspect the waveform.
Verify that y_and = 1 only when a=1 AND b=1 — the single combination where both inputs are high.
Verify that y_or = 1 whenever a=1 OR b=1 (any input high forces the output high).
Verify that y_not is always the exact complement of a, regardless of b.
The waveform should agree with the truth table.
# Expected Result
The basic logic gates — AND, OR, and NOT — were realized using Verilog HDL:
Y_AND = A.B
Y_OR = A+B
Y_NOT = A'
The design was compiled and simulated using Synopsys VCS, and the functionality was verified using DVE waveform analysis, matching the expected truth table.
Output
<img width="1917" height="310" alt="Screenshot 2026-10-29 124355" src="https://github.com/user-attachments/assets/7d7995f2-98b3-444c-846d-a1bb1c90fb37" />









# OUTPUT
<img width="1920" height="1080" alt="Screenshot 2026-10-29 124552" src="https://github.com/user-attachments/assets/9dbdf4d7-6fe0-45bd-b4a0-3d66485189a9" />


 
