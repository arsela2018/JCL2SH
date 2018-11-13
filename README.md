# JCL2SH
Convert JCL to SHELL
the files extracted from zip I copied in a MAC laptop with OS LINUX.
Was necesary eliminate the option xplink from compilation line in build.sh. The option xplink is just for  optimization
The compilation in one MAC OS LINUX send warnings messages that its "ok"...
But when execute the example to convert JCL to SHELL the result is not the planned with a simple JCL, just one step: 
1. //STEP0001  JOB 'REXX EX',REGION=0M,CLASS=A,MSGCLASS=7,
2. //          NOTIFY=$SYSUID,MSGLEVEL=(1,1)
3. //*********************************************************
4. //*********************************************************
5. //* SEND RECORD PROCESS
6. //*********************************************************
7. //*********************************************************
8. //EXREXX EXEC PGM=IKJEFT01,DYNAMNBR=20
9. //SYSTSPRT DD SYSOUT=*
10 //SYSPRINT DD SYSOUT=*
 
Result 9 lines numbered from 1 to 9 with the text: 
1. Stmt 000000001 JOB  Lines: 02 Ptr:0x7fe1dbe00080
2. Stmt 000000001  //* Lines: 01 Ptr:0x7fe1dbe004c0
3. Stmt 000000001  //* Lines: 01 Ptr:0x7fe1dbe005d0
4. Stmt 000000001  //* Lines: 01 Ptr:0x7fe1dbe006e0
5. Stmt 000000001  //* Lines: 01 Ptr:0x7fe1dbe00810
6. Stmt 000000001  //* Lines: 01 Ptr:0x7fe1dbe00940
7. Stmt 000000001 EXEC Lines: 01 Ptr:0x7fe1dbe00a70
8. Stmt 000000001   DD Lines: 01 Ptr:0x7fe1dbe00c50
9. Stmt 000000001   DD Lines: 01 Ptr:0x7fe1dbe00da0

Any idea about how to solve this...? Mike?, any suggestion?

In other way, the programs downloded using the version from desk in github are not well, neither. When I make the upload, from my laptop, with windows 10, using the IND$FILE PUT... , option 6 of ISPF menu, to TSO in my Hercules,... the map codepage is wrong,... First, the files downloaded from github, are in ascii code, this is LF at the end of each record; and the options to upload, can use the conversion option: ASCII TO EBCDIC and CRLR, so  it was necesary, previously, convert from UNIX to Windows, the modules. To do this,  I used NOTEPAD++, to change LR to CRLF, this software is free and useful. Later when make the upload, the characters like "square parhentesis", and the character (!),  are converted to x'ba', x'bb', x'5a' that must be changed in TSO to x'ad' and x'bd', and in the case of x'5a' this character is recognizer as negation but is not uniform,...it was necesary to make the conversion step by step to verify and confirm the conversion... so was necesary to edit each module and change the code to EBCDIC 1147, that is well recognized by the C compiler in OMVS, UNIX ZOS, option 10 in ISPF menu.
At the end the C compilation is failing with: 
CCN3046 Syntax error.
in line 707 KeyValuePair_T* kvp = cur->kvphead; of program scanjcl.c  
I am looking for some solution to this error ...
As you can see, I am working in two scenarios: one in MAC with LINUX and the other in UNIX ZOS in HERCULES emulator
... both of them have ERRORS.
Please, if you have a suggestion or one good idea to solve the CCN3046 ERROR in Hercules or to fix the "bad" result in LINUX, let me know it! thanks a lot for your help!
