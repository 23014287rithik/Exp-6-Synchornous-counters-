# Exp-6: Synchornous counters up counter and down counter 
## AIM: 
To implement 4 bit up and down counters and validate functionality.
## Equipments Required:
Hardware Required: PC, Cyclone II , USB flasher
Software Required: Quartus prime
## THEORY 

### UP COUNTER 
The counter is a digital sequential circuit and here it is a 4 bit counter, which simply means it can count from 0 to 15 and vice versa based upon the direction of counting (up/down). 

The counter (“count“) value will be evaluated at every positive (rising) edge of the clock (“clk“) cycle.
The Counter will be set to Zero when “reset” input is at logic high.
The counter will be loaded with “data” input when the “load” signal is at logic high. Otherwise, it will count up or down.
The counter will count up when the “up_down” signal is logic high, otherwise count down

Since we know that binary count sequences follow a pattern of octave (factor of 2) frequency division, and that J-K flip-flop multivibrators set up for the “toggle” mode are capable of performing this type of frequency division, we can envision a circuit made up of several J-K flip-flops, cascaded to produce four bits of output.
The main problem facing us is to determine how to connect these flip-flops together so that they toggle at the right times to produce the proper binary sequence.
Examine the following binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1:
Binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1.

Note that each bit in this four-bit sequence toggles when the bit before it (the bit having a lesser significance, or place-weight), toggles in a particular direction: from 1 to 0.

Starting with four J-K flip-flops connected in such a way to always be in the “toggle” mode, we need to determine how to connect the clock inputs in such a way so that each succeeding bit toggles when the bit before it transitions from 1 to 0.
The Q outputs of each flip-flop will serve as the respective binary bits of the final, four-bit count:
Four-bit “Up” Counter

![image](https://user-images.githubusercontent.com/36288975/169644758-b2f4339d-9532-40c5-af40-8f4f8c942e2c.png)

### DOWN COUNTER 

As well as counting “up” from zero and increasing or incrementing to some preset value, it is sometimes necessary to count “down” from a predetermined value to zero allowing us to produce an output that activates when the zero count or some other pre-set value is reached.

This type of counter is normally referred to as a Down Counter, (CTD). In a binary or BCD down counter, the count decreases by one for each external clock pulse from some preset value. Special dual purpose IC’s such as the TTL 74LS193 or CMOS CD4510 are 4-bit binary Up or Down counters which have an additional input pin to select either the up or down count mode.
![image](https://user-images.githubusercontent.com/36288975/169644844-1a14e123-7228-4ed8-81a9-eb937dff4ac8.png)


4-bit Count Down Counter

## Procedure
1. Create a new project in Quartus II software.
2. Name the project as uc for upcounter and dc for downcounter.
3. Create a new Verilog HDL file in the project file.
4. Name the module as dc and uc for downcounter and upcounter.
5. Within the module declare input and output variables.
6. Complete the program.
7. End the module.

## PROGRAM 
### UP COUNTER
```
module uc(clk, A);
input clk;
output reg [2:0]A;
always @(posedge clk)
begin
A[2]=(((A[0])&(A[1]))^A[2]);
A[1]=(A[0])^A[1];
A[0]=A[0]^1;
end
endmodule
```
### DOWN COUNTER
```
module dc(clk,A);
input clk;
output reg [2:0]A;
always @(posedge clk)
begin
A[2]=(((~A[0])&(~A[1]))^A[2]);
A[1]=(~A[0])^A[1];
A[0]=1^A[0];
end
endmodule
```

## RTL LOGIC UP COUNTER AND DOWN COUNTER  
### UP COUNTER
![Screenshot 2023-12-26 174741](https://github.com/23014287rithik/Exp-6-Synchornous-counters-/assets/150985832/46990739-250b-4fce-9902-8fedd8f02c37)


 ### DOWN COUNTER

 ![Screenshot 2023-12-26 174749](https://github.com/23014287rithik/Exp-6-Synchornous-counters-/assets/150985832/e98cc933-19e6-4975-a79b-1aaddba98429)

## TIMING DIGRAMS FOR COUNTER  
### UP COUNTER

![Screenshot 2023-12-26 174804](https://github.com/23014287rithik/Exp-6-Synchornous-counters-/assets/150985832/18945d14-d8d2-4381-9fef-241ff703be52)

 ### DOWN COUNTER
![Screenshot 2023-12-26 174813](https://github.com/23014287rithik/Exp-6-Synchornous-counters-/assets/150985832/ad0edec8-1c1f-4f93-9b8c-70a91e3e1464)

 
## TRUTH TABLE
### UP COUNTER

![Screenshot 2023-12-26 174822](https://github.com/23014287rithik/Exp-6-Synchornous-counters-/assets/150985832/de5c5bfc-0029-4a02-8ecf-0bb5b6cd7690)


 
### DOWN COUNTER


 ![Screenshot 2023-12-26 174833](https://github.com/23014287rithik/Exp-6-Synchornous-counters-/assets/150985832/366cbac4-5efc-4ee2-9313-999227f5803e)


### RESULTS 
Thus we have verified the truthtable of 4-bit up and down counter using verilog.
