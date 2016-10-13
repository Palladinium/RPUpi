# Check DTR

## Overview

This firmware is used to test the DTR connections, do not use it with a node board, or a Pi Zero installed.

``` 
delay 4000
set DTR_TXD LOW so U4 DI input has 0V.
set DTR_DE HIGH to drive DTR pair, so R12 has 3.3V.
set DTR_nRE LOW cause U4 to copy DTR pair to RO output
blink 1
test DTR_RXD == LOW
delay 1000
set DTR_TXD HIGH which should cause an undriven pair
blink 2
test DTR_RXD == HIGH
delay 1000
set DTR_DE LOW
set DTR_nRE HIGH to disconned RO so R10 pulls up DTR_RXD
set DTR_TXD LOW to drive pair low
blink 3
test DTR_RXD == HIGH
delay 1000
set DTR_DE  HIGH connect DI from DTR pair.
blink 4
test DTR_RXD == HIGH
loop
``` 

Toolchain setup http://epccs.org/indexes/Document/DvlpNotes/LinuxBoxCrossCompiler.html


