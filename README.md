PDFGen
======
<img src="/docs/pdfgen_logo.png" alt="PDFGen Logo" width="200" align="right"/>

<a href="https://www.buymeacoffee.com/EstIgnavus" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/default-orange.png" alt="Buy Me A Coffee" height="41" width="174"></a>

シンプルで簡単なC言語のPDF作成/生成ライブラリ。
ヘッダファイルを含むシングルファイルライブラリであるため、外部ライブラリへの依存はありません。

基本的なPDF出力を必要とするプログラムへの組み込みに便利です。

以下のPDFの機能を提供します。
* 様々なフォント/サイズ/色のテキスト
* 基本的な描画
    * 線
    * 短形
    * 塗り潰された短形
    * 多角形
    * 塗り潰された多角形
    * ベジェ曲線
* ブックマーク
* バーコード (Code-128 & Code-39)
* 画像埋め込み
    * PPM/PGM (バイナリ形式のみ)
    * JPEG
    * PNG (アルファチャンネルはサポートされていません)
    * BMP

サンプルプログラム
=============
```c
#include "pdfgen.h"

int main(void) {
    struct pdf_info info = {
        .creator = "My software",
        .producer = "My software",
        .title = "My document",
        .author = "My name",
        .subject = "My subject",
        .date = "Today"
    };
    struct pdf_doc *pdf = pdf_create(PDF_A4_WIDTH, PDF_A4_HEIGHT, &info);
    pdf_set_font(pdf, "Times-Roman");
    pdf_append_page(pdf);
    pdf_add_text(pdf, NULL, "これはテキストです", 12, 50, 20, PDF_BLACK);
    pdf_add_line(pdf, NULL, 50, 24, 150, 24, 3, PDF_BLACK);
    pdf_save(pdf, "output.pdf");
    pdf_destroy(pdf);
    return 0;
}
```

ライセンス
=======
[![License: Unlicense](https://img.shields.io/badge/license-Unlicense-blue.svg)](http://unlicense.org/)

このプログラムのソースコードはパブリックドメインです。
もし、気になる点があるようでしたら、andre@ignavus.net までご連絡ください。

Builds
======
Build status: [![GitHub Actions](https://github.com/AndreRenaud/PDFGen/workflows/Build%20and%20Test/badge.svg)](https://github.com/AndreRenaud/PDFGen/actions)

Appveyor status: [![Build status](https://ci.appveyor.com/api/projects/status/3qpsmr06xg5gx74j/branch/master?svg=true)](https://ci.appveyor.com/project/AndreRenaud/pdfgen/branch/master)

Code Coverage: [![Coverage Status](https://coveralls.io/repos/github/AndreRenaud/PDFGen/badge.svg?branch=master)](https://coveralls.io/github/AndreRenaud/PDFGen?branch=master)

Coverity scan: [![Coverity scan](https://scan.coverity.com/projects/11942/badge.svg)](https://scan.coverity.com/projects/andrerenaud-pdfgen)

Static Analysis
===============
This is a code base that I use to test static analysis tools. As such the build system is quite a bit more complex than should be necessary for a project of this size.
