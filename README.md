[English](/README.md) | [ 简体中文](/README_zh-Hans.md) | [繁體中文](/README_zh-Hant.md) | [日本語](/README_ja.md) | [Deutsch](/README_de.md) | [한국어](/README_ko.md)

<div align=center>
<img src="/doc/image/logo.svg" width="400" height="150"/>
</div>

## LibDriver AHT10

[![MISRA](https://img.shields.io/badge/misra-compliant-brightgreen.svg)](/misra/README.md) [![API](https://img.shields.io/badge/api-reference-blue.svg)](https://www.libdriver.com/docs/aht10/index.html) [![License](https://img.shields.io/badge/license-MIT-brightgreen.svg)](/LICENSE)

AHT10, as a new generation of temperature and humidity sensors, has established a new standard in size and intelligence. It is embedded in a double row flat no-lead package suitable for reflow soldering, with a bottom of 4 x 5 mm and a height of 1.6 mm. The sensor outputs calibrated digital 2 signals in standard IC format. AHT10 is equipped with a newly designed ASIC chip, an improved MEMS semiconductor capacitive humidity sensing element and a standard on-chip temperature sensing element. As a result, the performance of the new generation of temperature and humidity sensors has greatly improved or even exceeded that of the previous ones with more stability in harsh environments. Each sensor is calibrated and tested, with product batch number printed on the surface of the product. Due to the improvement and miniaturization of the sensor, its cost-effective ratio is higher, and finally all equipment will benefit from the cutting edge energy-saving operation mode.

LibDriver AHT10 is a full-featured driver of AHT10 launched by LibDriver.It provides the function of reading temperature and relative humidity. LibDriver is MISRA compliant.

### Table of Contents

  - [Instruction](#Instruction)
  - [Install](#Install)
  - [Usage](#Usage)
    - [example basic](#example-basic)
  - [Document](#Document)
  - [Contributing](#Contributing)
  - [License](#License)
  - [Contact Us](#Contact-Us)

### Instruction

/src includes LibDriver AHT10 source files.

/interface includes LibDriver AHT10 IIC platform independent template.

/test includes LibDriver AHT10 driver test code and this code can test the chip necessary function simply.

/example includes LibDriver AHT10 sample code.

/doc includes LibDriver AHT10 offline document.

/datasheet includes AHT10 datasheet.

/project includes the common Linux and MCU development board sample code. All projects use the shell script to debug the driver and the detail instruction can be found in each project's README.md.

/misra includes the LibDriver MISRA code scanning results.

### Install

Reference /interface IIC platform independent template and finish your platform IIC driver.

Add the /src directory, the interface driver for your platform, and your own drivers to your project, if you want to use the default example drivers, add the /example directory to your project.

### Usage

You can refer to the examples in the /example directory to complete your own driver. If you want to use the default programming examples, here's how to use them.

#### example basic

```C
#include "driver_aht10_basic.h"

uint8_t res;
uint8_t i;
float temperature;
uint8_t humidity;

res = aht10_basic_init();
if (res != 0)
{
    return 1;
}

...

for (i = 0; i < 3; i++)
{
    aht10_interface_delay_ms(2000);
    res = aht10_basic_read((float *)&temperature, (uint8_t *)&humidity);
    if (res != 0)
    {
        (void)aht10_basic_deinit();

        return 1;
    }
    aht10_interface_debug_print("aht10: temperature is %0.2fC.\n", temperature);
    aht10_interface_debug_print("aht10: humidity is %d%%.\n", humidity); 
    
    ...
        
}

...

(void)aht10_basic_deinit();

return 0;
```

### Document

Online documents: [https://www.libdriver.com/docs/aht10/index.html](https://www.libdriver.com/docs/aht10/index.html).

Offline documents: /doc/html/index.html.

### Contributing

Please refer to CONTRIBUTING.md.

### License

Copyright (c) 2015 - present LibDriver All rights reserved



The MIT License (MIT) 



Permission is hereby granted, free of charge, to any person obtaining a copy

of this software and associated documentation files (the "Software"), to deal

in the Software without restriction, including without limitation the rights

to use, copy, modify, merge, publish, distribute, sublicense, and/or sell

copies of the Software, and to permit persons to whom the Software is

furnished to do so, subject to the following conditions: 



The above copyright notice and this permission notice shall be included in all

copies or substantial portions of the Software. 



THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR

IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,

FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE

AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER

LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,

OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE

SOFTWARE. 

### Contact Us

Please send an e-mail to lishifenging@outlook.com.