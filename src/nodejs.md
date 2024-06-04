# Noscrape - PHP

## <br> Installation

To begin, install the *noscrape* library using `npm`:

    $ npm install noscrape

## <br> New Instance

Create a new instance of the *noscrape* class by providing the path to your desired font file. This sets up *noscrape*
to use the specified font for obfuscating text:

    # with require
    const { Noscrape } = require("noscrape");

    # or import (ECMAScript Module)
    import { Noscrape } from "noscrape";

    const noscrape = new Noscrape("path/to/font.ttf");

## <br> Obfuscation

Obfuscate your text by calling the obfuscate method on your *noscrape* instance. This will convert your text into a
series of unique characters from the Private Use Area (PUA) of Unicode, making it unreadable by standard means:

    const obfuscatedText = noscrape.obfuscate("text to obfuscate");

    console.log(obfuscatedText);
    > 


    // one could also obfuscate an integer
    obfuscatedInt = noscrape.obfuscate(1337);


    // or an array
    obfuscatedArray = noscrape.obfuscate({
        test: "This is a Test",
        another: {
            test: "This is another Test",
        }
    });

## <br> Rendering

Render the obfuscated font into a Base64-encoded string using the render method. This encoded string can then be
embedded directly into your HTML for easy use:

    const b64Font = noscrape.render();

    console.log(obfuscatedText.toString("base64");
    > T1RUTwAJAIAAAwAQQ0ZGIIaTIyUAAAVkAAARe09TLzL4TxrlAAABAAAAAGBjbWFwACT...

## <br> Putting it together

Combine everything into a complete HTML document. Embed the Base64-encoded font directly in your HTML using the
@font-face rule and apply the obfuscated font to your text with CSS. This ensures that the obfuscated text is displayed
correctly in the browser:

    <html lang="en">
    <head>
        <title>Noscrape - DEMO</title>
        <style>
            @font-face {
                font-family: 'noscrape-obfuscated';
                src: url('data:font/truetype;charset=utf-8;base64,${font.toString("base64")}');
            }
        </style>
    </head>
    <body>
        <div style="font-family: 'noscrape-obfuscated'">${obfuscated}</div>
    </body>
    </html>

## <br> Running Example


    $ git clone git@github.com:noscrape/noscrape-node-example.git
    $ cd noscrape-node-example
    $ npm install
    $ node src/index.js

open [http://localhost:1234](http://localhost:1234)
