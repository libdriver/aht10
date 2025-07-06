### 1. Board

#### 1.1 Board Info

Board Name: Raspberry Pi 4B.

IIC Pin: SCL/SDA GPIO3/GPIO2.

### 2. Install

#### 2.1 Dependencies

Install the necessary dependencies.

```shell
sudo apt-get install libgpiod-dev pkg-config cmake -y
```

#### 2.2 Makefile

Build the project.

```shell
make
```

Install the project and this is optional.

```shell
sudo make install
```

Uninstall the project and this is optional.

```shell
sudo make uninstall
```

#### 2.3 CMake

Build the project.

```shell
mkdir build && cd build 
cmake .. 
make
```

Install the project and this is optional.

```shell
sudo make install
```

Uninstall the project and this is optional.

```shell
sudo make uninstall
```

Test the project and this is optional.

```shell
make test
```

Find the compiled library in CMake. 

```cmake
find_package(aht10 REQUIRED)
```

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
./aht10 -i

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
./aht10 -p

aht10: SCL connected to GPIO3(BCM).
aht10: SDA connected to GPIO2(BCM).
```

```shell
./aht10 -t read --times=3

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
aht10: temperature: 27.7C.
aht10: humidity: 24%.
aht10: temperature: 27.6C.
aht10: humidity: 24%.
aht10: temperature: 27.6C.
aht10: humidity: 24%.
aht10: finish read test.
```

```shell
./aht10 -e read --times=3

aht10: 1/3.
aht10: temperature is 27.67C.
aht10: humidity is 23%.
aht10: 2/3.
aht10: temperature is 27.66C.
aht10: humidity is 23%.
aht10: 3/3.
aht10: temperature is 27.68C.
aht10: humidity is 23%.
```

```shell
./aht10 -h

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

