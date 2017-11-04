# LU_Week7Project_WordPress_Kali
Vulnerabilities in WordPress 4.2

# Project 7 - WordPress Pentesting

Time spent: **3** hours spent in total

> Objective: Find, analyze, recreate, and document **three vulnerabilities** (5 is optional) affecting an old version of WordPress

## Pentesting Report

1. WordPress 2.5-4.6 - Authenticated Stored Cross-Site Scripting via Image Filename
  - [X] Summary: An attacker can inject JavaScript code into the application via upload of an image onto WordPress.
    - Vulnerability types: XXS
    - Tested in version: 4.2
    - Fixed in version: 4.2.10
  - [X] GIF Walkthrough: <img src='https://imgur.com/yDcjSOu.gif' />
  - [X] Steps to recreate:
    - Save an image with the file name such as:
        NameFile\<img src=a onerror=alert(document.cookie)>.jpg     
    - Upload the image as an admin to WordPress & open the attachment page
  - [X] Affected source code:
    - [Link 1](https://github.com/WordPress/WordPress/commit/c9e60dab176635d4bfaaf431c0ea891e4726d6e0)

2. WordPress 4.2.2 - Authenticated Stored Cross-Site Scripting (XSS)
  - [X] Summary: An attacker with a contributor or author level account can insert specially formatted HTML containing JavaScript on a WordPress page or post.
    - Vulnerability types: XXS
    - Tested in version: 4.2
    - Fixed in version: 4.2.3
  - [X] GIF Walkthrough: <img src='https://i.imgur.com/TUtTsXG.gif' />
  - [X] Steps to recreate:
    - Log onto a contributor or author level account. Create a post in html with the content of: 
        \<a href = "[caption code=">"]</a><a title=" onmouseover=alert('test') ">link</a>
    - Log onto administrator account and view the post
  - [X] Affected source code:
    - [Link 1](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/class-wp-embed.php?rev=33359)
3. WordPress 3.3-4.7.4 - Large File Upload Error XSS
  - [X] Summary: An attacker can inject malicious script into the filename of a video as an administrator.
    - Vulnerability types: XXS
    - Tested in version: 4.2
    - Fixed in version: 4.2.15
  - [X] GIF Walkthrough: <img src='https://i.imgur.com/l8O5Ioa.gif' />
  - [X] Steps to recreate:
    - Create a file larger than 2 MB (the maximum upload size) with the file name such as: 
        NameFile<img src=x onerror=alert('boo')>.jpg
    - Upload the video as an admin to WordPress Media
  - [X] Affected source code:
    - [Link 1](https://github.com/WordPress/WordPress/commit/8c7ea71edbbffca5d9766b7bea7c7f3722ffafa6)

## Assets

List any additional assets, such as scripts or files

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Describe any challenges encountered while doing the work

1) Finding good resources describing the vulnerabilities and examples
2) Although the IP stated was 127.0.53.53 when wpdistillery.dev was pinged, it was actually 192.168.33.10.
3) The hostname I found worked for me was not wpdistillery.dev but wpdistillery.local.

## License

    Copyright [2017] [Kelly Lu]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
