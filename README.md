Download Link: https://assignmentchef.com/product/solved-ca108-homework-3-verilog-exercise-matrix-vector-multiplication
<br>



<h1>1.      Introduction</h1>

In this exercise, you need to design a Verilog program to compute the operation 2*A*x + b. Vectors x and b are directly sent to your circuit and matrix A is stored in a memory. You need to access the memory to acquire the data and then compute the answer y. Here is an example of y = 2*A*x + b, where the dimension of matrix A is 2×2 and the size of vectors x and b is 2×1.




In this exercise, the size of matrix A is 16×16 and the size of vectors x and b is 16×1. Each number in the matrix or vectors are represented with 8 bits. The numbers are unsigned. You don’t need to consider overflow problem in this exercise, so the numbers of the output vector are also represented in 8 bits.




<h1>2.      Specification</h1>

The input/output pins are defined in Table1:

Tabel1 :I/O pins specification

<table width="553">

 <tbody>

  <tr>

   <td width="104"><strong>Signal name </strong></td>

   <td width="113"><strong>Input / Output </strong></td>

   <td width="76"><strong>Bit width </strong></td>

   <td width="260"><strong>Description </strong></td>

  </tr>

  <tr>

   <td width="104"><strong>CLK </strong></td>

   <td width="113">I</td>

   <td width="76">1</td>

   <td width="260">Clock signal.Positive edge trigger.</td>

  </tr>

  <tr>

   <td width="104"><strong>RST </strong></td>

   <td width="113">I</td>

   <td width="76">1</td>

   <td width="260">Active high <strong>asynchronous</strong> reset signal.</td>

  </tr>

  <tr>

   <td width="104"><strong>vector_x </strong></td>

   <td width="113">I</td>

   <td width="76">128</td>

   <td width="260">Input data <strong>x</strong>16×1. This signal is consistent.</td>

  </tr>

  <tr>

   <td width="104"><strong>vector_b </strong></td>

   <td width="113">I</td>

   <td width="76">128</td>

   <td width="260">Input data <strong>b</strong>16×1. This signal is consistent.</td>

  </tr>

  <tr>

   <td width="104"><strong>vector_y </strong></td>

   <td width="113">O</td>

   <td width="76">128</td>

   <td width="260">Output data <strong>y</strong>16×1.It’ll be checked when finish is 1.</td>

  </tr>

  <tr>

   <td width="104"><strong>Q </strong></td>

   <td width="113">I</td>

   <td width="76">128</td>

   <td width="260">Input data sent from memory.</td>

  </tr>

  <tr>

   <td width="104"><strong>A </strong></td>

   <td width="113">O</td>

   <td width="76">4</td>

   <td width="260">The address of the memory.</td>

  </tr>

  <tr>

   <td width="104"><strong>finish </strong></td>

   <td width="113">O</td>

   <td width="76">1</td>

   <td width="260">Control signal.Set it 1 when all the computation is done; otherwise set it 0.</td>

  </tr>

 </tbody>

</table>







<h1>3.      Timing Diagram for Memory</h1>

Fig. 1 shows the timing diagram for reading data from a memory. Here CEN is always 0 and WEN is always 1. You just need to control the address A in this exercise. Note that you may need to operate CEN and WEN signals by yourself in the future exercises. Here the memory stores matrix A. The i-th word in the memory represents A<sub>i,0:15</sub>. You can change A to access different words in the memory.







<h1>4.      Simulation Scripts</h1>

4.1 Sample Code: findmax

Circuit findmax.v finds the max and argmax value for eight continuous inputs. Visit folder sample/findmax and run the following script.

<h1>ncverilog testfixture.v findmax.v +access+r</h1>

4.2 Sample Code: matvec2x2

Circuit matvec2x2.v computes matrix-vector multiplication Ax. In this sample, the size of matrix A is 2×2 and the size of vector x is 2×1. Visit folder sample/matvec2x2 and run the following script.

This sample is similar to the exercise. If you’re not very familiar with Verilog, please make sure you fully understand this sample code.

<strong>ncverilog testfixture.v matvec2x2.v +access+r +define+tb1 +notimingchecks </strong>

4.3 RTL Simulation

<h1>ncverilog testfixture.v matvecmult.v +access+r +define+tb1 +notimingchecks</h1>

You can change between test cases by substituting tb1 to tb2

4.4 Synthesis

Please execute this script in syn folder. Synopsys Design Compiler will automatically synthesize your RTL code into gate-level netlist following the commands in this script.

<h1>dc_shell Run the code: source run.tcl</h1>

Please check if there’s any error message (you can ignore most warning messages). If any, read the error messages and try to resolve them; if not, enter exit to leave Design Compiler.

<h2>4.5               Gate-level Simulation ncverilog testfixture.v matvecmult_syn.v -v tsmc13.v +access+r +define+tb1+SDF</h2>

4.6 Debug

Use program nWave to view the simulated signals. This will be very helpful for this exercise. <strong>nWave&amp; </strong>

<strong> </strong>

<h1>5.      Files</h1>

The deadline for this exercise is 13:00, Dec. 3th. Please pack your files in a folder named CA_hw3_yourid, compress it into a HW3.zip file and then submit to CEIBA.

There’s a 5% penalty for incorrect upload format. No late submission is accepted.

Example:

./CA_hw3_r08943016/  matvecmult.v    (RTL file)  matvecmult_syn.v   (synthesized gate-level netlist)

matvecmult_syn.ddc (Design database generated by Synopsys Design Compiler) <strong>  </strong>matvecmult_syn.sdf (Pre-layout gate-level sdf)          r08943016.pdf            area.txt            timing.txt