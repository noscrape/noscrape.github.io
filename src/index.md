# Welcome to noscrape Documentation

Welcome to the official documentation for **noscrape**! This guide will help you understand the concept, usage, and benefits of integrating noscrape into your projects.

## Concept

The primary mechanism behind noscrape is the utilization of any true-type font. Noscrape generates a new version with shuffled unicodes, ensuring that it's impossible to reverse-calculate them. This means that both strings and integers are obfuscated and can only be deciphered using the generated obfuscation-font.

While the glyph-paths inside the font cannot be entirely removed, they are obfuscated by randomly shifting them slightly. This makes it challenging to reverse-calculate them, though not entirely impossible, especially for machine learning algorithms. We are open to suggestions for improving this aspect.

## Use-Cases

In an era where artificial intelligence is becoming increasingly integral to our daily lives, it's important to remember that AI thrives on data, and your data is a valuable commodity that shouldn't be given away lightly. Here are some key use-cases for noscrape:

### Anti-Scraping Measures for Websites

Implement noscrape on your website to protect against web scrapers. This can be particularly useful for content that is unique to your site, which you wish to prevent from being copied or used without permission. Examples include:

- Sport results
- Betting results
- Prices (e-commerce)
- Geo-information

### Protecting Sensitive Data

Use noscrape to obfuscate sensitive information such as personal identifiers, financial details, or confidential text in a way that is visually accessible but protected against scraping and automated data extraction tools.

### Reduce Bot Interactions

Once your data is protected by noscrape, it makes no sense for scrapers to target it, thereby reducing the number of bot interactions and lowering associated costs.

### Secure Applications

In applications where data security is paramount, such as in banking or healthcare apps, noscrape can be used to display information in a secure manner. Examples include:

- PIN/TAN numbers
- Bot protection (captcha)



## Language Implementations

- [Java Implementation](java.md)
- [PHP Implementation](php.md)
- [NodeJS/TypeScript Implementation](node.md)

## Platform Implementation

**noscrape** is not implemented directly in every programming language. Instead, it utilizes platform-specific binaries to achieve its functionality. These binaries include:

- `noscrape_darwin_arm64`
- `noscrape_darwin_x86_64`
- `noscrape_linux_arm64`
- `noscrape_linux_x86_64`
- `noscrape_windows_x86_64.exe`

These binaries serve as the core engine of **noscrape**, handling the generation of obfuscated text using true-type fonts with shuffled unicodes. They are compiled to run efficiently on specific operating systems and architectures.

**Note:** If you require **noscrape** for a different operating system or architecture combination, please open a GitHub issue, and we'll work on providing support for it.

## Wrapper Implementations

The implementations provided in languages such as PHP, Java, and Node.js act as wrappers for these binaries. Their main purpose is to facilitate communication with the **noscrape** binaries, providing them with the necessary inputs and configurations to generate obfuscated text.

These wrapper implementations handle tasks such as:

- Collecting input data from the application or user.
- Calling the appropriate **noscrape** binary based on the host platform.
- Passing the input data to the **noscrape** binary for obfuscation.
- Returning the obfuscated text or other outputs back to the application.

By utilizing wrappers, **noscrape** can seamlessly integrate with a wide range of programming languages and environments while maintaining its core functionality across different platforms.

## Where NOT to Use Noscrape

While Noscrape provides a powerful tool for obfuscating text and protecting sensitive information, it's essential to understand its limitations and use it judiciously. Here are some scenarios where using Noscrape might not be appropriate:

### Search Engine Optimization (SEO)

Noscrape renders text as images or obfuscated characters, making it unreadable by search engine crawlers. As a result, content obfuscated with Noscrape may not be indexed by search engines like Google, Bing, or Yahoo. This can negatively impact your website's search engine rankings and visibility.

### Accessibility

Obfuscated text can pose accessibility challenges for users with visual impairments or those using assistive technologies such as screen readers. Screen readers rely on text to provide auditory feedback, and obfuscated text may be unintelligible or completely inaccessible to these users.

### Legal Compliance

Using Noscrape to obfuscate legally required information, such as terms of service, privacy policies, or compliance notices, may violate regulatory requirements or legal obligations. Ensure that obfuscating such information complies with applicable laws and regulations in your jurisdiction.

### User Experience (UX)

Obfuscated text can degrade the user experience, especially when used for essential content such as navigation menus, form labels, or instructional text. Users may find it difficult to understand or interact with obfuscated content, leading to frustration and dissatisfaction.

### Warranty and Liability

Noscrape is provided as-is, without warranties or guarantees of any kind. While it can help protect sensitive information, misuse or improper implementation of Noscrape may lead to unintended consequences or security vulnerabilities. We cannot accept liability for any damages, losses, or legal issues arising from the use of Noscrape.

Before using Noscrape, carefully consider the implications and limitations outlined above. Use Noscrape responsibly and in accordance with best practices for web development and security.

---

Let's make the web a safer place with noscrape!
