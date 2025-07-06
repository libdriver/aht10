### 1. Chip

#### 1.1 Chip Info

Chip Name: STM32F407ZGT6.

Extern Oscillator: 8MHz.

UART Pin: TX/RX PA9/PA10.

IIC Pin: SCL/SDA PB8/PB9.

### 2. Development and Debugging

#### 2.1 Integrated Development Environment

LibDriver provides both Keil and IAR integrated development environment projects.

MDK is the Keil ARM project and your Keil version must be 5 or higher.Keil ARM project needs STMicroelectronics STM32F4 Series Device Family Pack and you can download from https://www.keil.com/dd2/stmicroelectronics/stm32f407zgtx.

EW is the IAR ARM project and your IAR version must be 9 or higher.

#### 2.2 Serial Port Parameter

Baud Rate: 115200.

Data Bits : 8.

Stop Bits: 1.

Parity: None.

Flow Control: None.

#### 2.3 Serial Port Assistant

We use '\n' to wrap lines.If your serial port assistant displays exceptions (e.g. the displayed content does not divide lines), please modify the configuration of your serial port assistant or replace one that supports '\n' parsing.

### 3. AHT10

#### 3.1 Command Instruction

1. Show aht10 chip and driver information.

   ```shell
   aht10 (-i | --information)
   ```

2. Show aht10 help.

   ```shell
   aht10 (-h | --help)
   ```

3. Show aht10 pin connections of the current board.

   ```shell
   aht10 (-p | --port)
   ```

4. Run aht10 read test, num means test times.

   ```shell
   aht10 (-t read | --test=read) [--times=<num>]
   ```

5. Run aht10 read function, num means test times.

   ```shell
   aht10 (-e read | --example=read) [--times=<num>]
   ```

#### 3.2 Command Example

```shell
aht10 -i

aht10: chip is ASAIR AHT10.
aht10: manufacturer is ASAIR.
aht10: interface is IIC.
aht10: driver version is 1.0.
aht10: min supply voltage is 1.8V.
aht10: max supply voltage is 3.6V.
aht10: max current is 10.00mA.
aht10: max temperature is 85.0C.
aht10: min temperature is -40.0C.
```

```shell
aht10 -p

aht10: SCL connected to GPIOB PIN8.
aht10: SDA connected to GPIOB PIN9.
```

```shell
aht10 -t read --times=3

aht10: chip is ASAIR AHT10.
aht10: manufacturer is ASAIR.
aht10: interface is IIC.
aht10: driver version is 1.0.
aht10: min supply voltage is 2.2V.
aht10: max supply voltage is 5.5V.
aht10: max current is 0.98mA.
aht10: max temperature is 85.0C.
aht10: min temperature is -40.0C.
aht10: start read test.
aht10: temperature: 31.5C.
aht10: humidity: 21%.
aht10: temperature: 31.3C.
aht10: humidity: 21%.
aht10: temperature: 31.2C.
aht10: humidity: 20%.
aht10: finish read test.
```

```shell
aht10 -e read --times=3

aht10: 1/3.
aht10: temperature is 30.16C.
aht10: humidity is 21%.
aht10: 2/3.
aht10: temperature is 30.10C.
aht10: humidity is 21%.
aht10: 3/3.
aht10: temperature is 30.05C.
aht10: humidity is 21%.
```

```shell
aht10 -h

Usage:
  aht10 (-i | --information)
  aht10 (-h | --help)
  aht10 (-p | --port)
  aht10 (-t read | --test=read) [--times=<num>]
  aht10 (-e read | --example=read) [--times=<num>]

Options:
  -e <read>, --example=<read>    Run the driver example.
  -h, --help                     Show the help.
  -i, --information              Show the chip information.
  -p, --port                     Display the pin connections of the current board.
  -t <read>, --test=<read>       Run the driver test.
      --times=<num>              Set the running times.([default: 3])
```

