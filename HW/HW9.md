# Memory
```
CHIP Memory {
    IN in[16], load, address[15];
    OUT out[16];

    PARTS:
    // Put your code here:
    
    //RAM( 0 ~ 16383 )
    Not(in=address[14],out=n14);
    And(a=n14 ,b=load ,out=R0);
    RAM16K(in=in ,load=R0 ,address=address[0..13] ,out=o0);
    
    //RAM( 16384 ~ 24575 )
    And(a=address[14] ,b=load ,out=al);
    Not(in=address[13] ,out=n13);
    And(a=al ,b=n13 ,out=R1);
    Screen(in=in ,load=R1 ,address=address[0..12] ,out=o1);
    
    //RAM( 24576 )
    Keyboard(out=o2);

    //輸出
    Mux16(a=o1 ,b=o2 ,sel=address[13] ,out=o12);
    Mux16(a=o0 ,b=o12 ,sel=address[14] ,out=out);
}
```

# Computer
```
CHIP Computer {

    IN reset;

    PARTS:
    // Put your code here:

    ROM32K(address=pc ,out=instruction); //輸出對應pc的指令
    
    CPU(inM=Mo ,instruction=instruction ,reset=reset ,outM=Mi ,writeM=writeM ,addressM=Adata ,pc=pc); //接收並執行指令

    Memory(in=Mi ,load=writeM ,address=Adata ,out=Mo); //輸出對應位置數據及接受CPU改動
}
```
