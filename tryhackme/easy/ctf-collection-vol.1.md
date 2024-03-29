# CTF collection Vol.1

{% embed url="https://tryhackme.com/room/ctfcollectionvol1" %}

##

## Task 2: What does the base said?

> Can you decode the following? VEhNe2p1NTdfZDNjMGQzXzdoM19iNDUzfQ==

### Feed me the flag!

* We can decode the flag using the `base64` utility.

```
$ echo "VEhNe2p1NTdfZDNjMGQzXzdoM19iNDUzfQ==" | base64 -d
THM{ju57_d3c0d3_7h3_b453} 
```

### Answer

```
THM{ju57_d3c0d3_7h3_b453} 
```

##

## Task 3: Meta meta

### I'm hungry, I need the flag.

* The name of the task hints us that the flag might be in the image metadata.
* We can extract this metadata using `exiftool`.

```
$ exiftool Findme.jpg                                    
ExifTool Version Number         : 12.44
File Name                       : Findme.jpg
Directory                       : .
File Size                       : 35 kB
File Modification Date/Time     : 2023:12:09 10:26:58+05:30
File Access Date/Time           : 2023:12:09 10:26:58+05:30
File Inode Change Date/Time     : 2023:12:09 10:27:26+05:30
File Permissions                : -rw-r--r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.01
X Resolution                    : 96
Y Resolution                    : 96
Exif Byte Order                 : Big-endian (Motorola, MM)
Resolution Unit                 : inches
Y Cb Cr Positioning             : Centered
Exif Version                    : 0231
Components Configuration        : Y, Cb, Cr, -
Flashpix Version                : 0100
Owner Name                      : THM{3x1f_0r_3x17}
Comment                         : CREATOR: gd-jpeg v1.0 (using IJG JPEG v62), quality = 60.
Image Width                     : 800
Image Height                    : 480
Encoding Process                : Progressive DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 800x480
Megapixels                      : 0.384
```

### Answer

```
THM{3x1f_0r_3x17}
```

##

## Task 4: Mon, are we going to be okay?

### It is sad. Feed me the flag.

* Sometimes other data or files can be hidden inside of JPG files.
* We can use `steghide` to extract these hidden files.

```
$ steghide extract -sf Extinction.jpg       
Enter passphrase: 
wrote extracted data to "Final_message.txt".
```

* Let's read the `Final_message.txt` file.

```
$ cat Final_message.txt 
It going to be over soon. Sleep my child.

THM{500n3r_0r_l473r_17_15_0ur_7urn}
```

### Answer

```
THM{500n3r_0r_l473r_17_15_0ur_7urn}
```

##

## Task 5: Erm......Magick

> Huh, where is the flag?

### Did you find the flag?

* If we just select the task string, we will see the flag.

<figure><img src="../../.gitbook/assets/1 (20).png" alt=""><figcaption></figcaption></figure>

### Answer

```
THM{wh173_fl46}
```

##

## Task 6: QRrrrr

### More flag please!

* The image we have is a QR code.
* In order to extract the flag, we can use the ZXing Decoder.&#x20;

<figure><img src="../../.gitbook/assets/2 (27).png" alt=""><figcaption></figcaption></figure>

### Answer

```
THM{qr_m4k3_l1f3_345y}
```

##

## Task 7: Reverse it or read it?

### Found the flag?

* For this challenge we are given an executable file.

```
$ file hello.hello      
hello.hello: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=02900338a56c3c8296f8ef7a8cf5df8699b18696, for GNU/Linux 3.2.0, not stripped
```

* We can check the strings inside the file using the `strings` command.

```
$ strings hello.hello                
/lib64/ld-linux-x86-64.so.2
libc.so.6
puts
printf
__cxa_finalize
__libc_start_main
GLIBC_2.2.5
_ITM_deregisterTMCloneTable
__gmon_start__
_ITM_registerTMCloneTable
u/UH
[]A\A]A^A_
THM{345y_f1nd_345y_60}
-- snip --;
```

### Answer

```
THM{345y_f1nd_345y_60}
```

##

## Task 8 Another decoding stuff

> Can you decode it? 3agrSy1CewF9v8ukcSkPSYm3oKUoByUpKG4L

### Oh, Oh, Did you get it?

* We can use the `Magic` function from CyberChef to decode the flag.

<figure><img src="../../.gitbook/assets/3 (29).png" alt=""><figcaption></figcaption></figure>

### Answer

