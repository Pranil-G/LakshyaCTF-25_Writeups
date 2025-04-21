# Hello World

## Description
Jaisa dikhta hai waisa hota hai nahi.

Ek compiled binary diya gaya hai jisme ek certain string form mein memory mein embedded hai—lekin direct-readable format mein nahi. Program khud ek standard output call use karta hai jo is constant ko runtime pe reveal karta hai.

Dekhte hain aap kitne ache se binary ki antar-atma tak pahunch paate ho. Bas dhyaan rahe: kuch cheezein encoded mein chipki hui hain, aur shabd kuch aise hain jo turant samajh nahi aayenge... unless you know where to look

# Solve

I opened the binary in Ghidra and began exploring the disassembled code. As expected, there were several functions of interest, but one in particular stood out: _hiddenflag. This function wasn’t called directly in main(), but it clearly held the logic for constructing the output string.

```
                             _hiddenFlag
        00401475 55              PUSH       EBP
        00401476 89  e5           MOV        EBP ,ESP
        00401478 83  ec  38       SUB        ESP ,0x38
        0040147b c6  45  db  4c    MOV        byte ptr [EBP  + -0x25 ],0x4c
        0040147f c6  45  dc  61    MOV        byte ptr [EBP  + -0x24 ],0x61
        00401483 c6  45  dd  6b    MOV        byte ptr [EBP  + -0x23 ],0x6b
        00401487 c6  45  de  73    MOV        byte ptr [EBP  + -0x22 ],0x73
        0040148b c6  45  df  68    MOV        byte ptr [EBP  + -0x21 ],0x68
        0040148f c6  45  e0  79    MOV        byte ptr [EBP  + -0x20 ],0x79
        00401493 c6  45  e1  61    MOV        byte ptr [EBP  + -0x1f ],0x61
        00401497 c6  45  e2  43    MOV        byte ptr [EBP  + -0x1e ],0x43
        0040149b c6  45  e3  54    MOV        byte ptr [EBP  + -0x1d ],0x54
        0040149f c6  45  e4  46    MOV        byte ptr [EBP  + -0x1c ],0x46
        004014a3 c6  45  e5  7b    MOV        byte ptr [EBP  + -0x1b ],0x7b
        004014a7 c6  45  e6  68    MOV        byte ptr [EBP  + -0x1a ],0x68
        004014ab c6  45  e7  69    MOV        byte ptr [EBP  + -0x19 ],0x69
        004014af c6  45  e8  64    MOV        byte ptr [EBP  + -0x18 ],0x64
        004014b3 c6  45  e9  64    MOV        byte ptr [EBP  + -0x17 ],0x64
        004014b7 c6  45  ea  65    MOV        byte ptr [EBP  + -0x16 ],0x65
        004014bb c6  45  eb  6e    MOV        byte ptr [EBP  + -0x15 ],0x6e
        004014bf c6  45  ec  5f    MOV        byte ptr [EBP  + -0x14 ],0x5f
        004014c3 c6  45  ed  66    MOV        byte ptr [EBP  + -0x13 ],0x66
        004014c7 c6  45  ee  6c    MOV        byte ptr [EBP  + -0x12 ],0x6c
        004014cb c6  45  ef  61    MOV        byte ptr [EBP  + -0x11 ],0x61
        004014cf c6  45  f0  67    MOV        byte ptr [EBP  + -0x10 ],0x67
        004014d3 c6  45  f1  5f    MOV        byte ptr [EBP  + -0xf ],0x5f
        004014d7 c6  45  f2  68    MOV        byte ptr [EBP  + -0xe ],0x68
        004014db c6  45  f3  65    MOV        byte ptr [EBP  + -0xd ],0x65
        004014df c6  45  f4  72    MOV        byte ptr [EBP  + -0xc ],0x72
        004014e3 c6  45  f5  65    MOV        byte ptr [EBP  + -0xb ],0x65
        004014e7 c6  45  f6  7d    MOV        byte ptr [EBP  + -0xa ],0x7d
        004014eb c6  45  f7  00    MOV        byte ptr [EBP  + -0x9 ],0x0
        004014ef 8d  45  db       LEA        EAX ,[EBP  + -0x25 ]
        004014f2 89  44  24  04    MOV        dword ptr [ESP  + 0x4 ],EAX
        004014f6 c7  04  24       MOV        dword ptr [ESP ],s_Flag:_%s_00405072             = "Flag: %s\n"
                 72  50  40  00
```

decoding this gave the flag.

Flag - `LakshyaCTF{hidden_flag_here}`
