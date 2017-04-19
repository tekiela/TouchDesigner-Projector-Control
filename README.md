# TouchDesigner-Projector-Control

TouchDesigner099 component that provides projector control via the RS-232 serial port. Controls are limited to a couple that are useful in a real-time environment, and some extra room to add messages that you could find useful for your project.

## Build and Version
This tool was created on Windows, and is stable in 64-bit, build 5040.

## Installation
Add the ```nVoid_TouchDesigner_Projector_Control.tox``` component anywhere in your project.

## Setup (Windows)
- Make sure the computer and projector are turned off
- Connect the RS232 cable to the computer and projector
- Turn on computer and go to *Device Manager* to find out what Comm port the RS232 cable is connected to

### Tox setup
- Make sure settings are correct on the custom parameters *Setup* page
- Baud Rate, Data Bits, and Stop Bits settings will be outlined in the projector models RS232 commands manual

## Usage
Commands and settings differ from brand to brand, and even between models. But each model, series, or brand will outline the commands in either their product manual, or a seperate RS232 command manual.

The messages outlined in the manuals are usually ASCII, Hexadecimal, or they may provide both. In this system, hex is the most reliable since there is only one code per character, whereas ASCII could have different ways of expressing an escape character.
For example, Benq has ASCII messages in their manual, and '<CR>' their syntax for a carriage return, while TouchDesigner uses '\r'. In Hexadecimal, it is simply '0D', with no other alternatives. ASCII messages with escape sequences such as <CR> or [CR] are converted automatically.

Operation is simple, enter the command into the appropriate text box, and to trigger it just hit the corresponding pulse button.

## Examples

### NEC NP600S
Baud Rate = 19200

Data Bits = 8

Stop Bits = 1

Message Type = HEX

On Message = 02 00 00 00 00 02
Off Message = 02 01 00 00 00 03
Picture Mute On = 02 10 00 00 00 12
Picture Mute Off = 02 11 00 00 00 13

### BENQ MX819ST
Baud Rate = 115200
Data Bits = 8
Stop Bits = 1
Message Type = ASCII

On Message = <CR>*pow=on#<CR>
Off Message = <CR>*pow=off#<CR>
Picture Mute On = <CR>*blank=on#<CR>
Picture Mute Off = <CR>*blank=off#<CR>

### OPTOMA DS550
Baud Rate = 9600
Data Bits = 8
Stop Bits = 1
Message Type = HEX

On Message = 7E 30 30 30 30 20 31
Off Message = 7E 30 30 30 30 20 32
Picture Mute On = 7E 30 30 30 32 20 31
Picture Mute Off = 7E 30 30 30 32 20 32
