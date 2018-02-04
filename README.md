Susie plugin for OPTWORKS games (spioptw)
=========================================
[![AppVeyor Build Status](https://ci.appveyor.com/api/projects/status/1ygpy7b1v8m9vdap/branch/master?svg=true)](https://ci.appveyor.com/project/gocha/spioptw/branch/master)

spioptw is a Susie plugin package for [OPTWORKS](http://www.toranoana.jp/mailorder/cit/circle/19/66/5730303436363139/ns_4f5054574f524b53_01.html) games (NC-17).

- **ifhmp.spi**: Decoder plugin for HMP image format (16-bit color image)
- **ifpmp.spi**: Decoder plugin for PMP image format (24-bit color image)

I'm not sure whether the plugins support all available OPTWORKS games, since I don't know about the game itself too much. I analyzed the format just by request.

What is Susie plugin?
------------------------

[Susie](http://www.digitalpad.co.jp/~takechin/) is an old-school picture viewer for Windows, which can load additional formats by adding Susie plugins (*.spi). In Japan, Susie plugin is often used for decoding custom image formats inside a game.

There are several picture viewers that supports Susie plugin. For example:

- [Susie](http://www.digitalpad.co.jp/~takechin/betasue.html#susie32)
- [Linar](http://hp.vector.co.jp/authors/VA015839/)
- [picture effecter](http://www.asahi-net.or.jp/~DS8H-WTNB/software/index.html)
- [stereophotomaker](http://stereo.jpn.org/eng/stphmkr/)
- [vix](http://www.forest.impress.co.jp/library/software/vix/)
- [A to B converter](http://www.asahi-net.or.jp/~KH4S-SMZ/spi/abc/index.html)
- [ACDSee](http://www.acdsee.com/) (commercial)

My favorite is [Linar](http://hp.vector.co.jp/authors/VA015839/) for browsing, and [AtoB Converter](http://www.asahi-net.or.jp/~kh4s-smz/spi/abc/) for batch conversion.

Note
------------------------

- Any use of the software is entirely at your own risk.

File Format
------------------------

There are two formats as you know, HMP and PMP.
HMP is a 16-bit color image, and PMP is a 24-bit color image.
Both they are similar to Windows Bitmap format, but they have a small compression mechanism.

The image formats are constituted by a file header, a compressed bitmap, and a flagmap which indicates how to decompress the bitmap.
File header structure is very simple. See the Susie plugin's header file for details.

The bitmap of HMP is compressed by RLE.
The flagmap indicates the data length and what color to use for decompression.

PMP image has three bitmaps which correspond to each RGB element.
Also, there are three flagmaps which correspond to each bitmaps.
The bitmap/flagmap can be separated into two areas.
The first part is for upper 4 bits of RGB, and the second one is for lower 4 bits.
I think the compression is a sort of delta encoding.

It was a good tutorial for me, a newbie researcher.
