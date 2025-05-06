;m### SYNCHRONOUS-UP-COUNTER

**AIM:**

To implement 4 bit synchronous up counter and validate functionality.

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**

**4 bit synchronous UP Counter**

If we enable each J-K flip-flop to toggle based on whether or not all preceding flip-flop outputs (Q) are “high,” we can obtain the same counting sequence as the asynchronous circuit without the ripple effect, since each flip-flop in this circuit will be clocked at exactly the same time:

![image](https://github.com/naavaneetha/SYNCHRONOUS-UP-COUNTER/assets/154305477/d5db3fa0-e413-404c-b80e-b2f39d82e7e8)


![image](https://github.com/naavaneetha/SYNCHRONOUS-UP-COUNTER/assets/154305477/52cb61eb-d04b-442d-810c-31185a68410b)

Each flip-flop in this circuit will be clocked at exactly the same time.
The result is a four-bit synchronous “up” counter. Each of the higher-order flip-flops are made ready to toggle (both J and K inputs “high”) if the Q outputs of all previous flip-flops are “high.”
Otherwise, the J and K inputs for that flip-flop will both be “low,” placing it into the “latch” mode where it will maintain its present output state at the next clock pulse.
Since the first (LSB) flip-flop needs to toggle at every clock pulse, its J and K inputs are connected to Vcc or Vdd, where they will be “high” all the time.
The next flip-flop need only “recognize” that the first flip-flop’s Q output is high to be made ready to toggle, so no AND gate is needed.
However, the remaining flip-flops should be made ready to toggle only when all lower-order output bits are “high,” thus the need for AND gates.

**Procedure**
1. Open Quartus and create a new project. Go to File -> New -> Verilog HDL File and type the program.

2. Compile and run the program.

3. Then go to Tools -> NetList Viewers -> RTL Viewer and generate the RTL schematic and save the logic diagram.

4. Then go to File -> New -> University program VWF. Create nodes for inputs and outputs to generate the timing diagram.

5. Give different input combinations and go to Run Functional Simulation to generate the timing diagram.


**PROGRAM**

```verilog
module counter 
(
    input wire clk,          
    input wire reset,        
    output reg [3:0] count   
);

always @(posedge clk) begin
    if (reset)
        count <= 4'b0000;   
    else
        count <= count + 1;  
end

endmodule
```

**RTL DIAGRAM**

![Screenshot (299)](https://github.com/user-attachments/assets/fe0ae55a-0168-41a8-a85c-297921358847)

**TRUTH TABLE**

![Screenshot (301)](https://github.com/user-attachments/assets/2728dd63-5f07-4fe0-aa5f-5ad021c73659)

**WAVEFORM**

![Screenshot (302)](https://github.com/user-attachments/assets/48567803-91a6-4fe0-bd20-e25e53a85c4a)

**RESULTS**
A 4 bit synchronous up counter has been implemented and the functionality has been validated
