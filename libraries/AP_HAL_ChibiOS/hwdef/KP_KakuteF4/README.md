# KakuteF4 AIO Flight Controller

The [KakuteF4 AIO](http://www.holybro.com/product/47) is a flight controller produced by [Holybro](http://www.holybro.com).

## Modified version!

This is a modified target to allow 7 outputs from Kakute F4.
LED strip pad is utilized as number five and SmartPort (USART1) circuitry is desoldered to allow outputs PA9 and PA10 be use as outputs number six and seven.
Serial order is also changed.

## Features

 - STM32F405 microcontroller
 - ICM20689 IMU
 - BMP280 barometer
 - MAX7456 OSD
 - 5 UARTs
 - 4 PWM outputs

## Pinout

![KakuteF4 Top](kakutef4_top.jpg "KakuteF4Top")

## UART Mapping

The UARTs are marked Rn and Tn in the above pinouts. The Rn pin is the
receive pin for UARTn. The Tn pin is the transmit pin for UARTn.

The pin labelled Rx on each corner of the board is a common pin for
ESC telemetry input.

 - SERIAL0 -> USB
 - SERIAL1 -> UART3 (RC input)
 - SERIAL2 -> UART4
 - SERIAL3 -> USART6 (GPS by default)
 - SERIAL4 -> UART5 (ESC Telemetry pads, RX only)

## RC Input
 
RC input is configured on the R3 (UART3_RX) pin. It supports all RC protocols.
 
## FrSky Telemetry
 
FrSky Telemetry is removed (desoldered inverters) to allow for two additional motor/servo outputs.
  
## OSD Support

The KakuteF4 supports OSD using OSD_TYPE 1 (MAX7456 driver). You can also connect DJI on a spare serial.

## PWM Output

The KakuteF4 supports up to 4 PWM outputs. But this target enhances it to seven, but requires desoldering of SmartPort inverters.
All outputs support DShot as well as all PWM types. 

Outputs have following groups:

 - PWM 1 and 2 in group1
 - PWM 3 and 4 in group2
 - PWM 5 in group3
 - PWM 6 and 7 in group4

Channels within the same group need to use the same output rate. If
any channel in a group uses DShot then all channels in the group need
to use DShot.

## Battery Monitoring

The board has a builting voltage and current sensor. The voltage
sensor can handle up to 6S LiPo batteries.

The correct battery setting parameters are:

 - BATT_MONITOR 4
 - BATT_VOLT_PIN 13
 - BATT_CURR_PIN 12
 - BATT_VOLT_MULT 10.1
 - BATT_AMP_PERVLT 17.0

## Compass

The KakuteF4 AIO does not have a builting compass, but you can attach an external compass using I2C on the SDA and SCL pads.

## Logging

The KakuteF4 supports on-board dataflash logging.

## Loading Firmware

Initial firmware load can be done with DFU by plugging in USB with the
bootloader button pressed. Then you should load the "with_bl.hex"
firmware, using your favourite DFU loading tool.

Once the initial firmware is loaded you can update the firmware using
any ArduPilot ground station software. Updates should be done with the
*.apj firmware files.

