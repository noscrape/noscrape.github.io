# Noscrape - PHP

## Installation
To begin, install the NoScrape library using Composer, which allows you to effortlessly manage your project's dependencies:

    $ composer require noscrape/noscrape

## New Instance
Create a new instance of the NoScrape class by providing the path to your desired font file. This sets up NoScrape to use the specified font for obfuscating text:
    
    $noscrape = new Noscrape("path/to/font.ttf");

## Obfuscation
Obfuscate your text by calling the obfuscate method on your NoScrape instance. This will convert your text into a series of unique characters from the Private Use Area (PUA) of Unicode, making it unreadable by standard means:
    
    $obfuscatedText = $noscrape->obfuscate("text to obfuscate");

    echo $obfuscatedText;
    > 




    // one could also obfuscate an integer
    $obfuscatedInt = $noscrape->obfuscate(1337);




    // or an array
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



## Rendering
Render the obfuscated font into a Base64-encoded string using the render method. This encoded string can then be embedded directly into your HTML for easy use:
    
    $b64Font = $noscrape->render();

    echo $b64Font;
    > T1RUTwAJAIAAAwAQQ0ZGIIaTIyUAAAVkAAARe09TLzL4TxrlAAABAAAAAGBjbWFwACT...

## Putting it together
Combine everything into a complete HTML document. Embed the Base64-encoded font directly in your HTML using the @font-face rule and apply the obfuscated font to your text with CSS. This ensures that the obfuscated text is displayed correctly in the browser:
    
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

## Laravel Example

    Route::get('/', function () {
        $noscrape = new Noscrape(public_path("font/anyfont.ttf"));
    
        return view('welcome', [
            'title' => $noscrape->obfuscate("Welcome to Noscrape"),
            'description' => $noscrape->obfuscate("This is text is obfuscated."),
            'font' => $noscrape->render()
        ]);
    });
