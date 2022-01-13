# 這次作業是複製陳育誠學長的已經過本人同意
# 網址:https://github.com/cycyucheng1010/co109a/blob/master/20201123HW9.md
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
 
# Fill
```
// This file is part of www.nand2tetris.org
// and the book "The Elements of Computing Systems"
// by Nisan and Schocken, MIT Press.
// File name: projects/04/Fill.asm

// Runs an infinite loop that listens to the keyboard input.
// When a key is pressed (any key), the program blackens the screen,
// i.e. writes "black" in every pixel;
// the screen should remain fully black as long as the key is pressed. 
// When no key is pressed, the program clears the screen, i.e. writes
// "white" in every pixel;
// the screen should remain fully clear as long as no key is pressed.

// Put your code here.
//16384---->screen
//24576---->keyboard
@8192               
D=A               
@0                
M=D                
@24576
D=M
@18                  
D;JNE            //IF OUT!=0 JUMP TO LINE 18
//WHITE LOOP
@0
D=M               
M=M-1                
@0              
D;JEQ           //IF OUT ==0 JUMP TO 0     
@16383          //16384開始是螢幕
A=D+A                
M=0              
@8                
0;JMP         //開始下次迴圈       
//BLACK LOOP
@0
D=M
M=M-1
@0
D;JEQ        //IF OUT ==0 JUMP TO 0        
@24576
A=A-D
M=-1
@18
0;JMP       //開始下次迴圈
```
![003](https://user-images.githubusercontent.com/81726807/149135052-12b91c31-5ac5-4bf3-afcb-744561bc58dc.png)
