# VLSI-LAB-EXPERIMENTS
# AIM:
To simulate and synthesis Logic Gates,Adders and Subtractor using vivado

# APPARATUS REQUIRED:
Vivado

# PROCEDURE: 
1. Open Vivado: Launch Xilinx Vivado software on your computer.

2. Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

3. Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

4. Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

5. Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

6. Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

7. Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

8. Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

9. View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.

# Logic Diagram :

Logic Gates:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)


Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)


Full adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)


Half Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)



Full Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)



8 Bit Ripple Carry Adder

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)



# VERILOG CODE:

# Logic Gates:
```
module logicgate (a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
input a,b;  
output andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate;
and(andgate,a,b);
or(orgate,a,b);
xor(xorgate,a,b);
nand(nandgate,a,b); 
nor(norgate,a,b);
xnor(xnorgate,a,b);
not(notgate,a);
endmodule
```
# Half Adder:
```
module halfadder(a,b,sum,carry);
input a,b;
output sum,carry;
xor g1(sum,a,b);
and g2(carry,a,b);
endmodule
```
# Half Subractor:
```
module halfsubtractor(a,b,diff,borrow);
input a,b;
output diff,borrow;
xor g1(diff,a,b);
and g2(borrow,~a,b);
endmodule
```
# Full Adder:
```
module fadd(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
wire w1,w2,w3;
xor g1(w1,a,b);
and g2(w2,a,b);
xor g3(sum,w1,c);
and g4(w3,w1,c);
or g5(carry,w3,w2);
endmodule
```
# Full Subtractor:
```
module fs(a,b,bin,d,bout);
input a,b,bin; 
output d,bout;
wire w1,w2,w3;
xor g1(w1,b,bin; 
xor g2(d,w1,a);
and g3(w2,a,~w1);
and g4(w3,~b,bin);
or g5(bout,w2,w3);
endmodule
```
# 4 bit ripple carry adder:
```
module rippe_adder(S,Cout,X,Y,Cin);
input [3:0] X,Y;
input Cin;
output [3:0] S;
output Cout;
wire w1,w2,w3;
fulladder u1(S[0],w1,X[0],Y[0],Cin);
fulladder u2(S[1],w2,X[1],Y[1],w1);
fulladder u3(S[2],w3,X[2],Y[2],w2);
fulladder u4(S[3],Cout,X[3],Y[3],w3);
endmodule

module fulladder(S,CO,X,Y,Ci);
input X,Y,Ci;
output S,CO;
wire w1,w2,w3;
xor G1(w1,X,Y);
xor G2(S,w1,Ci);
and G3(w2,X,Ci);
and G4(w3,X,Y);
or G5(CO,w3,w3);
endmodule
```
# 8 bit ripple carry adder:
```
module rippe_adder(S,Cout,X,Y,Cin);
input [7:0] X,Y;
input Cin;
output [7:0] S;
output Cout;
wire w1,w2,w3,w4,w5,w6,w7;
fulladder u1(S[0],w1,X[0],Y[0],Cin);
fulladder u2(S[1],w2,X[1],Y[1],w1);
fulladder u3(S[2],w3,X[2],Y[2],w2);
fulladder u4(S[3],w4,X[3],Y[3],w3);
fulladder u5(S[4],w5,X[4],Y[4],w4);
fulladder u6(S[5],w6,X[5],Y[5],w5);
fulladder u7(S[6],w7,X[6],Y[6],w6);
fulladder u8(S[7],Cout,X[7],Y[7],w7);
endmodule

module fulladder(S,CO,X,Y,Ci);
input X,Y,Ci;
output S,CO;
wire w1,w2,w3;
xor G1(w1,X,Y);
xor G2(S,w1,Ci);
and G3(w2,X,Ci);
and G4(w3,X,Y);
or G5(CO,w3,w3);
endmodule
```
# OUTPUT:
# OR gate:
![image](https://github.com/KabilanBaskaran0807/VLSI-LAB-EXP-1/assets/166724685/78287d03-bd28-451e-a6f5-3b90a3241f23)



NOT gate:
![image](https://github.com/KabilanBaskaran0807/VLSI-LAB-EXP-1/assets/166724685/5c2fd618-f855-407f-9eef-e9970a70fbec)


AND gate:
![image](https://github.com/KabilanBaskaran0807/VLSI-LAB-EXP-1/assets/166724685/183f47f5-5fab-4239-a093-7aad81698dac)


NAND gate:
![image](https://github.com/KabilanBaskaran0807/VLSI-LAB-EXP-1/assets/166724685/2c890e01-ec81-4be6-9268-1014ae4fa30f)


NOR gate:
![image](https://github.com/KabilanBaskaran0807/VLSI-LAB-EXP-1/assets/166724685/0f12bde3-5888-4b5e-93cb-1c16571a513d)


XNOR gate:
![image](https://github.com/KabilanBaskaran0807/VLSI-LAB-EXP-1/assets/166724685/37149034-bdd3-4d40-8967-5fd7f98f6bf2)


XOR gate:
![image](https://github.com/KabilanBaskaran0807/VLSI-LAB-EXP-1/assets/166724685/4dc484ac-1f5d-49b9-8a81-ab446b77073d)


Half Adder:
![image](https://github.com/KabilanBaskaran0807/VLSI-LAB-EXP-1/assets/166724685/20cf9b91-eaaa-407b-b6b4-c4df54006f27)


Half Subtracter:
![image](https://github.com/KabilanBaskaran0807/VLSI-LAB-EXP-1/assets/166724685/0c52931d-75d7-4a2d-9944-3d91adee3b90)


Full Adder:
![image](https://github.com/KabilanBaskaran0807/VLSI-LAB-EXP-1/assets/166724685/418e4cdf-f507-4431-9276-9d795c0a90bb)


Full Subtracter:
![image](https://github.com/KabilanBaskaran0807/VLSI-LAB-EXP-1/assets/166724685/70859e6b-5454-4c8b-ad56-be876a254e85)


4 Bit Ripple Carry Adder:
![image](https://github.com/KabilanBaskaran0807/VLSI-LAB-EXP-1/assets/166724685/ca98bb86-d870-4fb0-b940-4d4b2fee3480)


8 Bit Ripple Carry Adder:
![image](https://github.com/KabilanBaskaran0807/VLSI-LAB-EXP-1/assets/166724685/73e264b3-5aa2-4087-a3c4-7ae0105fa7c4)


# RESULT:
Hence Logic Gates,Adders and Subtractor are simulated and synthesised using vivado

