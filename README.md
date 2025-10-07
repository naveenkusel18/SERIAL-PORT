
# Serial Transfer of Single Byte / Character using 8051 (Keil)

## AIM
To write and execute an Embedded C Program for Serial Transfer of Single Byte / Character using 8051 in Keil.

## APPARATUS REQUIRED
- Personal Computer  
- Keil µVision Software  

## PROGRAM

### (i) Serial Port Transfer a Single Character

```
NAVEEN.A51

ORG 00H 
MOV TMOD, #20H 
MOV TH1, #0FDH 
MOV SCON, #50H 
SETB TR1 
MAIN_LOOP:
MOV SBUF, #'B' 
WAIT_TI:
JNB TI, WAIT_TI 
CLR TI 
END

NAVEEN.c

#include<reg51.h>
void main(void)
{
TMOD=0X20;
TH1=0XFA;
SCON=0X50;
TR1=1;
while(1)
{
SBUF='A';
while(T1==0);
T1=0;
}
}
```
### (ii) Serial Port to Transfer a Message

```
NAVEEN.C

#include<reg51.h>
void main(void)
{
unsigned char msg[]="NAVEEN K";
unsigned char i;
TMOD=0X20; //TIMER 1, MODE 2
TH1=0XFA;
SCON=0X50;
TR1=1;
for(i-0;i<=12;i++)
{
SBUF=msg[i];
while(TI==0);
TI=0;
}
while(1);
}

NAVEEN.A51

ORG 0000H
MOV TMOD, #20H
MOV TH1, #OFDH
MOV SCON, #50H
SETB TR1
MOV A ,#'T'
ACALL TRANS
MOV A ,#'A'
ACALL TRANS
MOV A, #'N'
ACALL TRANS
MOV A, #'U'
ACALL TRANS
MOV A , #'J'
ACALL TRANS
SJMP $
TRANS: MOV SBUF, A
WAIT: JNB T1, WAIT
CLR T1
RET
END
```

### OUTPUT:

(i) Serial Port Transfer a Single Character
<img width="940" height="230" alt="image" src="https://github.com/user-attachments/assets/9f9aadab-dcd6-41cd-bd71-3960db4297df" />

(ii) Serial Port to Transfer a Message
<img width="940" height="284" alt="image" src="https://github.com/user-attachments/assets/c072a5dc-bff9-484b-964d-9a91223ae952" />

### RESULT:

Thus the Serial transfer of Single Byte / Character using 8051 KEIL was done and shown the output.
