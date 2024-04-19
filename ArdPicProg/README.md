# ardpicprog(1) - General Commands Manual

## NAME
       ardpicprog - Arduino-based programmer for PIC devices

## SYNOPSIS
    ardpicprog --quiet -q --verbose -v --help -h
    --device DEVTYPE -d DEVTYPE --pic-serial-port PORT -p PORT
    --input-hexfile INPUT -i INPUT --output-hexfile OUTPUT -o OUTPUT
    --ihx8m --ihx16  --ihx32 --cc-hexfile CCFILE -c CCFILE --skip-ones
    --erase --burn --force-calibration --list-devices --detect --speed SPEED

## ENVIRONMENT
    PIC_DEVICE PIC_PORT

## DESCRIPTION
See http://rweather.github.io/ardpicprog/host_program.html

## OPTIONS
* Default port: /dev/ttyUSB0
* Default speed: 115200 bit/s
* See http://rweather.github.io/ardpicprog/host_program.html

## AUTHOR
Written by Southern Storm Software, Pty Ltd.

http://rweather.github.io/ardpicprog/

## SEE ALSO
picprog(1)

Southern Storm Software                      May 2012                               ardpicprog(1)
