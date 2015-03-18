Susie plugin for OPTWORKS games (spioptw)
=========================================

spioptw は [OPTWORKS](http://www.toranoana.jp/mailorder/cit/circle/19/66/5730303436363139/ns_4f5054574f524b53_01.html) 製ゲーム向けの Susie プラグインパッケージです。

- **ifhmp.spi**: HMP 形式（16ビットカラー画像）向けの読み込みプラグイン
- **ifpmp.spi**: PMP 形式（24ビットカラー画像）向けの読み込みプラグイン

頼まれて解析しただけなので、どのタイトルに対応しているかはよくわかりません。

Susie プラグインとは？
------------------------

[Susie](http://www.digitalpad.co.jp/~takechin/) は昔ながらの Windows 向けの画像ビューアです。Susie プラグイン（*.spi）と呼ばれるファイルを追加することで対応フォーマットを増やすことができます。国内ではよくゲーム内部のカスタム画像フォーマットをデコードするのに Susie プラグインが使われます。

Susie プラグインに対応した画像ビューアはいくつか存在します。

- [Susie](http://www.digitalpad.co.jp/~takechin/betasue.html#susie32)
- [Linar](http://hp.vector.co.jp/authors/VA015839/)
- [picture effecter](http://www.asahi-net.or.jp/~DS8H-WTNB/software/index.html)
- [stereophotomaker](http://stereo.jpn.org/eng/stphmkr/)
- [vix](http://www.forest.impress.co.jp/library/software/vix/)
- [A to B converter](http://www.asahi-net.or.jp/~KH4S-SMZ/spi/abc/index.html)
- [ACDSee](http://www.acdsee.com/) (commercial)

わたしのお気に入りは、閲覧目的なら [Linar](http://hp.vector.co.jp/authors/VA015839/)、一括変換目的なら [AtoB Converter](http://www.asahi-net.or.jp/~kh4s-smz/spi/abc/) です。

注意事項・備考など
------------------------

- 本ツールを用いたことによる、いかなる損害やトラブルについても作者は責任を負いません。

ファイルフォーマット
------------------------

ご存知のとおり、HMP と PMP の2つのフォーマットがあります。
HMP が16ビットカラー画像で、PMP が24ビットカラー画像です。
どちらも Windows ビットマップ形式に似ていますが、ちょっとした圧縮の仕組みを備えています。

フォーマットはファイルヘッダと、圧縮されたビットマップと、展開方法を示すフラグマップで構成されています。
ファイルヘッダの構造は非常に単純です。詳細は Susie プラグインのヘッダーファイルをご覧ください。

HMP のビットマップはランレングス圧縮されています。
フラグマップによって展開のデータ長と使用する色が示されます。

PMP には RGB の各要素に対応する3つのビットマップがあります。
また、各ビットマップに対応した3つのフラグマップがあります。
ビットマップ及びフラグマップはの2つの領域に分けることが可能で、
前者はRGBの上位4ビットに対応し、後者が下位4ビットに対応します。
どうやら差分圧縮の一種であると言えそうです。

解析初心者のわたしにも理解しやすい良いフォーマットでした。圧倒的感謝。
