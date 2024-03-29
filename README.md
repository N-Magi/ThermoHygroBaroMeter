# ThermoHygroBaroMeter
![ThermoHygroBaroMeter](/image/DSC_0850.jpg "温湿度気圧計")

スモークアクリルを使って少しおしゃれな置物風

秋月電子をフラットして適当にC型基板を買ったらフッと思いついた一品

ユニバーサル基板を使いながら配線の取り回したその他の見た目にこだわってお酒をひっかけながら作りました.

ちなみに回路図なしで頭の中で行き当たりばったりで設計しています.

## 概要
`ThermoHygroBaroMeter`は温度,湿度,気圧を表示するマルチ計測器です.

使用しているのはBOSCHのBME280です. 大体1080円しました.

## 回路図
![ThermoHygorBaroMeterCircuit](/image/ThermoHygorBaroMeterCircuit.png "回路図")

いたって普通の回路図です。

ハードウェアSPIを使うことで通信速度を向上させています。

基板サイズは76mm * 51mm に収まっています. 秋月電子のC型基板です.

## ソフトウェア
使用するATmega328p-puはArduinoブートローダを焼きこんで使用してください.

また各ピン配置は` define `ステートメントで変更可能です.

adafuitsのBME280ライブラリを使用しています. インストールしてください.

あらかじめ最適値に設定しております.

### ` #define `の内容
|機能|デフォルト値|説明|
|:-:|:-:|:-:|
`SER  `    |    0   |SERピン|
|`RCLK `   |    1   |レジスタークロックピン|
|`SRCLK `  |    2   |シフトレジスタクロックピン|
|`SRCLR `  |    3   |シフトレジスタクリアピン|
|`DI1`     |    5   |7セグ　一桁目のカソードピン|
|`DI2`     |    6   |7セグ 二桁目|
|`DI3`     |    7   |7セグ 三桁目|
|`DI4`     |    8   |7セグ  四桁目|
|`SWITCH_TIME`| 50000   |モード切り替えの時間[ms]|
|`DELAY`    |   0   |シフトレジスタの入力用遅延時間|
|`DISPLAY_HIGH_DELAY` | 3 | ディスプレイのON時間[ms]|
|`DISPLAY_LOW_DELAY`    | 1 | ディスプレイのOFF時間[ms]|
|`USE_SMALL_DEGREEC`    |   1   |   Cの小文字を使用する  |
|`USE_FAHRENHEIT `      |   0   |   華氏を使用する      |
