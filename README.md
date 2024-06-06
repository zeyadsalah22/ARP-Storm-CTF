# ARP Storm

## Discovering abnormalities

The first thing we can do when we open the PCAP is to search for any abnormalities in it, if we take a look at the image below we can notice something strange, we know that the opcode can only be 0 or 1 referring to request and reply operations but in the PCAP we find that the opcode is strange it is always Unknown ARP opcode 0x…. , so from here we can start to check the abnormality we found.

[![ARP STORM 1](https://github.com/zeyadsalah22/LAN-Chat-using-Python-socket/blob/main/images/lanchat1.png)](https://github.com/zeyadsalah22/LAN-Chat-using-Python-socket/blob/main/images/lanchat1.png)

## Searching for the way to the flag

After we found that unusual thing, we can check all the abnormal opcodes to determine a pattern or something, after doing that we discover that they all have the same representation except for the character in the middle which change for each opcode as shown in the image below, so if we can get all those characters from the opcodes may be we can get the flag or encoded version of it.

[![LAN Chat 1](https://github.com/zeyadsalah22/LAN-Chat-using-Python-socket/blob/main/images/lanchat1.png)](https://github.com/zeyadsalah22/LAN-Chat-using-Python-socket/blob/main/images/lanchat1.png)


## First step to get the flag

An easy way to get that character from each opcode rather than copying and pasting each one is to use tshark in command prompt to find the sequence of those characters, if we run the following command: tshark.exe -r C:\\Users\\Lenovo\\Downloads\\ARP+Storm.pcap -T fields -e arp.opcode , we will get the decimal representation for each character as shown in the image below.



## Second step to get the flag

Now we want to convert from the decimal representation of each character to its actual value using ascii code, we can do that by running a python code to do that job for us. Here is the code snippet:



Then the output of that code will be our encoded flag which is: ZmxhZ3tnckB0dWl0MHVzXzBwY09kZV8xc19BbHdAeXNfQTZ1U2VkX3QwX3AwMXMwbn0

 ## Final step to get the flag

It is common that if the flag is encoded and it ends by ‘=’, then that means that it is encoded by base 64, We can also run python code to decode that flag which is the following:



After that we will get our desired flag and the answer of our problem which is:

flag{gr@tuit0us_0pcOde_1s_Alw@ys_A6uSed_t0_p01s0n}
