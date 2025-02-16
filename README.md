# Exp-6-Synchornous-counters - up counter and down counter 
### AIM: To implement 4 bit up and down counters and validate  functionality.
### HARDWARE REQUIRED:  – PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:   Quartus prime
### THEORY 

## UP COUNTER 
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



## DOWN COUNTER 

As well as counting “up” from zero and increasing or incrementing to some preset value, it is sometimes necessary to count “down” from a predetermined value to zero allowing us to produce an output that activates when the zero count or some other pre-set value is reached.

This type of counter is normally referred to as a Down Counter, (CTD). In a binary or BCD down counter, the count decreases by one for each external clock pulse from some preset value. Special dual purpose IC’s such as the TTL 74LS193 or CMOS CD4510 are 4-bit binary Up or Down counters which have an additional input pin to select either the up or down count mode.
![image](https://user-images.githubusercontent.com/36288975/169644844-1a14e123-7228-4ed8-81a9-eb937dff4ac8.png)


4-bit Count Down Counter
### Procedure
/* write all the steps invloved */



### PROGRAM 
```
UP COUNTER
module upcounter(clk,a);
input clk;
output reg[3:0]a;
always@(posedge clk)
begin
a[3]=(a[2] & a[1] & a[0]) ^ a[3];
a[2]=(a[1] & a[0]) ^ a[2];
a[1]=(a[0] ^ a[1]);
a[0]=1 ^ a[0];
end
endmodule

DOWN COUNTER
module downcounter(clk,a);
input clk;
output reg[3:0]a;
always@(posedge clk)
begin
a[3]=(~a[2] & ~a[1] & ~a[0])^ a[3];
a[2]=(~a[1] & ~a[0]) ^ a[2];
a[1]=(~a[0] ^ a[1]);
a[0]=1 ^ a[0];
end
endmodule
````
/*
Program for flipflops  and verify its truth table in quartus using Verilog programming.
```
Developed by:Hariharan.S
RegisterNumber:212222050016
```
*/






### RTL LOGIC UP COUNTER AND DOWN COUNTER  
UP COUNTER![uprtl](https://github.com/Hariharan2004S/Exp-7-Synchornous-counters-/assets/123146156/44547ec2-eaf8-4cfa-a21f-a9a04ed1b4e2)

DOWN COUNTER![WhatsApp Image 2023-06-07 at 13 19 10](https://github.com/Hariharan2004S/Exp-7-Synchornous-counters-/assets/123146156/65c8505e-1ac0-4ada-8c81-d092274cd56c)









### TIMING DIGRAMS FOR COUNTER  
UP COUNTER![uptd](https://github.com/Hariharan2004S/Exp-7-Synchornous-counters-/assets/123146156/12b46c76-3e4c-43c4-99a8-70486f241449)


DOWN COUNTER![dctd](https://github.com/Hariharan2004S/Exp-7-Synchornous-counters-/assets/123146156/8cbbfae6-3d04-4983-8f99-0f54d102e2be)





### TRUTH TABLE
UP COUNTER![UPcounter](https://github.com/Hariharan2004S/Exp-7-Synchornous-counters-/assets/123146156/42fc32ed-172d-4067-a03f-f4e70ef59836)


DOWN COUNTER![downcounter](https://github.com/Hariharan2004S/Exp-7-Synchornous-counters-/assets/123146156/d4e8de51-8e4c-4a0f-9316-3ff8ecde2bd0)




### RESULTS 
