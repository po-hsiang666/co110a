# AND 圖片都是自己畫的

```
/**
 * And gate: 
 * out = 1 if (a == 1 and b == 1)
 *       0 otherwise
 */

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
/**
 * Not gate:
 * out = not in
 */
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
 /**
 * Or gate:
 * out = 1 if (a == 1 or b == 1)
 *       0 otherwise
 */
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
/**
 * Exclusive-or gate:
 * out = not (a == b)
 */
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
/** 
 * Multiplexor:
 * out = a if sel == 0
 *       b otherwise
 */

CHIP Mux {
    IN a, b, sel;
    OUT out;

    PARTS:
    // Put your code here:
    Not(in=sel,out=notsel);
    And(a=a,b=notsel,out=out1);
    And(a=b,b=sel,out=out2);
    Or(a=out1,b=out2,out=out);
}
```

# DMUX
```
/**
 * Demultiplexor:
 * {a, b} = {in, 0} if sel == 0
 *          {0, in} if sel == 1
 */

CHIP DMux {
    IN in, sel;
    OUT a, b;

    PARTS:
    // Put your code here:
    Not(in=sel,out=notsel);
    And(a=in,b=notsel,out=a);
    And(a=in,b=sel,out=b);
}
```
![image](https://user-images.githubusercontent.com/81726807/149161968-8fc29214-b660-4bb3-af0c-185b8213a98f.png)

