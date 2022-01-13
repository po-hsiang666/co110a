# AND 圖片都是自己畫的

```
CHIP And {
    IN a, b;
    OUT out;

    PARTS:
    // Put your code here:
    Nand(a=a,b=b,out=AnandB);
    Not(in=AnandB,out=out);

}
```

# NOT
```
CHIP Not {
    IN in;
    OUT out;

    PARTS:
    // Put your code here:
    Nand(a=in, b=in, out=out);
}
```

# OR
```
CHIP Or {
    IN a, b;
    OUT out;

    PARTS:
    // Put your code here:
    Not(in=a,out=na);
    Not(in=b,out=nb);
    Nand(a=na,b=nb,out=out);

}
```

# XOR
```
CHIP Xor {
    IN a, b;
    OUT out;

    PARTS:
    // Put your code here:
    Not(in=a, out=na);
    Not(in=b, out=nb);
    And(a=a, b=nb ,out=c);
    And(a=na, b=b, out=d);
    Or(a=c, b=d, out=out); 
}
```

# MUX
```
CHIP Mux {
    IN a, b, sel;
    OUT out;

    PARTS:
    // Put your code here:
    Not(in=sel, out=nsel);
    And(a=a,b=nsel,out=c);
    And(a=b,b=sel,out=d);
    Or(a=c,b=d,out=out);
}
```

# DMUX
```
CHIP DMux {
    IN in, sel;
    OUT a, b;

    PARTS:
    // Put your code here:
    Not(in=sel,out=nsel);
    And(a=in, b=nsel, out=a);
    And(a=in, b=sel, out=b);
}
```
![image](https://user-images.githubusercontent.com/81726807/149161968-8fc29214-b660-4bb3-af0c-185b8213a98f.png)