```
THM{17_h45_l3553r_l3773r5}
```

##

## Task 9 Left or right

### Left, right, left, right... Rot 13 is too mainstream. Solve this MAF{atbe\_max\_vtxltk}

* Let's use the `Rot13` function with the amount set to `7`.

<figure><img src="../../.gitbook/assets/4 (25).png" alt=""><figcaption></figcaption></figure>

### Answer

```
THM{hail_the_caesar}
```

##

## Task 10: Make a comment

### I'm hungry now... I need the flag

* Let's inspect the page.&#x20;

<figure><img src="../../.gitbook/assets/5 (25).png" alt=""><figcaption></figcaption></figure>

### Answer

```
THM{4lw4y5_ch3ck_7h3_c0m3mn7}
```

##

## Task 11: Can you fix it?

### I accidentally messed up with this PNG file. Can you help me fix it? Thanks, ^^

* Let's check the hash dump of the PNG file.

```
$ xxd spoil.png | head
00000000: 2333 445f 0d0a 1a0a 0000 000d 4948 4452  #3D_........IHDR
00000010: 0000 0320 0000 0320 0806 0000 00db 7006  ... ... ......p.
00000020: 6800 0000 0173 5247 4200 aece 1ce9 0000  h....sRGB.......
00000030: 0009 7048 5973 0000 0ec4 0000 0ec4 0195  ..pHYs..........
00000040: 2b0e 1b00 0020 0049 4441 5478 9cec dd79  +.... .IDATx...y
00000050: 9c9c 559d eff1 cf79 9e5a bb7a 5f92 7477  ..U....y.Z.z_.tw
00000060: f640 4802 0920 1150 c420 bba2 88a8 805c  .@H.. .P. .....\
00000070: 1906 7c5d 64c0 79e9 752e 03ce 38e3 0e8e  ..|]d.y.u...8...
00000080: 2f75 e63a 23ea 8c0c e830 8e03 6470 c191  /u.:#....0..dp..
00000090: cd80 880c 4b20 0909 184c 42b6 4ed2 e9f4  ....K ...LB.N...
```

* So the first 4 characters are wrong. In a PNG file the first 4 characters should be `89 50 4E 47` as shown in this image:

<figure><img src="../../.gitbook/assets/8 (14).png" alt=""><figcaption></figcaption></figure>

* Let's use `hexedit` to fix the bytes.

```
$ hexedit spoil.png
```

<figure><img src="../../.gitbook/assets/6 (24).png" alt=""><figcaption></figcaption></figure>

* We should now be able to view the image.

<figure><img src="../../.gitbook/assets/7 (22).png" alt=""><figcaption></figcaption></figure>

```
THM{y35_w3_c4n}
```

##

## Task 12 Read it

### Did you found the hidden flag?

* For this question, we have to perform some Google dorking.
* Enter the following text in the search bar and click on the first link:

```
site:reddit.com/[r/tryhackme](https://www.reddit.com/r/tryhackme/) intext:THM{*}
```

<figure><img src="../../.gitbook/assets/8 (15).png" alt=""><figcaption></figcaption></figure>

### Answer

```
THM{50c14l_4cc0un7_15_p4r7_0f_051n7}
```

##

## Task 13: Spin my head

> What is this?++++++++++\[>+>+++>+++++++>++++++++++<<<<-]>>>++++++++++++++.------------.+++++.>+++++++++++++++++++++++.<<++++++++++++++++++.>>-------------------.---------.++++++++++++++.++++++++++++.<++++++++++++++++++.+++++++++.<+++.+.>----.>++++.

### Can you decode it?

* The text is encrypted using Brainfuck.
* We can decode it using an online decoder.&#x20;

<figure><img src="../../.gitbook/assets/9 (11).png" alt=""><figcaption></figcaption></figure>

### Answer

```
THM{0h_my_h34d}
```

##

## Task 14: An exclusive!

> Exclusive strings for everyone! S1: 44585d6b2368737c65252166234f20626d\
> S2: 1010101010101010101010101010101010

### Did you crack it? Feed me now!

* Since there are two strings, the possible decryption method is XOR.
* Let's use an online decoder.

<figure><img src="../../.gitbook/assets/10 (8).png" alt=""><figcaption></figcaption></figure>

### Answer

```
THM{3xclu51v3_0r}
```

##

## Task 15 Binary walk

### Flag! Flag! Flag!

* We have to extract the embedded files from the JPG file using `binwalk`.

