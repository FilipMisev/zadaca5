# zadaca5
Микропроцесорски систем базиран на 8085 служи за контрола на температура. Контролата се врши секоја 0.5 s. Доколку прочитаната температура е во интервалот помеѓу две гранични температури, сместени на врвот на стекот, се пали зелена сијаличка, а обратно се пали црвена сијаличка и се запира работата на процесорот. Температурата доаѓа по прекидна секвенца.

 ![Screenshot (1)](  https://github.com/TrajceStudent/zadaca5/blob/main/123.png  )

3Ch: DCR B
RET 
MVI A, 11010011b ; 19, 5000/256=19 и ост 136 поворка кратки имплуси
OUT THB
MVI A, 10001000b ; 136
OUT TLB
MVI A,11XXXXXXb ; се стартува тајмерот
OUT CSR
INIT: MVI B,250d
PAK:MOV A,B
 ANI FFh THB EQU 00001 101
 JNZ PAK TLB EQU 00001 100
 POP D CSR EQU 00001 000
IN 01h
 CMP D
 JC STOP
 CMP E
 JNC STOP
 MVI A,11XXXXXXb
 SIM 
JMP INIT
STOP: MVI A,01XXXXXXb
 SIM
 HLT
 END 
