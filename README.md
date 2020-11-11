![image](https://github.com/mytechnotalent/0x05_arm_32_hacking_char/blob/main/RPI32AAHC.png?raw=true)

# 0x05_arm_32_hacking_char
About ARM 32-bit Raspberry Pi Hacking Char example in Kali Linux.

## Schematic
![image](https://github.com/mytechnotalent/0x05_arm_32_hacking_char/blob/main/schematic.png?raw=true)

## Parts
[Raspberry Pi 4](https://www.adafruit.com/product/4292)<br>
[64GB Micro SD Card](https://www.amazon.com/SDSDQUA-064G-A11-Professional-MicroSDXC-formatted-recording/dp/106171327X)<br>
[Micro SD Card Reader/Writer](https://www.amazon.com/uni-Adapter-Supports-Compatible-MacBook/dp/B081VHSB2V)

## STEP 1: Download Kali Linux ARM Image - Raspberry Pi 32-bit
[Download](https://images.kali.org/arm-images/kali-linux-2020.3a-rpi3-nexmon.img.xz)

## STEP 2: Download balenaEtcher
[Download](https://www.balena.io/etcher)

## STEP 3: Flash Kali Linux ARM Image
[Watch YT Null Byte Video](https://www.youtube.com/watch?v=Jquf9BDm4iU&t=493s)

## STEP 4: Power Up RPI & Login
***POWER UP DEVICE AND LOGIN AS KALI AND SET UP SSH***

## STEP 5: Create File In VIM
```c
#include <stdio.h>

int main()
{
    char x;

    x = 'h';

    printf("%c\n", x);

    return 0;
}
```

## STEP 6: Save File As - 0x05_arm_32_hacking_chare.c [:wq]

## STEP 7: Build & Link
```
gcc -o 0x05_arm_32_hacking_char 0x04_arm_32_hacking_char.c
```

## STEP 8: Run Binary
```
./0x05_arm_32_hacking_char
h
```

## STEP 9: Run Radare2 - Debug Mode
```
r2 -d ./0x05_arm_32_hacking_char
```

## STEP 10: Run Radare2 - Debug Step 1 [Examine Binary @ Entry Point]
```
aaa
s main
vv
```
![image](https://github.com/mytechnotalent/0x05_arm_32_hacking_char/blob/main/1.png?raw=true)

## STEP 11: Run Radare2 - Debug Step 2 [Examine char]
```
q
[0x0044a50c]> pf x @0x0044a512
0x0044a512 = 0x71fb2368
```

## STEP 12: Run Radare2 - Debug Step 3 [Hack char]
```
[0x0044a50c]> wa mov r3, 0x69 @0x0044a512
```

## STEP 13: Run Radare2 - Debug Step 4 [Review Hack]
```
[0x0044a50c]> pf x @0x0044a512
0x0044a512 = 0x71fb2369
```

## STEP 14: Run Radare2 - Debug Step 5 [Hack Binary Permanently]
```
q
r2 -w ./0x05_arm_32_hacking_char
[0x00000400]> aaa
[0x00000400]> s main
[0x00000510]> vv
```
![image](https://github.com/mytechnotalent/0x05_arm_32_hacking_char/blob/main/2.png?raw=true)
```
q
[0x0000050c]> wa mov r3, 0x69 @0x00000512
```

## STEP 15: Prove Hack
```
./0x05_arm_32_hacking_char
i
```

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0)
