---
layout: osdoc
title: Text
group: Usage
permalink: /text/
parser: academicmarkdown
---

Bi-directional-text support and non-Latin default fonts are available as of OpenSesame 2.8.0.
{: .page-notification}

## Overview

%--
toc:
 mindepth: 2
 exclude: [Overview]
--%

## Formatting (HTML subset)

You can use a subset of HTML tags, which you can simply insert into your text. You can use these tags everywhere: In `sketchpad` items, in `inline_script`s (provided you use the `openexp.canvas` class), in forms, etc.

Example:

{% highlight html %}
OpenSesame supports a sub-set of HTML tags:
- <b>Bold face</b>
- <i>Italic</i>
- <u>Underline</u>

In addition, you can pass 'color', 'size', and 'style' as keywords to a 'span' tag:
- <span color="red">Color</span>
- <span size="32">Font size</span>
- <span style="serif">Font style</span>

Finally, you can force newlines with the 'br' tag:
Line 1<br>Line 2
{% endhighlight %}

The text above will be rendered as shown in %FigHTML. (The exact appearance depends on your default colors, font, etc.)

%--
figure:
 id: FigHTML
 source: form-example.png
 caption: "Using (a subset of) HTML, you can define the appearance of your text."
--%

## Fonts

### Default fonts

You can select one of the default fonts from the font-selection dialogs (%FigFontSelect). These fonts are included with OpenSesame and your experiment will therefore be fully portable when you use them.

%--
figure:
 id: FigFontSelect
 source: font-selection-dialog.png
 caption: "A number of default fonts, which are bundled with OpenSesame, can be selected through the font-selection dialogs."
--%

The fonts have been renamed for clarity, but correspond to the following open-source fonts:

|__Name in OpenSesame__		|__Actual font__		|
|`sans`						|Droid Sans				|
|`serif`					|Droid Serif			|
|`mono`						|Droid Sans Mono		|
|`chinese-japanese-korean`	|WenQuanYi Micro Hei	|
|`arabic`					|Droid Arabic Naskh		|
|`hebrew`					|Droid Sans Hebrew		|
|`hindi`					|Lohit Hindi			|
 
### Selecting a custom font through the font-selection dialog

If you select 'other ...' in the font selection dialog, you can select any font that is available on your operating system. If you do this, your experiment is no longer fully portable, and will require that the selected font is installed on the system that you run your experiment on.

### Placing a custom font in the file pool

Another way to use a custom font is to put a font file in the file pool. For example, if you place the font file `inconsolata.ttf` in the file pool, you can use this font in a `sketchpad` item, like so:

	draw textline 0.0 0.0 "This will be inconsolata" font_family="inconsolata"
	
Note that the font file must be a truetype `.ttf` file.

## Bi-directional text support

By default, all text is rendered from left to right. However, you can enable bi-directional-text support through the 'Bi-directional-text support' checkbox in the general tab:

%--
figure:
 id: FigBidi
 source: bidi.png
 caption: ".bat lareneg eht hguorht delbane eb nac troppus txet-lanoitcerid-iB"
--%

## Why do I see squares or question marks when I run my experiment?

If you select the font `mono` and add a string of, say, Hebrew text to a `sketchpad`, the user interface will display your text just fine. However, when you run the experiment, you will see a row of squares, and no characters. This happens because the `mono` font, which is actually 'Droid Sans Mono', does not contain Hebrew characters. The user interface deals with this by falling back to a different font that does contain Hebrew characters. However, the OpenSesame runtime deals with this by showing ... a bunch of squares.

The bottom line is that if you find that characters are missing, you should select a different font that actually contains the characters--Even when the characters display fine in the user interface!
