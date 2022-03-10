# DFF_toSR_FLIPFLOP


## Table of Contents

- Abstract 
- Author
- Acknowledgements
- References
## Abstract 
The process of converting the given D flip-flop into an SR-type is initiated by obtaining a table which represents both the information present in the truth table of the SR flip-flop as well as the information conveyed by the excitation table of the D flip-flop. Such a table is referred to as the D-to-SR conversion table
## Introduction
 In S-R flip-flop, if Q = 0 the output is said to be reset and set for Q = 1. Explanation: The output of latches will remain in set/reset untill the trigger pulse is given to change the state. D Flip-flops are used as a part of memory storage elements and data processors as well. D flip-flop can be built using NAND gate or with NOR gate. Due to its versatility they are available as IC packages. The major applications of D flip-flop are to introduce delay in timing circuit, as a buffer, sampling data at specific intervals. D flip-flop is simpler in terms of wiring connection compared to JK flip-flop. Here we are using NAND gates for demonstrating the D flip flop.</br>

## Reference Circuit Diagram

The fig. here represents the Model schematis that is to be implemented here.</br>
<p align="center">
<img src="https://user-images.githubusercontent.com/100523474/157721129-d49ca9a1-64cf-471c-812d-0ed73322f44a.png">
</p>


## Reference Waveform
<p align="center">
  <img src="https://user-images.githubusercontent.com/100523474/157722013-17c35907-fd3e-46ec-96bb-4c9bbb3f00d3.png">
</p>






## Circuit Implementation</br>
</br>
<p align="center">
  <img src="https://user-images.githubusercontent.com/100523474/157722483-52098a3c-0fc4-4861-94f3-426155441663.png">
</p>

## Output Waveform</br>
![image](https://user-images.githubusercontent.com/100523474/157724307-67e30be0-67d6-4339-96a6-1203891ad377.png)




## Verilog implementaion of D-Latch</br>
- Code used</br>
module d_latch (  input d,           // 1-bit input pin for data  
                  input en,          // 1-bit input pin for enabling the latch  
                  input rstn,        // 1-bit input pin for active-low reset  
                  output reg q);     // 1-bit output pin for data output  
  
   // This always block is "always" triggered whenever en/rstn/d changes  
   // If reset is asserted, then the output will be zero   
   // Else as long as enable is high, output q follows input d  
  
   always @ (en or rstn or d)  
      if (!rstn)  
         q <= 0;  
      else  
         if (en)  
            q <= d;  
endmodule   
- Makerchip Display</br>

\TLV_version 1d: tl-x.org
\SV
/* verilator lint_off UNUSED*/  /* verilator lint_off DECLFILENAME*/  /* verilator lint_off BLKSEQ*/  /* verilator lint_off WIDTH*/  /* verilator lint_off SELRANGE*/  /* verilator lint_off PINCONNECTEMPTY*/  /* verilator lint_off DEFPARAM*/  /* verilator lint_off IMPLICIT*/  /* verilator lint_off COMBDLY*/  /* verilator lint_off SYNCASYNCNET*/  /* verilator lint_off UNOPTFLAT */  /* verilator lint_off UNSIGNED*/  /* verilator lint_off CASEINCOMPLETE*/  /* verilator lint_off UNDRIVEN*/  /* verilator lint_off VARHIDDEN*/  /* verilator lint_off CASEX*/  /* verilator lint_off CASEOVERLAP*/  /* verilator lint_off PINMISSING*/ /* verilator lint_off BLKANDNBLK*/  /* verilator lint_off MULTIDRIVEN*/  /* verilator lint_off ASSIGNDLY*/  /* verilator lint_off MODDUP*/  /* verilator lint_off STMTDLY*/  /* verilator lint_off LITENDIAN*/  /* verilator lint_off INITIALDLY*/    

//Your Verilog/System Verilog Code Starts Here:
module dlatch (  input d,           // 1-bit input pin for data  
                  input en,          // 1-bit input pin for enabling the latch  
                  input rstn,        // 1-bit input pin for active-low reset  
                  output reg q);     // 1-bit output pin for data output  
  
   // This always block is "always" triggered whenever en/rstn/d changes  
   // If reset is asserted, then the output will be zero   
   // Else as long as enable is high, output q follows input d  
  
   always @ (en or rstn or d)  
      if (!rstn)  
         q <= 0;  
      else  
         if (en)  
            q <= d;  
endmodule  

//Top Module Code Starts here:
	module top(input logic clk, input logic reset, input logic [31:0] cyc_cnt, output logic passed, output logic failed);
		logic  d;//input
		logic  en;//input
		logic  rstn;//input
		logic  q;//output
//The $random() can be replaced if user wants to assign values
		assign d = 20'b01001010011011001100;
		assign en = 20'b01010101010101010101;
		assign rstn = 20'b10000000000000000000;
		dlatch dlatch(.d(d), .en(en), .rstn(rstn), .q(q));
	
\TLV
//Add \TLV here if desired                                     
\SV
endmodule


## Simulation Results and Observation</br>
</br>
<p align="center">
  <img src="https://user-images.githubusercontent.com/86653033/157718393-8cb21aee-2a7e-4536-be97-c5ea37c6bc4c.png">
</p>


- Input and Output to the circuit</br>


- Final results for each block</br>


- After increaing the Frequency of the input</br>



## Observation and Calculation</br>

![image](https://user-images.githubusercontent.com/100523474/157722962-37f0e918-4951-459d-aae0-9fa514f2a0a4.png)

-By the truth table we can observe that the Dff is coverted to SR flip floip  </br>
- Here we note that the last two rows of the conversion table have X (Don't Cares) in the "D Input" column. This is because with an SR flip-flop the input combination of S = R = 1 is invalid (because the output will be unpredictable).
Our next step will be to obtain the logical expression for the input of the given D flip-flop in terms of the inputs of the desired flip-flop, S and R, and the present-state, Qn. However, while doing so, we need to simplify the Boolean expression as much as possible using a suitable simplification technique, such as the K-map. </br>

## Result
D flip flop to S-R flip flop is implemented on 180nm Technology using Ngspice Smulation Tool (It is an Open Source EDA developed by FOSSEE, IIT Bombay. It is used for electronic circuit simulation. It is made by the combination of two software namely NgSpice and KiCAD.)
</br>

## Author

Priyanka Tiwari, Govt. Engineering College Raipur (Electronics &Telecommunication)

## Acknowledgements
- Kunal Ghosh (Co-Founder, VLSI System Design Pvt. Ltd.)

- FOSSEE, IIT Bombay

- Steve Hoover (Founder, Redwood EDA)

- Sumanto Kar (eSim Team, FOSSEE, IIT Bombay)


## References
[1] H. Dadhich, V. Maurya, K. Verma and S. Jaiswal, "Design and analysis of different type of charge pump using CMOS technology," 2016 International Conference on Advances in Computing, Communications and Informatics (ICACCI), 2016, pp. 294-298, doi: 10.1109/ICACCI.2016.7732062.
[2] https://www.electronicshub.org/d-flip-flop/
[3] https://www.allaboutcircuits.com/technical-articles/conversion-of-flip-flops-part-iv-d-flip-flops/
