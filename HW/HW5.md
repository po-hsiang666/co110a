# Bit
```
/**
 * 1-bit register:
 * If load[t] == 1 then out[t+1] = in[t]
 *                 else out does not change (out[t+1] = out[t])
 */

CHIP Bit {
    IN in, load;
    OUT out;

    PARTS:
    // Put your code here:
    Mux(a=gayout,b=in,sel=load,out=a);
    DFF(in=a,out=out,out=gayout);
}
```
# Register
```
// This file is part of www.nand2tetris.org
// and the book "The Elements of Computing Systems"
// by Nisan and Schocken, MIT Press.
// File name: projects/03/a/Register.hdl

/**
 * 16-bit register:
 * If load[t] == 1 then out[t+1] = in[t]
 * else out does not change
 */

CHIP Register {
    IN in[16], load;
    OUT out[16];

    PARTS:
    // Put your code here:
    Bit(in=in[0],load=load,out=out[0]);
    Bit(in=in[1],load=load,out=out[1]);
    Bit(in=in[2],load=load,out=out[2]);
    Bit(in=in[3],load=load,out=out[3]);
    Bit(in=in[4],load=load,out=out[4]);
    Bit(in=in[5],load=load,out=out[5]);
    Bit(in=in[6],load=load,out=out[6]);
    Bit(in=in[7],load=load,out=out[7]);
    Bit(in=in[8],load=load,out=out[8]);
    Bit(in=in[9],load=load,out=out[9]);
    Bit(in=in[10],load=load,out=out[10]);
    Bit(in=in[11],load=load,out=out[11]);
    Bit(in=in[12],load=load,out=out[12]);
    Bit(in=in[13],load=load,out=out[13]);
    Bit(in=in[14],load=load,out=out[14]);
    Bit(in=in[15],load=load,out=out[15]);
}
```
![image](https://user-images.githubusercontent.com/81726807/149163630-81c1a44f-fee1-4c98-b43a-a4685e7ef48d.png)

# RAM8
```
/**
* Memory of 8 registers, each 16 bit-wide. Out holds the value
* stored at the memory location specified by address. If load==1, then 
* the in value is loaded into the memory location specified by address 
* (the loaded value will be emitted to out from the next time step onward).
*/

CHIP RAM8 {
    IN in[16], load, address[3];
    OUT out[16];

    PARTS:
    // Put your code here:
    DMux8Way(in=load,sel=address,a=DM0,b=DM1,c=DM2,d=DM3,e=DM4,f=DM5,g=DM6,h=DM7);
    Register(in=in,load=DM0,out=r0);
    Register(in=in,load=DM1,out=r1);
    Register(in=in,load=DM2,out=r2);
    Register(in=in,load=DM3,out=r3);
    Register(in=in,load=DM4,out=r4);
    Register(in=in,load=DM5,out=r5);
    Register(in=in,load=DM6,out=r6);
    Register(in=in,load=DM7,out=r7);
    Mux8Way16(a=r0,b=r1,c=r2,d=r3,e=r4,f=r5,g=r6,h=r7,sel=address,out=out);
}
```
