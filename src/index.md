---
title: Noscrape Introduction
summary: A Description about how noscrape works and how it could help you to secure your content from scraping
authors:
  - Bernhard Schönberger
date: 2024-06-06
noscrape_url: https://github.com/noscrape
---

# Welcome to *noscrape*

Welcome to the official documentation for *noscrape*! This guide will help you understand the concept, usage, and benefits of integrating noscrape into your projects.

## Concept

The primary mechanism behind *noscrape* is the utilization of any true-type font. *Noscrape* generates a new version with shuffled unicodes, ensuring that it's impossible to reverse-calculate them. This means that both strings and integers are obfuscated and can only be deciphered using the generated obfuscation-font.

While the glyph-paths inside the font cannot be entirely removed, they are obfuscated by randomly shifting them slightly. This makes it challenging to reverse-calculate them, though not entirely impossible, especially for machine learning algorithms. We are open to suggestions for improving this aspect.

``` mermaid
sequenceDiagram
    participant User
    participant Server
    participant Noscrape

    User->>Server: Send Request
    Server->>Noscrape: Initialize noscrape
    Server->>Noscrape: obfuscatedText1 = noscrape.obfuscate("text to obfuscate")
    Server->>Noscrape: obfuscatedText2 = noscrape.obfuscate("another textblock")
    Noscrape-->>Server: Return Obfuscated Text
    Server->>Noscrape: font = noscrape.render()
    Noscrape-->>Server: Return Generated Font
    Server->>User: Send HTML Response with Obfuscated Text and Embedded Font
```


## <br /> Platform Implementation

*noscrape* is not implemented directly in every programming language. Instead, it utilizes platform-specific binaries to achieve its functionality. These binaries include:

- `noscrape_darwin_arm64`
- `noscrape_darwin_x86_64`
- `noscrape_linux_arm64`
- `noscrape_linux_x86_64`
- `noscrape_windows_x86_64.exe`

These binaries serve as the core engine of *noscrape*,
handling the generation of obfuscated text using true-type fonts with shuffled unicodes.
They are compiled to run efficiently on specific operating systems and architectures.

**Note:** If you require *noscrape* for a different operating system or architecture combination, please open a GitHub issue, and we'll work on providing support for it.

## Wrapper Implementations

The implementations provided in languages such as PHP, Java, and Node.js act as wrappers for these binaries. Their main purpose is to facilitate communication with the *noscrape* binaries, providing them with the necessary inputs and configurations to generate obfuscated text.

These wrapper implementations handle tasks such as:

- Collecting input data from the application or user.
- Calling the appropriate *noscrape* binary based on the host platform.
- Passing the input data to the *noscrape* binary for obfuscation.
- Returning the obfuscated text or other outputs back to the application.

By utilizing wrappers, *noscrape* can seamlessly integrate with a wide range of programming languages and environments while maintaining its core functionality across different platforms.

---

Let's make the web a safer place with *noscrape*!
