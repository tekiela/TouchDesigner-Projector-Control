# TouchDesigner-Projector-Control

TouchDesigner099 component that provides projector control via the RS-232 serial port. Controls are limited to a couple that are useful in a real-time environment, and some extra room to add messages that you could find useful for your project.

## Build and Version
This tool was created on Windows and is stable in TouchDesigner 099 64-bit build 5040.

## Installation
Add the ```nVoid_TouchDesigner_Projector_Control.tox``` component anywhere in your project.

## Setup
- Make sure the computer and projector are turned off
- Connect the RS232 cable to the computer and projector (we used a cheap RS232 to USB cable)
- Turn on computer and go to *Device Manager*, under the *Ports* section, find your serial device and you will see the COM port in parenthese next to its name.

### TOX setup
Make sure settings on the custom parameters *Setup* page are set correctly for the projector you are using. Baud Rate, Data Bits, and Stop Bits settings will be outlined in the projector model's RS232 commands manual

## Usage
Commands and settings differ from brand to brand, and even between models. But each model, series, or brand will outline the commands in either their product manual, or a seperate RS232 command manual.

The messages outlined in the manuals are usually ASCII, Hexadecimal, or they may provide both. In this system, hex is a bit easier to use since there is only one code per character, whereas ASCII could have different ways of expressing elements such as an escape character.

For example, Benq has ASCII messages in their manual with a '<CR>' their syntax for a carriage return, whereas Barco uses '[CR]'. In Hexadecimal, it is simply '0D', with no other alternatives. ASCII messages with escape sequences such as <CR> or [CR] are converted in our component, but there may be other variations we haven't explicitly accounted for.

Operation is simple. Enter the command into the appropriate text box, and to trigger it just hit the corresponding pulse button.

## Example setups

### NEC NP600S
Baud Rate = `19200`<br>
Data Bits = `8`<br>
Stop Bits = `1`<br>
Message Type = `HEX`<br>

On Message = `02 00 00 00 00 02`<br>
Off Message = `02 01 00 00 00 03`<br>
Picture Mute On = `02 10 00 00 00 12`<br>
Picture Mute Off = `02 11 00 00 00 13`<br>

### BENQ MX819ST
Baud Rate = `115200`<br>
Data Bits = `8`<br>
Stop Bits = `1`<br>
Message Type = `ASCII`<br>

On Message = `<CR>*pow=on#<CR>`<br>
Off Message = `<CR>*pow=off#<CR>`<br>
Picture Mute On = `<CR>*blank=on#<CR>`<br>
Picture Mute Off = `<CR>*blank=off#<CR>`<br>

### OPTOMA DS550
Baud Rate = `9600`<br>
Data Bits = `8`<br>
Stop Bits = `1`<br>
Message Type = `HEX`<br>

On Message = `7E 30 30 30 30 20 31`<br>
Off Message = `7E 30 30 30 30 20 32`<br>
Picture Mute On = `7E 30 30 30 32 20 31`<br>
Picture Mute Off = `7E 30 30 30 32 20 32`<br>

## Troubleshooting
If you find an issue, submit a pull request or post an issue on this repo. 

## User Setups
Projector Brand and Model:<br>
User Name:<br>
Command:<br> 

## Attribution
If you use this in one of your projects, feel free to give us (nVoid) a shoutout or just let us know what you're up to! 
