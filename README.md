# to-generate-a-2-second-delay-using-Timer-0-in-Mode-1-and-blink-an-LED-connected-to-Port-3.7.
## Aim
To write an assembly language program in 8051 microcontroller to generate a 2-second delay using Timer 0 in Mode 1 and blink an LED connected to Port 3.7.
## Apparatus
1.8051 Microcontroller Kit (or emulator such as Keil µVision)

2.LED connected to Port 3.7

3.Power supply

4.Jumper wires
## Aalgorithm 
1.Start the program.

2.Configure Port 3.7 as output (for LED).

3.Initialize Timer 0 in Mode 1 (16-bit mode).

4.Load timer registers TH0 and TL0 with initial values for 65.536 ms delay.

5.Start the timer.

6.Wait for TF0 flag to set (overflow).

7.Clear TF0 flag and reload timer values.

8.Repeat overflow counting 31 times to get approximately 2 seconds.

9.Toggle LED (P3.7).

10.Repeat the process infinitely.

## Program
```
ORG 0000H

MAIN:   MOV TMOD, #01H        
        SETB P3.7            

AGAIN:  ACALL DELAY_2S       
        SJMP AGAIN            

DELAY_2S:
        MOV R2, #31           

DELAY_LOOP:
        MOV TH0, #00H         
        MOV TL0, #00H         
        SETB TR0              

WAIT_OV:
        JNB TF0, WAIT_OV     

        CLR TR0              
        CLR TF0               
        DJNZ R2, DELAY_LOOP

        RET

END
```
## output
![WhatsApp Image 2025-11-05 at 15 27 18_767f82aa](https://github.com/user-attachments/assets/ef6caf24-0480-4099-8f04-27359b05bcdf)
![WhatsApp Image 2025-11-05 at 15 25 18_f00e53c7](https://github.com/user-attachments/assets/5072a767-02fd-437d-9bc1-0a188c7ea742)
## reslut
The assembly program was successfully executed.
The LED connected to Port 3.7 blinks continuously with a 2-second delay between ON and OFF states.

