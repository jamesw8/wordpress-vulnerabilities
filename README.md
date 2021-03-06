# Project 7 - WordPress Pentesting

Time spent: **6** hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. (Required) WordPress <= 4.3 - Authenticated Shortcode Tags Cross-Site Scripting (XSS)
  - [ ] Summary: Shortcodes, which are alternative HTML tags that render macro content, can be used to inject JavaScript by leaving an attribute open so that it can be closed with the malicious script that appends another attribute containing the JavaScript.
    - Vulnerability types: Stored XSS
    - Tested in version: 4.2
    - Fixed in version: 4.3.1
  - [ ] GIF Walkthrough: 
    - <img src="Cross-Site Scripting (XSS) via Shortcode.gif" width="800">
  - [ ] Steps to recreate:
    - Insert a shortcode where its attribute is an HTML tag with an attribute containing an unclosed quotation. Then, after the shortcode, insert another tag with an arbitrary attribute that "opens" a string which would close the shortcode quotation, and then append an attribute that would contain JavaScript code to be executed.
  - [ ] Affected source code:
    - [Link 1](https://github.com/WordPress/WordPress/commit/f72b21af23da6b6d54208e5c1d65ececdaa109c8)
2. (Required) WordPress  4.0-4.7.2 - Authenticated Stored Cross-Site Scripting (XSS) in YouTube URL Embeds
  - [ ] Summary: Escape sequences can be used in an embedded YouTube URL to execute JavaScript.
    - Vulnerability types: Stored XSS
    - Tested in version: 4.2
    - Fixed in version: 4.7.3
  - [ ] GIF Walkthrough: 
    - <img src="Cross-Site Scripting via YouTube URL.gif" width="800">
  - [ ] Steps to recreate: 
    - Insert an embedded YouTube URL where the URL includes an svg tag with a JavaScript event handler by escaping anything that will be sanitized with regex.
  - [ ] Affected source code:
    - [Link 1](https://github.com/WordPress/WordPress/commit/419c8d97ce8df7d5004ee0b566bc5e095f0a6ca8)
3. (Required) WordPress 3.6.0-4.7.2 - Authenticated Cross-Site Scripting (XSS) via Media File Metadata
  - [ ] Summary: Media File Metadata (ID3 Tags) can be used to inject JavaScript when they are inserted into an Audio Playlist. The playlist will show the metadata for each audio file which contains the html tag with the JavaScript code. The cause of this is unsanitized metadata.
    - Vulnerability types: Stored XSS
    - Tested in version: 4.2
    - Fixed in version: 4.7.3
  - [ ] GIF Walkthrough:
    - <img src="Authenticated Cross-Site Scripting (XSS) via Media File Metadata .gif" width="800">
  - [ ] Steps to recreate: 
    - Create an mp3 file along with metadata containing JavaScript. Create an Audio Playlist in a post and insert the mp3 media file. The metadata is not sanitized so it will execute the script when the post is viewed.
  - [ ] Affected source code:
    - [Link 1](https://github.com/WordPress/WordPress/commit/28f838ca3ee205b6f39cd2bf23eb4e5f52796bd7)
4. (Optional) WordPress 2.5-4.6 - Authenticated Stored Cross-Site Scripting via Image Filename
  - [ ] Summary: Uploaded image filenames aren't sanitized and can potentially allow an attacker to inject malicious JavaScript.
    - Vulnerability types: Stored XSS
    - Tested in version: 4.2
    - Fixed in version: 4.6.1
  - [ ] GIF Walkthrough: 
    - <img src="Cross-Site Scripting via Image Filename.gif" width="800">
  - [ ] Steps to recreate:
    - Insert an image tag with JavaScript as the title for an image and set to link to an attachment page. This would show the title when you click the image and execute the JavaScript code.
  - [ ] Affected source code:
    - [Link 1](https://github.com/WordPress/WordPress/commit/c9e60dab176635d4bfaaf431c0ea891e4726d6e0)
    
## Assets

List any additional assets, such as scripts or files

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Describe any challenges encountered while doing the work:
- Figuring out how to use WordPress when the posts had broken permalinks.

## License

    Copyright [2018] [James Wong]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
