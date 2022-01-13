# CPU

```
CHIP CPU {

    IN  inM[16],         // M value input  (M = contents of RAM[A])
        instruction[16], // Instruction for execution
        reset;           // Signals whether to re-start the current
                         // program (reset==1) or continue executing
                         // the current program (reset==0).

    OUT outM[16],        // M value output
        writeM,          // Write to M? 
        addressM[15],    // Address in data memory (of M)
        pc[15];          // address of next instruction

    PARTS:
    // Put your code here:
Or16(a=false, b=instruction, out[15]=isC,out[12]=aa,out[11]=c1,out[10]=c2,out[9]=c3,out[8]=c4,out[7]=c5,out[6]=c6,out[5]=d1,out[4]=d2,out[3]=d3,out[2]=j1,out[1]=j2,out[0]=j3);
    Not(in=isC,out=isA);
    //amux
    
    Mux16(a=instruction,b=aluout,sel=isC,out=amux);
    //ARegister
    And(a=isC,b=d1,out=cxd0);
    Or(a=isA,b=cxd0,out=aorcxd1);
    
    //mux a m
    Mux16(a=ra,b=inM,sel=aa,out=inmmuxra);
    //DRegister
    And(a=d2,b=isC,out=dd2);
    

    // jumps

    //Or(a=alung,b=aluzr,out=dau);
    //Not(in=dau,out=po);
    
    //Xor(a=j1,b=alung,out=nx1);
    //Xor(a=j2,b=aluzr,out=nx2);
    //Xor(a=j3,b=po,out=nx3);
    //Not(in=nx1,out=x1);
    //Not(in=nx2,out=x2);
    //Not(in=nx3,out=x3);
    //And(a=x1,b=x2,out=x4);
    //And(a=x3,b=x4,out=nnxend);

    Not(in=alung,out=notng);//偷抄
    Not(in=aluzr,out=notzr);
    And(a=notng,b=notzr,out=PO);
    
    And(a=j1,b=alung,out=out1);
    And(a=j2,b=aluzr,out=out2);
    And(a=j3,b=PO,out=out3);
    Or(a=out1,b=out2,out=out4);
    Or(a=out3,b=out4,out=jnj);
    //pc
    And(a=isC,b=jnj,out=pcload);
    //end
    ARegister(in=amux,load=aorcxd1,out=ra,out[0..14]=addressM);
    ALU(x=rd,y=inmmuxra,zx=c1,nx=c2,zy=c3,ny=c4,f=c5,no=c6,out=aluout,out=outM,zr=aluzr,ng=alung);
    DRegister(in=aluout,load=dd2,out=rd);
    And(a=isC,b=d3,out=writeM);
    PC(in=ra,load=pcload,inc=true,reset=reset,out[0..14]=pc);
}
```
![image](https://user-images.githubusercontent.com/81726807/149296647-d17c3b46-c37d-43f6-9de6-ad5dc5b8ecd3.png)
## 來源:https://www.itread01.com/content/1548693009.html
