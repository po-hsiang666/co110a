# MULT
```
// This file is part of www.nand2tetris.org
// and the book "The Elements of Computing Systems"
// by Nisan and Schocken, MIT Press.
// File name: projects/04/Mult.asm

// Multiplies R0 and R1 and stores the result in R2.
// (R0, R1, R2 refer to RAM[0], RAM[1], and RAM[2], respectively.)

// Put your code here.

@2    // R2=0
M=0
@0   //R0=M 
D=M
@50  //IF R0=0 , JUMP TO R50  0*ANY=0
D;JEQ 
@1  //R1=M
D=M
@50 //IF R1=0,JUMP TO R50 ANY*0=0
D;JEQ
@12 //LOOP 
D;JNE
@0
D=M
@2
M=M+D // mult=>a=a+b do x times 
@1
M=M-1
D=M
@12 //LOOP


```
hack

![001](https://user-images.githubusercontent.com/81726807/149134347-9cf67d76-be7e-4e04-a4ad-1bdb3c0d7c70.png)


result
![002](https://user-images.githubusercontent.com/81726807/149134374-af7aba73-3593-4be7-b8c4-a73a00576f11.png)

