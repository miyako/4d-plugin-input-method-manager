# 4d-plugin-input-method-manager
Commands to control the front-end text editor on Windows.

**注記**: Windows 7以前のOSではIMEモードがスレッド単位で保持されていました。
Windows 8やWindows Server 2012ではユーザー単位で保持されるように仕様が変更されています。
この変更によって，``ImeMode``・・・によるIMEモードの切り替えが動作しない場合があります。

https://docs.grapecity.com/help/spread-winforms-8/gc-spwin-ime.html

### Platform

| carbon | cocoa | win32 | win64 |
|:------:|:-----:|:---------:|:---------:|
|||<img src="https://cloud.githubusercontent.com/assets/1725068/22371562/1b091f0a-e4db-11e6-8458-8653954a7cce.png" width="24" height="24" />|<img src="https://cloud.githubusercontent.com/assets/1725068/22371562/1b091f0a-e4db-11e6-8458-8653954a7cce.png" width="24" height="24" />|

### Version

<img width="32" height="32" src="https://user-images.githubusercontent.com/1725068/73986501-15964580-4981-11ea-9ac1-73c5cee50aae.png"> <img src="https://user-images.githubusercontent.com/1725068/73987971-db2ea780-4984-11ea-8ada-e25fb9c3cf4e.png" width="32" height="32" />

## Syntax

```4d
error:=IM Associate
error:=IM Disassociate
```

Parameter|Type|Description
------------|------------|----
error|LONGINT|``ImmAssociateContextEx``の返り値（エラーコード）

```4d
result:=IM Get mode (conversion;sentence)
result:=IM Set mode (conversion;sentence)
```

Parameter|Type|Description
------------|------------|----
conversion|LONGINT|変換モード
sentence|LONGINT|文章モード
error|LONGINT|``ImmSetConversionStatus``または``ImmGetConversionStatus``の返り値（エラーコード）

* IME Conversion Mode

```c
CMODE_DIRECT_INPUT -1
CMODE_ALPHANUMERIC 0
CMODE_NATIVE 1
CMODE_KATAKANA 2
CMODE_LANGUAGE 3
CMODE_FULLSHAPE 8
CMODE_ROMAN 16
CMODE_CHARCODE 32
CMODE_HANJACONVERT 64
CMODE_SOFTKBD 128
CMODE_NOCONVERSION 256
CMODE_EUDC 512
CMODE_SYMBOL 1024
CMODE_FIXED 2048
```

* IME Sentence Mode

```c
SMODE_NONE 0
SMODE_PLURALCLAUSE 1
SMODE_SINGLECONVERT 2
SMODE_AUTOMATIC 4
SMODE_PHRASEPREDICT 8
SMODE_CONVERSATION 16
```

半角英数は``CMODE_ROMAN;SMODE_AUTOMATIC``  
全角ひらがなは``CMODE_ROMAN|CMODE_FULLSHAPE|CMODE_NATIVE;SMODE_AUTOMATIC``
