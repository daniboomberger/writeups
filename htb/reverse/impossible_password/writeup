#Impossible Password Challenge
The Challenge was provided in the HackTheBox [https://www.hackthebox.eu/home/challenges/Reversing] by Decoder.
Follwing Tutorial to solve the Problem are just an example so there are other possible ways to solve the Challenge.
The Screenshot were made on an kali linux machine.

- So basically I downloaded the Zip file of the Challenge from HackTheBox
- In the next step I used the commend `unzip -q impossible_password.zip`, the addition `-q` is for password protected zip compressed folder
- Afterwards you unzip the downloaded folder you will get a file called `impossible_password.bin`
- I used Radare2 to disassembly the binary executable. I ran the command `r2 -A impossible_password.bin`
- In the Radare2 you will need to move to the main function with this command `pdf@main`
- It will show you the main function of the binary file
```
            ; DATA XREF from entry0 @ 0x4006bd
┌ 283: int main (int argc, char **argv);
│           ; var int64_t var_50h @ rbp-0x50
│           ; var int64_t var_44h @ rbp-0x44
│           ; var int64_t var_40h @ rbp-0x40
│           ; var int64_t var_3fh @ rbp-0x3f
│           ; var int64_t var_3eh @ rbp-0x3e
│           ; var int64_t var_3dh @ rbp-0x3d
│           ; var int64_t var_3ch @ rbp-0x3c
│           ; var int64_t var_3bh @ rbp-0x3b
│           ; var int64_t var_3ah @ rbp-0x3a
│           ; var int64_t var_39h @ rbp-0x39
│           ; var int64_t var_38h @ rbp-0x38
│           ; var int64_t var_37h @ rbp-0x37
│           ; var int64_t var_36h @ rbp-0x36
│           ; var int64_t var_35h @ rbp-0x35
│           ; var int64_t var_34h @ rbp-0x34
│           ; var int64_t var_33h @ rbp-0x33
│           ; var int64_t var_32h @ rbp-0x32
│           ; var int64_t var_31h @ rbp-0x31
│           ; var int64_t var_30h @ rbp-0x30
│           ; var int64_t var_2fh @ rbp-0x2f
│           ; var int64_t var_2eh @ rbp-0x2e
│           ; var int64_t var_2dh @ rbp-0x2d
│           ; var int64_t var_20h @ rbp-0x20
│           ; var int64_t var_ch @ rbp-0xc
│           ; var int64_t var_8h @ rbp-0x8
│           ; arg int argc @ rdi
│           ; arg char **argv @ rsi
│           0x0040085d      55             push rbp
│           0x0040085e      4889e5         mov rbp, rsp
│           0x00400861      4883ec50       sub rsp, 0x50
│           0x00400865      897dbc         mov dword [var_44h], edi    ; argc
│           0x00400868      488975b0       mov qword [var_50h], rsi    ; argv
│           0x0040086c      48c745f8700a.  mov qword [var_8h], str.SuperSeKretKey ; 0x400a70 ; "SuperSeKretKey"
│           0x00400874      c645c041       mov byte [var_40h], 0x41    ; 'A' ; 65
│           0x00400878      c645c15d       mov byte [var_3fh], 0x5d    ; ']' ; 93
│           0x0040087c      c645c24b       mov byte [var_3eh], 0x4b    ; 'K' ; 75
│           0x00400880      c645c372       mov byte [var_3dh], 0x72    ; 'r' ; 114
│           0x00400884      c645c43d       mov byte [var_3ch], 0x3d    ; '=' ; 61
│           0x00400888      c645c539       mov byte [var_3bh], 0x39    ; '9' ; 57
│           0x0040088c      c645c66b       mov byte [var_3ah], 0x6b    ; 'k' ; 107
│           0x00400890      c645c730       mov byte [var_39h], 0x30    ; '0' ; 48
│           0x00400894      c645c83d       mov byte [var_38h], 0x3d    ; '=' ; 61
│           0x00400898      c645c930       mov byte [var_37h], 0x30    ; '0' ; 48
│           0x0040089c      c645ca6f       mov byte [var_36h], 0x6f    ; 'o' ; 111
│           0x004008a0      c645cb30       mov byte [var_35h], 0x30    ; '0' ; 48
│           0x004008a4      c645cc3b       mov byte [var_34h], 0x3b    ; ';' ; 59
│           0x004008a8      c645cd6b       mov byte [var_33h], 0x6b    ; 'k' ; 107
│           0x004008ac      c645ce31       mov byte [var_32h], 0x31    ; '1' ; 49
│           0x004008b0      c645cf3f       mov byte [var_31h], 0x3f    ; '?' ; 63
│           0x004008b4      c645d06b       mov byte [var_30h], 0x6b    ; 'k' ; 107
│           0x004008b8      c645d138       mov byte [var_2fh], 0x38    ; '8' ; 56
│           0x004008bc      c645d231       mov byte [var_2eh], 0x31    ; '1' ; 49
│           0x004008c0      c645d374       mov byte [var_2dh], 0x74    ; 't' ; 116
│           0x004008c4      bf7f0a4000     mov edi, 0x400a7f           ; const char *format
│           0x004008c9      b800000000     mov eax, 0
│           0x004008ce      e82dfdffff     call sym.imp.printf         ; int printf(const char *format)
│           0x004008d3      488d45e0       lea rax, qword [var_20h]
│           0x004008d7      4889c6         mov rsi, rax
│           0x004008da      bf820a4000     mov edi, str.20s            ; 0x400a82 ; "%20s" ; const char *format
│           0x004008df      b800000000     mov eax, 0
│           0x004008e4      e887fdffff     call sym.imp.__isoc99_scanf ; int scanf(const char *format)
│           0x004008e9      488d45e0       lea rax, qword [var_20h]
│           0x004008ed      4889c6         mov rsi, rax
│           0x004008f0      bf870a4000     mov edi, str.s              ; 0x400a87 ; "[%s]\n" ; const char *format
│           0x004008f5      b800000000     mov eax, 0
│           0x004008fa      e801fdffff     call sym.imp.printf         ; int printf(const char *format)
│           0x004008ff      488b55f8       mov rdx, qword [var_8h]
│           0x00400903      488d45e0       lea rax, qword [var_20h]
│           0x00400907      4889d6         mov rsi, rdx                ; const char *s2
│           0x0040090a      4889c7         mov rdi, rax                ; const char *s1
│           0x0040090d      e81efdffff     call sym.imp.strcmp         ; int strcmp(const char *s1, const char *s2)
│           0x00400912      8945f4         mov dword [var_ch], eax
│           0x00400915      837df400       cmp dword [var_ch], 0
│       ┌─< 0x00400919      740a           je 0x400925
│       │   0x0040091b      bf01000000     mov edi, 1                  ; int status
│       │   0x00400920      e85bfdffff     call sym.imp.exit           ; void exit(int status)
│       │   ; CODE XREF from main @ 0x400919
│       └─> 0x00400925      bf8d0a4000     mov edi, 0x400a8d           ; const char *format
│           0x0040092a      b800000000     mov eax, 0
│           0x0040092f      e8ccfcffff     call sym.imp.printf         ; int printf(const char *format)
│           0x00400934      488d45e0       lea rax, qword [var_20h]
│           0x00400938      4889c6         mov rsi, rax
│           0x0040093b      bf820a4000     mov edi, str.20s            ; 0x400a82 ; "%20s" ; const char *format
│           0x00400940      b800000000     mov eax, 0
│           0x00400945      e826fdffff     call sym.imp.__isoc99_scanf ; int scanf(const char *format)
│           0x0040094a      bf14000000     mov edi, 0x14               ; 20 ; size_t arg1
│           0x0040094f      e839feffff     call fcn.0040078d
│           0x00400954      4889c2         mov rdx, rax
│           0x00400957      488d45e0       lea rax, qword [var_20h]
│           0x0040095b      4889d6         mov rsi, rdx                ; const char *s2
│           0x0040095e      4889c7         mov rdi, rax                ; const char *s1
│           0x00400961      e8cafcffff     call sym.imp.strcmp         ; int strcmp(const char *s1, const char *s2)
│           0x00400966      85c0           test eax, eax
│       ┌─< 0x00400968      750c           jne 0x400976
│       │   0x0040096a      488d45c0       lea rax, qword [var_40h]
│       │   0x0040096e      4889c7         mov rdi, rax                ; int64_t arg1
│       │   0x00400971      e802000000     call fcn.00400978
│       │   ; CODE XREF from main @ 0x400968
│       └─> 0x00400976      c9             leave
└           0x00400977      c3             ret

```
- The main function will give you actually a lot of hints for the whole running process of the binary file
- Initially to that I opend up a new Terminal window and try to run the binary file
- The first command I used was `chmod 755 impossible_password.bin` which basically gives me the rights to execute the file
- So afterwards I ran the file with `./impossible_password.bin` and the output of the file was the following character '*'
- In the main function the output run by the first printf function `0x004008ce      e82dfdffff     call sym.imp.printf         ; int printf(const char *format)`
- The next major function which is called, is the scanf function `x004008e4      e887fdffff     call sym.imp.__isoc99_scanf ; int scanf(const char *format)`
- After we input an string in the binary file the next function called is an print of our string
- strcmp is the next important function which is called to understand what happens when the strcmp isn't true
- When the string comparison is not true it will exit `0x00400920      e85bfdffff     call sym.imp.exit           ; void exit(int status)`
. If the comparison is true it will jump over the exit function and will provide us with another printf function
- As we run the binary file as an test we see that if we input after this character `*` another string it will print it but the first strcmp is still false
- So we try this provided string we saw in the main function `SuperSeKretKey` and put it after `*` and it works and shows us this following string `**`
- When we look further into the main  function we see there is the printf which provides us with the string `0x0040092f      e8ccfcffff     call sym.imp.printf         ; int printf(const char *format)`
- Also there is another scanf which seems to be just another input we have to give
- And there is an strcmp called which doesn't lead us into an exit function if we are wrong
- But in some of the last lines of the code we see this call `0x00400968      750c           jne 0x400976`, which actually jumps as to the end of the binary file
- Basically it never runs trough this function called after that jump `0x00400971      e802000000     call fcn.00400978`
- So we need to edit the main function with Radare2 as we write in Radare2 `oo+`, which makes it an editable binary file and then we enter Visual Mode with `V`
- And to change the view of the Visual Mode we press `p` afterwards we look up where we need to change our binary file and press `c` to edit it
- With insert we provide this `9090` which makes this line `0x00400968      750c           jne 0x400976` to an nop line which actually doesn't interfere our binary file
- Afterwards we close our fully changed binary and run it again, after we reach `**` we just provide an input and it will show us the htb{flag}
