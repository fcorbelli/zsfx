# zsfx
### ZPAQ/[zpaqfranz](https://github.com/fcorbelli/zpaqfranz)   SFX module for Windows (32/64) 
zsfx.exe (and zsfx32.exe) create self-extracting Windows executables from ZPAQ or [zpaqfranz archives](https://github.com/fcorbelli/zpaqfranz)  
Supports just about everything: 
- journaling
- multithread
- command switches (-only, -to...)
- non-Latin charsets
- fast, really fast
- easy to use (no weird "voodoo" needed)
- the 32 bit version (zsfx32.exe) can extract limitless archives (just not as fast as the 64 bit)

The software is not very small (~300KB) and the resulting EXE must be less than 2GB in size (Windows limitation).  

[The archaic (2012) ZPAQ sfx module](http://mattmahoney.net/dc/zpaqutil.html)  

_Note: if you use something like UPX or whatever heuristic-fake virus detection is common. It is not my fault :)_

The usage is trivial
```
Usage:   zsfx x nameofzpaqfile (...zpaq extraction options) (-output mynewsfx.exe)

Ex: zsfx x z:\1.zpaq
Ex: zsfx x z:\1.zpaq -to .\xtracted\
Ex: zsfx x z:\1.zpaq -to y:\testme\ -output z:\mynewsfx.exe
```
_Do NOT call the output file zsfx.exe or zsfx32.exe_  
_Do NOT rename zsfx.exe and zsfx32.exe to something else_

**CREDITS**  

- [Matt Mahoney (of course)](http://mattmahoney.net/)
- SeDD user of the encode.ru forum
- This user (https://github.com/dertuxmalwieder)

# How to build
In this case only Windows is supported, be careful to link the pthread library.  
Today it is splitted into 3 source code, not merged as zpaqfranz, because no "strange" platform here, just plain Win.  

Targets
```
Targets
Windows 64 (g++ 7.3.0)
g++ -O3 zsfx.cpp libzpaq.cpp -o zsfx -static

(more aggressive) 10.3.0 beware of -flto
g++ -Os zsfx.cpp libzpaq.cpp -o zsfx -static -fno-rtti -Wl,--gc-sections -fdata-sections -flto

Windows 32 (g++ 7.3.0)
c:\mingw32\bin\g++ -m32 -O3  zsfx.cpp libzpaq.cpp -o zsfx32 -pthread -static

(more aggressive) 10.3.0 -flto
c:\mingw32\bin\g++ -m32 -Os  zsfx.cpp libzpaq.cpp -o zsfx32 -pthread -static -fno-rtti  -Wl,--gc-sections -flto

```
