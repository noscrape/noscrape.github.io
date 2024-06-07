---
title: 'Noscrape NodeJS'
repo_url: 'https://github.com/noscrape/noscrape-node'
---
# Noscrape - Python

Noscrape is a Python library that protects your web content from scraping. It uses true-type fonts with shuffled unicodes to obfuscate text, making it unreadable by standard methods while still displaying correctly in browsers. This tool helps developers secure their websites from data harvesting and unauthorized scraping.

<br>

##  Installation

To begin, install the *noscrape* library using `pip`:
```shell
pip install noscrape
```

## <br> New Instance

Create a new instance of the *noscrape* class by providing the path to your desired font file. This sets up *noscrape*
to use the specified font for obfuscating text:
``` python
from noscrape import Noscrape

noscrape_instance = Noscrape("/path/to/font.ttf")
```

## <br> Obfuscation

Obfuscate your text by calling the obfuscate method on your *noscrape* instance. This will convert your text into a
series of unique characters from the Private Use Area (PUA) of Unicode, making it unreadable by standard means:
``` python
text = noscrape.obfuscate("text to obfuscate")
print(text)
# 

# one could also obfuscate an integer
obfuscatedInt = noscrape.obfuscate(1337)

# or an list
input_list = ["text1", 1234, "this is the output", 5678]
obfuscated_list = noscrape.obfuscate(input_list)
print("%s" % json.dumps(obfuscated_list, ensure_ascii=False))
# ["", "", "", ""]
```

## <br> Rendering

Render the obfuscated font into a Base64-encoded string using the render method. This encoded string can then be
embedded directly into your HTML for easy use:
``` python
b64_font = noscrape.render()
print(b64_font)

# T1RUTwAJAIAAAwAQQ0ZGIIaTIyUAAAVkAAARe09TLzL4TxrlAAABAAAAAGBjbWFwACT...
```

## <br> Putting it together

Combine everything into a complete HTML document. Embed the Base64-encoded font directly in your HTML using the
@font-face rule and apply the obfuscated font to your text with CSS. This ensures that the obfuscated text is displayed
correctly in the browser:
``` html
<html lang="en">
<head>
    <title>Noscrape - DEMO</title>
    <style>
        @font-face {
            font-family: 'noscrape-obfuscated';
            src: url('data:font/truetype;charset=utf-8;base64,{{b64_font}}');
        }
    </style>
</head>
<body>
    <div style="font-family: 'noscrape-obfuscated'">{{obfuscated_text}}</div>
</body>
</html>
```

