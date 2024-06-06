---
title: Noscrape PHP
repo_url: https://github.com/noscrape/noscrape-php
---

# Noscrape - PHP

## <br> Installation

To begin, install the *noscrape* library using Composer, which allows you to effortlessly manage your project's
dependencies:
``` shell
$ composer require noscrape/noscrape
```

## <br> New Instance

Create a new instance of the *noscrape* class by providing the path to your desired font file. This sets up *noscrape*
to use the specified font for obfuscating text:
```php 
$noscrape = new Noscrape("path/to/font.ttf");
```

## <br> Obfuscation

Obfuscate your text by calling the obfuscate method on your *noscrape* instance. This will convert your text into a
series of unique characters from the Private Use Area (PUA) of Unicode, making it unreadable by standard means.


##### <br /> obfuscate text
```php 
    $obfuscatedText = $noscrape->obfuscate("text to obfuscate");

    echo $obfuscatedText;
    > 
```


##### <br /> obfuscate a number
```php 
    $obfuscatedInt = $noscrape->obfuscate(1337);
```


##### <br /> obfuscate an array
```php 
    $obfuscatedArray = $noscrape->obfuscate([
        "test" => "This is a Test",
        "another" => [
            "test" => "This is another Test",
        ]
    ]);
    /*
    [
        "test" => "",
        "another" => [
            "test" => "",
        ]
    ]
    */
```

## <br> Rendering

Render the obfuscated font into a Base64-encoded string using the render method. This encoded string can then be
embedded directly into your HTML for easy use:

    $b64Font = $noscrape->render();

    echo $b64Font;
    > T1RUTwAJAIAAAwAQQ0ZGIIaTIyUAAAVkAAARe09TLzL4TxrlAAABAAAAAGBjbWFwACT...

## <br> Putting it together

Combine everything into a complete HTML document. Embed the Base64-encoded font directly in your HTML using the
@font-face rule and apply the obfuscated font to your text with CSS. This ensures that the obfuscated text is displayed
correctly in the browser:

    <!DOCTYPE html>
    <html lang="en">
    <head>
    <style>
        @font-face {
            font-family: 'noscrape-obfuscated';
            src: url("data:font/truetype;charset=utf-8;base64,{{ $font }}")
        }

        .obfuscated {
            font-family: "noscrape-obfuscated";
        }
    </style>
    </head>
    <body>
        <div class="obfuscated">{{ $obfuscatedText }}</div>
    </body>
    </html>

## <br> Laravel Example

In a Laravel application, you can easily integrate *noscrape* by creating a new instance of the *noscrape* class in your
controller or route. Use the public_path function to provide the path to your font file. Pass the obfuscated text and
font to your view:

    Route::get('/', function () {
        $noscrape = new Noscrape(public_path("font/anyfont.ttf"));

        return view('welcome', [
            'title' => $noscrape->obfuscate("Welcome to Noscrape"),
            'description' => $noscrape->obfuscate("This is text is obfuscated."),
            'font' => $noscrape->render()
        ]);
    });
