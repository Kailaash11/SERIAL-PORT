
# Serial Transfer of Single Byte / Character using 8051 (Keil)

## AIM
To write and execute an Embedded C Program for Serial Transfer of Single Byte / Character using 8051 in Keil.

## APPARATUS REQUIRED
- Personal Computer  
- Keil µVision Software  

## PROGRAM

### (i) Serial Port Transfer a Single Character

```
kailaash.A51

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

Kailaash.c

#include<reg51.h>
void main(void)
{
unsigned char msg[]="KAILAASH";
unsigned char i;
TMOD=0X20; 
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


```
### (ii) Serial Port to Transfer a Message

```
kailaash.A51

ORG 00H 
START:
 MOV TMOD, #20H 
 MOV TH1, #0FAH 
 MOV SCON, #50H 
 SETB TR1 
 MOV DPTR, #4500H 
 SEND_MESSAGE: MOVX A, @DPTR 
  MOV SBUF, A 
 WAIT_TI:
 JNB TI, WAIT_TI 
 CLR TI 
 INC DPTR 
 SJMP SEND_MESSAGE 
 L1:SJMP L1


kailaash.c

#include<reg51.h>
void main(void)
{
unsigned char msg[]="Embedded LAB";
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



```

### OUTPUT:
![WhatsApp Image 2025-10-08 at 08 58 37_8540c97d](https://github.com/user-attachments/assets/37666b66-0493-44d2-aa69-909d1f5dd128)

![WhatsApp Image 2025-10-08 at 09 15 12_58bf6bcf](https://github.com/user-attachments/assets/4494976e-366a-477f-bec2-3425222654cf)

### RESULT:
Thus the Serial transfer of Single Byte / Character using 8051 KEIL was done and shown the output.
