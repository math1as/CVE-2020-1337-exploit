# CVE-2020-1337 Windows Privilege Escalation
this is a WWW(write-what-where) exploit 

## credit

Junyu Zhou (@md5_salt), who told me there could be a new bug.

Wenxu Wu (@ma7h1as), I find the bug and write this exploit.

## how it works
in the patch of CVE-2020-1048, Microsoft add the validation code of portname on XcvData function.

which could be triggered by call Add-Printer in Powershell.

now both AddPort and XcvData function would check if current user has access to portname.

but still, We could use junction to solve this problem, once the check is passed, we reparse it to a system folder. for example, C:\windows\system32

after reboot or service restart, user controlled data would be written into portname.

see exploit.ps1 for more details.
