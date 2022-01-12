# RAM64
```
// This file is part of www.nand2tetris.org
// and the book "The Elements of Computing Systems"
// by Nisan and Schocken, MIT Press.
// File name: projects/03/a/RAM64.hdl

/**
* Memory of 64 registers, each 16 bit-wide. Out holds the value
* stored at the memory location specified by address. If load==1, then 
* the in value is loaded into the memory location specified by address 
* (the loaded value will be emitted to out from the next time step onward).
*/

CHIP RAM64 {
    IN in[16], load, address[6];
    OUT out[16];

    PARTS:
    // Put your code here:
    DMux8Way(in=load,sel=address[3..5],a=DM0,b=DM1,c=DM2,d=DM3,e=DM4,f=DM5,g=DM6,h=DM7);
    RAM8(in=in,load=DM0,address=address[0..2],out=r0);
    RAM8(in=in,load=DM1,address=address[0..2],out=r1);
    RAM8(in=in,load=DM2,address=address[0..2],out=r2);
    RAM8(in=in,load=DM3,address=address[0..2],out=r3);
    RAM8(in=in,load=DM4,address=address[0..2],out=r4);
    RAM8(in=in,load=DM5,address=address[0..2],out=r5);
    RAM8(in=in,load=DM6,address=address[0..2],out=r6);
    RAM8(in=in,load=DM7,address=address[0..2],out=r7);
    Mux8Way16(a=r0,b=r1,c=r2,d=r3,e=r4,f=r5,g=r6,h=r7,sel=address[3..5],out=out);
}
```
![RAM64](https://user-images.githubusercontent.com/81726807/149163956-2a96dddb-5c12-4e79-ac1b-63a1822369dc.png)


# RAM512
```
// This file is part of the materials accompanying the book 
// "The Elements of Computing Systems" by Nisan and Schocken, 
// MIT Press. Book site: www.idc.ac.il/tecs
// File name: projects/03/b/RAM512.hdl

/**
* Memory of 512 registers, each 16 bit-wide. Out holds the value
* stored at the memory location specified by address. If load==1, then 
* the in value is loaded into the memory location specified by address 
* (the loaded value will be emitted to out from the next time step onward).
*/

CHIP RAM512 {
    IN in[16], load, address[9];
    OUT out[16];

    PARTS:
    // Put your code here:
    DMux8Way(in=load,sel=address[6..8],a=DM0,b=DM1,c=DM2,d=DM3,e=DM4,f=DM5,g=DM6,h=DM7);
    RAM64(in=in,load=DM0,address=address[0..5],out=r0);
    RAM64(in=in,load=DM1,address=address[0..5],out=r1);
    RAM64(in=in,load=DM2,address=address[0..5],out=r2);
    RAM64(in=in,load=DM3,address=address[0..5],out=r3);
    RAM64(in=in,load=DM4,address=address[0..5],out=r4);
    RAM64(in=in,load=DM5,address=address[0..5],out=r5);
    RAM64(in=in,load=DM6,address=address[0..5],out=r6);
    RAM64(in=in,load=DM7,address=address[0..5],out=r7);
    Mux8Way16(a=r0,b=r1,c=r2,d=r3,e=r4,f=r5,g=r6,h=r7,sel=address[6..8],out=out);
}
```
![RAM512](https://user-images.githubusercontent.com/81726807/149164118-2fed5db4-cc69-43cb-a300-a5c4b6e62b12.png)

# RAM4K

```
// This file is part of www.nand2tetris.org
// by Nisan and Schocken, MIT Press.
// File name: projects/03/b/RAM4K.hdl

/**
* Memory of 4K registers, each 16 bit-wide. Out holds the value
* stored at the memory location specified by address. If load==1, then 
* the in value is loaded into the memory location specified by address 
* (the loaded value will be emitted to out from the next time step onward).
*/

CHIP RAM4K {
    IN in[16], load, address[12];
    OUT out[16];

    PARTS:
    // Put your code here:
    DMux8Way(in=load,sel=address[9..11],a=DM0,b=DM1,c=DM2,d=DM3,e=DM4,f=DM5,g=DM6,h=DM7);
    RAM512(in=in,load=DM0,address=address[0..8],out=r0);
    RAM512(in=in,load=DM1,address=address[0..8],out=r1);
    RAM512(in=in,load=DM2,address=address[0..8],out=r2);
    RAM512(in=in,load=DM3,address=address[0..8],out=r3);
    RAM512(in=in,load=DM4,address=address[0..8],out=r4);
    RAM512(in=in,load=DM5,address=address[0..8],out=r5);
    RAM512(in=in,load=DM6,address=address[0..8],out=r6);
    RAM512(in=in,load=DM7,address=address[0..8],out=r7);
    Mux8Way16(a=r0,b=r1,c=r2,d=r3,e=r4,f=r5,g=r6,h=r7,sel=address[9..11],out=out);
}
```
![RAM4K](https://user-images.githubusercontent.com/81726807/149164157-0c54cc06-64d0-4fb5-aab3-5e27e5da4c37.png)


# RAM16K
```
// This file is part of www.nand2tetris.org
// and the book "The Elements of Computing Systems"
// by Nisan and Schocken, MIT Press.
// File name: projects/03/b/RAM16K.hdl

/**
* Memory of 16K registers, each 16 bit-wide. Out holds the value
* stored at the memory location specified by address. If load==1, then 
* the in value is loaded into the memory location specified by address 
* (the loaded value will be emitted to out from the next time step onward).
*/

CHIP RAM16K {
    IN in[16], load, address[14];
    OUT out[16];

    PARTS:
    // Put your code here:
    DMux4Way(in=load,sel=address[12..13],a=DM0,b=DM1,c=DM2,d=DM3);
    RAM4K(in=in,load=DM0,address=address[0..11],out=r0);
    RAM4K(in=in,load=DM1,address=address[0..11],out=r1);
    RAM4K(in=in,load=DM2,address=address[0..11],out=r2);
    RAM4K(in=in,load=DM3,address=address[0..11],out=r3);
    Mux4Way16(a=r0,b=r1,c=r2,d=r3,sel=address[12..13],out=out);
}
```
![RAM16K](https://user-images.githubusercontent.com/81726807/149164178-048a3597-1883-4c63-ad00-2c303ca6233c.png)

# PC
```
// This file is part of www.nand2tetris.org
// and the book "The Elements of Computing Systems"
// by Nisan and Schocken, MIT Press.
// File name: projects/03/a/PC.hdl

/**
 * A 16-bit counter with load and reset control bits.
 * if      (reset[t] == 1) out[t+1] = 0
 * else if (load[t] == 1)  out[t+1] = in[t]
 * else if (inc[t] == 1)   out[t+1] = out[t] + 1  (integer addition)
 * else                    out[t+1] = out[t]
 */

CHIP PC {
    IN in[16],load,inc,reset;
    OUT out[16];

    PARTS:
    // Put your code here:
    Inc16(in=PC,out=PCI);
    Mux16(a=PC,b=PCI,sel=inc,out=PCN);
    Mux16(a=PCN,b=in,sel=load,out=Load);
    Mux16(a=Load,b=false,sel=reset,out=Re);
  
ter(in=Re,load=true,out=PC,out=out);
}
```
![unknown](https://user-images.githubusercontent.com/81726807/149164230-17115be2-9097-4e07-94c7-ddf4b61d9bac.png)
