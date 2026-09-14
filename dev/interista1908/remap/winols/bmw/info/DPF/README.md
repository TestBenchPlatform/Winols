https://www.ecuconnections.com/forum/viewtopic.php?p=124601&hilit=F385F#p124601

Car is a July 2006 BMW E61 530D estate wagon with a ZF 6HP26 automatic transmission (rated up to 600Nm by ZF).

On to the maps!

Boost maps
Requested boost (16x16, 6 maps) D9E7A, EF8F2, EFB36, EFD7A, EFFBE, F1480
N75 (16x16, 7 maps) EE168, EE524, EE8E0, EEB24, EF158, EF39E, F0B42
Boost limiter (10x13) F01F0
SVBL F0402

Fuelling limiters
IQ limiter by throttle and speed(?) - one has no axes, the following one has axes that look like % and speed to me, 16x13 D4E22, 16x16 D5006
IQ limiter by EGT(?- no idea what the second axis could be) D5238
Atm pressure rail limiters (12x8, 8x8) F6696, F6E56
SOI limiter (16x16) F6B22
Rail pressure limiters (8x8, 5x6) F80BC, F81C6
RPL by RPM (5x1) F8C0E
RPL by fuel temp(?) (5x6) F8170
SVRL F8C22, F8CAE (probably just one of these?)

Fuelling maps
DW, DW in DS mode (8x14), these use inner torque, C3E98, C4010
NM to IQ (5 maps, 3 16x16, 16x20, 16x10) CA546, D8BBA, D8D46, D9222, D9466
Duration (24x16) EACA0
Rail pressure (2 maps, 16x16) F6F8C, F7A8A
Inner Torque (16x16, signed, negative values) D44A0
SOI (6 maps, 16x16) D9C36, DD60C, DD850, DDF1C, DE160, DE34A
Lambda (5 maps, one "main"? goes up to 1200mg/str) "main" D746C, rest D66D4, D6DA0, D6FE4, D7228
Regen Lambda (5 maps) D6918, D6B5C, D76B0, D78F4, D7B38
EGR (16x16) D99F2
Cranking IQ (10x8) F8F8E
Replacement value mass airflow (16x16) C4A50

DPF/EGR Switches and Hysteresis
EGR Hysteresis (34x1, all to 0 to disable according to what I found here) C8FB2
DPF Switches (8 bit, 1x1, 5x1) D1AE4, F385F

Torque limiters (lots and lots...)
External (gearbox) torque limiter (21x1) D42FE
Gearbox max torque? (14x1, tops out at 600Nm) C48AE - could be internal torque too, not sure
Another two max external torque maps? (25x1, 10x1, flat at 620Nm) DA8A6, DA8EE
...and another (10x1, flat at 400Nm) DAA14
Gear-dependent external TLs (10x1, 7 maps, 1-2-3-4-5-6-R) DA85E, DA918, DA942, DA96C, DA996, DA9C0, DA9EA
Internal TLs (21x1) D4AE8, D4B94, D4C14 - what do these control? The values are identical, but there's gotta be a reason for them..haven't found a damos/A2L to compare with yet.
Internal TLs (10x1, 21x1, 10x1) - limp mode/reverse? CAA92, D4B3E, D4BD4
TL by DPF backpressure (8x12) CAB36
TL by EGT (6x9) CAC60
Some sort of TL by EGT? (8x1, but values in percent?) F414C
TL by oil temp(?) + same for DS mode, (6x1, 2 maps) DA318, DA332
TL by IAT (5x6) EA680


Vmax-related (all these are just possibles!)
1x1 C0616, F6116, F9226
8x1 C3D10
15x1 F6066
3x3 F612C
2x1 F8D2A