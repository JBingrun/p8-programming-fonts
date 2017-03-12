# PICO-8 Programming Fonts

Herein lies a collection of fonts I've modified for PICO-8 programming.  Why?  I can't say, really, other than it was a small challenge I was tempted to solve.  I can't say I use them... not until, _maybe_, I write a patcher (due to licensing) for Consolas.

### Encoding

It came up elsewhere what the p8 encoding might be.  It is clearly a custom form of Extended ASCII... or, as I think of it, `P8SCII` (first! :grin:).  But that's just my opinion.  Ask the author what he calls it, if anything.  Regardless, it's an 8-bit character set right now and -- judging by where the current extended characters sit (on top of Windows 125x, ISO 8859-x, and Unicode control characters) -- forever.

If working on P8 code in an external editor, open and save with a DOS encoding if you can, such as Code Page 437.  This works well in Sublime Text (as "DOS (CP 437)") and in Notepad++ (as either "ANSI" or "Western European -> OEM-US") and probably most others.

Saving as Windows 1252 can _appear_ to preserve the embedded extended characters when using these fonts... but don't be fooled, you may find differently when you reload the file in PICO-8.  To fix, reload in your editor as Windows 1252 and save as CP 437.  ISO 8859-1 won't work unless you get really lucky with your editor ("No, your _text_ editor!").  Feeling lucky?  Saving as UTF-8 will destroy the encoding, for sure, with multibyte replacements.

In my opinion, however, it is safer to escape the extended P8SCII characters than embed them:

♥ = `\135` or `\x87` (or `‡` in a PICO-8 OEM font)

### Editor Specifics

The comments here will, hopefully, tell you how to use the fonts in most editors, regardless of whether or not it is listed here.

#### Sublime Text

Here are some useful preferences to set in "Setting - Syntax Specific" for your *.p8 files:
```
"font_face": "PICO-8 Raize",
"fallback_encoding": "DOS (CP 437)",
"default_encoding": "DOS (CP 437)",
"rulers": [32]
```

Sublime won't load OEM fonts (which may just as well since some editors don't display them completely anyway) so use the non-OEM variants, mono or variable-width, your choice.

Sublime has an odd limitation when working with bitmap FON fonts that a few of you may run into.  That is, if you change the text zoom in Windows to, say, 150% (if you're on a high-DPI display and losing your youth vision like me), Sublime will not let you zoom all the way out with many FON fonts.  The furthest I can zoom out in Sublime with my current Windows display setting is 2x the actual bitmap size for all FON files I have here thus far (I think Windows text zoom is the cause--not sure yet).  The really bizarre thing is that Sublime will let you zoom all the way out on all but the smallest font in a FON file if the file has more than one font in it.  (Thus, the workaround might be to put a tiny font in all files [such as the 4x6 ROM font] but I don't care to go down that hacky road, so good luck getting Sublime to care enough to fix it.)

If working with TrueType or OpenType fonts in Windows with Sublime, the secret to turning off antialiasing is to set GDI mode as well:
```
"font_options": [ "gdi", "no_antialias" ]
```

#### Notepad++

Notepad++ works well with any of these fonts.  If loading and saving as "ANSI" use the OEM variants.  If loading and saving as "OEM-US" use the non-OEM variants.  Sounds a little backwards, eh?  But it makes some sense if you understand how code pages get translated by OSs.

#### Notepad

You don't want to use Windows' Notepad because it doesn't support the Unix line terminators that PICO-8 uses.  I thought I would mention it, however, because it is one of those programs that will only display correctly with the OEM variants of these fonts.

## The Fonts
_(Preview images coming...... maybe.)_

### PICO-8 ROM
I really didn't want to take the time creating this set -- because I don't see the point in punishing yourself with it -- I did enough of that with bad fonts ***and*** displays way back somewhere in the last century -- but I knew I would be pestered for it if I didn't create it, so here it is in all its "dune" glory (you might be able to figure out what that means if you find this 4x6 font to be worse than all other 4x6 fonts like I do).  I even created these as multi-font FON files (same font in multiple bitmap resolutions) so that your editor should let you zoom in pretty big before Windows decides you're totally insane and replaces it with a default vector font.
* [**PICO-8 ROM OEM**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-rom-oem.fon)
* [**PICO-8 ROM**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-rom.fon)
* [**PICO-8 ROM Mono OEM**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-rom-mono-oem.fon)
* [**PICO-8 ROM Mono**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-rom-mono.fon)

### PICO-8 Tektite
This is the first font I worked on... because, well, it was there when poking around various tools.  I call this one a semi-sane choice for programming.  It is a very VGA-ish 9x16 (plus I added an extra line of "external leading" because it looks better with more line space, but few editors pay attention to that attribute--_HxD_ being the only one I tested that does--so you may want to tell your editor to space it more).  If you like it, you can get the matching set of non-P8 versions (that I also modified a bit from the original Tektite font) by visiting their home here: https://github.com/juanitogan/mkwinfont
* [**PICO-8 Tektite OEM**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-tektite-oem.fon)
* [**PICO-8 Tektite**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-tektite.fon)
* [**PICO-8 Tektite OEM Mono**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-tektite-mono-oem.fon)
* [**PICO-8 Tektite Mono**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-tektite-mono.fon)
* Matching fonts:
  * [**Tektite OEM**](https://github.com/juanitogan/mkwinfont/raw/master/fonts/tektite16x9oem.fon) (CP 437)
  * [**Tektite**](https://github.com/juanitogan/mkwinfont/raw/master/fonts/tektite16x9.fon) (Windows 1252, ISO-8859-1, "Font has XWindows encoding" option in PuTTY)

### PICO-8 MSTester
This one is a formerly-sane choice for programming.  It is a squished VGA-ish of 8x12.  This is a sample font that was included with some Microsoft sample code for building a FNT editor, ages ago.  Thus, it sounds like public domain to me even though it looks suspiciuosly like an old version of **Fixedsys**.  I did descend the brackets a bit -- the curly brackets were hardly recognizable.  Otherwise, unchanged in the 7-bit region.
* [**PICO-8 MSTester OEM**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-tester-oem.fon)
* [**PICO-8 MSTester**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-tester.fon)
* [**PICO-8 MSTester OEM Mono**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-tester-mono-oem.fon)
* [**PICO-8 MSTester Mono**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-tester-mono.fon)

### PICO-8 Raize
This one is a fairly-sane choice for programming.  It comes in many sizes so I chose the fairly large 11x22 regular for some variety here (maybe I should include the 11x22 bold as well... but I'm bored with this P8 font stuff already and anxious to get back to game building).  I looked at ProFont, Proggy, Terminus, and a few others, and decided I liked Raize the best even though I'm not a huge fan of some of the squarish characters and dislike the high placement of `+` and `-`.  So, now you have to live with it or make your own mod or your favorite.  I'm not entirely sure it is licensed for modding like most of the others I looked at are -- it is copyrighted by Raize Software and given out as free software with no license details.
* [**PICO-8 Raize OEM**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-raize-oem.fon)
* [**PICO-8 Raize**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-raize.fon)
* [**PICO-8 Raize OEM Mono**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-raize-mono-oem.fon)
* [**PICO-8 Raize Mono**](https://github.com/juanitogan/p8-programming-fonts/raw/master/bitmap-fonts/p8-raize-mono.fon)
* Matching fonts:
  * [Raize Software](http://www.raize.com/DevTools/Tools/RzFont.asp) - Three sizes in regular and bold, plus Unix/Linux versions