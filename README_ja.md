[English](/README.md) | [ 简体中文](/README_zh-Hans.md) | [繁體中文](/README_zh-Hant.md) | [日本語](/README_ja.md) | [Deutsch](/README_de.md) | [한국어](/README_ko.md)

<div align=center>
<img src="/doc/image/logo.svg" width="400" height="150"/>
</div>

## LibDriver AHT10

[![MISRA](https://img.shields.io/badge/misra-compliant-brightgreen.svg)](/misra/README.md) [![API](https://img.shields.io/badge/api-reference-blue.svg)](https://www.libdriver.com/docs/aht10/index.html) [![License](https://img.shields.io/badge/license-MIT-brightgreen.svg)](/LICENSE)

AHT10は、新世代の温度湿度センサーとして、サイズとインテリジェンスにおいて新たな基準を確立しました。底面4 x 5 mm、高さ1.6 mmの、リフローはんだ付けに適した2列フラットノーリードパッケージに収められています。センサーは標準IC形式で校正済みのデジタル2信号を出力します。AHT10は、新設計のASICチップ、改良されたMEMS半導体容量性湿度センサー素子、そして標準オンチップ温度センサー素子を搭載しています。その結果、新世代の温度湿度センサーの性能は、過酷な環境下でもより安定し、従来のセンサーを大幅に上回りました。すべてのセンサーは校正とテストを実施し、製品表面には製品バッチ番号が印刷されています。センサーの改良と小型化により、コスト効率が向上し、最終的にはあらゆる機器が最先端の省エネ動作モードの恩恵を受けることができます。

LibDriver AHT10 は、LibDriver によって起動される AHT10 のフル機能ドライバーです。温度と相対湿度を読み取る機能を提供します。 LibDriver は MISRA 準拠です。

### 目次

  - [説明](#説明)
  - [インストール](#インストール)
  - [使用](#使用)
    - [example basic](#example-basic)
  - [ドキュメント](#ドキュメント)
  - [貢献](#貢献)
  - [著作権](#著作権)
  - [連絡して](#連絡して)

### 説明

/ srcディレクトリには、LibDriver AHT10のソースファイルが含まれています。

/ interfaceディレクトリには、LibDriver AHT10用のプラットフォームに依存しないIICバステンプレートが含まれています。

/ testディレクトリには、チップの必要な機能を簡単にテストできるLibDriver AHT10ドライバーテストプログラムが含まれています。

/ exampleディレクトリには、LibDriver AHT10プログラミング例が含まれています。

/ docディレクトリには、LibDriver AHT10オフラインドキュメントが含まれています。

/ datasheetディレクトリには、AHT10データシートが含まれています。

/ projectディレクトリには、一般的に使用されるLinuxおよびマイクロコントローラー開発ボードのプロジェクトサンプルが含まれています。 すべてのプロジェクトは、デバッグ方法としてシェルスクリプトを使用しています。詳細については、各プロジェクトのREADME.mdを参照してください。

/ misraはLibDriver misraコードスキャン結果を含む。

### インストール

/ interfaceディレクトリにあるプラットフォームに依存しないIICバステンプレートを参照して、指定したプラットフォームのIICバスドライバを完成させます。

/src ディレクトリ、プラットフォームのインターフェイス ドライバー、および独自のドライバーをプロジェクトに追加します。デフォルトのサンプル ドライバーを使用する場合は、/example ディレクトリをプロジェクトに追加します。

### 使用

/example ディレクトリ内のサンプルを参照して、独自のドライバーを完成させることができます。 デフォルトのプログラミング例を使用したい場合の使用方法は次のとおりです。

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

### ドキュメント

オンラインドキュメント: [https://www.libdriver.com/docs/aht10/index.html](https://www.libdriver.com/docs/aht10/index.html)。

オフラインドキュメント: /doc/html/index.html。

### 貢献

CONTRIBUTING.mdを参照してください。

### 著作権

著作権（c）2015-今 LibDriver 全著作権所有

MITライセンス（MIT）

このソフトウェアおよび関連するドキュメントファイル（「ソフトウェア」）のコピーを取得した人は、無制限の使用、複製、変更、組み込み、公開、配布、サブライセンスを含む、ソフトウェアを処分する権利を制限なく付与されます。ソフトウェアのライセンスおよび/またはコピーの販売、および上記のようにソフトウェアが配布された人の権利のサブライセンスは、次の条件に従うものとします。

上記の著作権表示およびこの許可通知は、このソフトウェアのすべてのコピーまたは実体に含まれるものとします。

このソフトウェアは「現状有姿」で提供され、商品性、特定目的への適合性、および非侵害の保証を含むがこれらに限定されない、明示または黙示を問わず、いかなる種類の保証もありません。 いかなる場合も、作者または著作権所有者は、契約、不法行為、またはその他の方法で、本ソフトウェアおよび本ソフトウェアの使用またはその他の廃棄に起因または関連して、請求、損害、またはその他の責任を負わないものとします。

### 連絡して

お問い合わせくださいlishifenging@outlook.com。