```
$ binwalk -e hell.jpg 

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             JPEG image data, JFIF standard 1.02
30            0x1E            TIFF image data, big-endian, offset of first image directory: 8
265845        0x40E75         Zip archive data, at least v2.0 to extract, uncompressed size: 69, name: hello_there.txt
266099        0x40F73         End of Zip archive, footer length: 22
```

* We can now read the flag from the `hello.txt` file.

```
$ cat _hell.jpg.extracted/hello_there.txt 
Thank you for extracting me, you are the best!

THM{y0u_w4lk_m3_0u7}
```

### Answer

```
THM{y0u_w4lk_m3_0u7}
```

##

## Task 16 Darkness

### What does the flag said?

* We have to first download `stegsolve` for this task using the following command:

```
$ wget http://www.caesum.com/handbook/Stegsolve.jar -O stegsolve.jar
$ chmod +x stegsolve.jar
$ mkdir bin
$ mv stegsolve.jar bin/
```

* We have to now move the `dark.png` image to the `bin` folder that we crated.

```
$ mv dark.png bin 
```

* We are now ready to use `stegsolve`.

```
$ java -jar stegsolve.jar
Picked up _JAVA_OPTIONS: -Dawt.useSystemAAFontSettings=on -Dswing.aatext=true
```

* After opening the image using `stegsolve`, we have to go to `Blue plane 1` to be able to see the flag.

<figure><img src="../../.gitbook/assets/11 (3).png" alt=""><figcaption></figcaption></figure>

### Answer

```
THM{7h3r3_15_h0p3_1n_7h3_d4rkn355}
```

##

## Task 17: A sounding QR

> How good is your listening skill? P/S: The flag formatted as THM{Listened Flag}, the flag should be in All CAPS

### What does the bot said?

* Let's decode the `QRCTF.png` file using Zxing.

<figure><img src="../../.gitbook/assets/12.png" alt=""><figcaption></figcaption></figure>

* We are given a Soundcloud link as the result.
* Let's visit the link.&#x20;

<figure><img src="../../.gitbook/assets/13.png" alt=""><figcaption></figcaption></figure>

* The audio tells us that the flag is `soundingqr`.

### Answer

```
THM{SOUNDINGQR}
```

##

## Task 18: Dig up the past

> Sometimes we need a 'machine' to dig the past Targetted website: https://www.embeddedhacker.com/ Targetted time: 2 January 2020

* For this one we have to use the Wayback Machine.

<figure><img src="../../.gitbook/assets/14.png" alt=""><figcaption></figcaption></figure>

* Let's look at the snapshot created on January 2, 2020.&#x20;

<figure><img src="../../.gitbook/assets/15.png" alt=""><figcaption></figcaption></figure>

### Answer

```
THM{ch3ck_th3_h4ckb4ck}
```

##

## Task 19: Uncrackable!

> Can you solve the following? By the way, I lost the key. Sorry >.<\
> MYKAHODTQ{RVG\_YVGGK\_FAL\_WXF} Flag format: TRYHACKME{FLAG IN ALL CAP}

### The deciphered text

* In this task, we have to use the # Vigenère cipher.
* The key is `THM`.

<figure><img src="../../.gitbook/assets/16.png" alt=""><figcaption></figcaption></figure>

### Answer

```
TRYHACKME{YOU_FOUND_THE_KEY}
```

##

## Task 20: Small bases

> Decode the following text. 581695969015253365094191591547859387620042736036246486373595515576333693

### What is the flag?

* We simply have to convert it from Decimal to Hexadecimal to ASCIII.&#x20;

<figure><img src="../../.gitbook/assets/17.png" alt=""><figcaption></figcaption></figure>

#### Hexadecimal

```
54484D7B31375F6A7535375F346E5F307264316E3472795F62343533357D
```

<figure><img src="../../.gitbook/assets/18.png" alt=""><figcaption></figcaption></figure>

### Answer

```
THM{17_ju57_4n_0rd1n4ry_b4535}
```

##

## Task 21: Read the packet

### Did you captured my neighbor's flag?

* We have to open the PCAP using Wireshark and set the following filter:

```
tcp.stream == 42
```

* That filters for the HTTP packets.
* We can find the flag in packet `1827`.&#x20;

<figure><img src="../../.gitbook/assets/19.png" alt=""><figcaption></figcaption></figure>

### Answer

```
THM{d0_n07_574lk_m3}
```
