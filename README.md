# Weeks-7-8-Project-WordPress-vs.-Kali
Cybersecurity_Codepath assignment for Week 7 &amp; 8

# Project 7 - WordPress Pentesting

Time spent: **10** hours spent in total

> Objective: Find, analyze, recreate, and document **vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. WordPress <= 4.2 - Unauthenticated Stored Cross-Site Scripting (XSS)
  - [ ] Summary: 
   Version 4.2 of WordPress is vulnerable to a stored XSS. We can inject HTML code in the comment section if our text is long enough. for this vulnerability the text was supposed to be at least 64k which is 64000 characters. HTML is triggered once the text is detected to be long enough and the message box is displayed.  
    - Vulnerability types: XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.1
  - [ ] GIF Walkthrough: [Image_1] https://github.com/alfarozavalae/Weeks-7-8-Project-WordPress-vs.-Kali/blob/master/1.gif
  - [ ] Steps to recreate: 
  Open wpdistillery and post a comment as a user. in the comment section add: <a title='x onmouseover=alert(unescape(/hello%20world/.source)) style=position:absolute;left:0;top:0;width:5000px;height:5000px  AAAAAAAAAAAA...[64 kb]..AAA'></a> replaing the ...[64 kb].. with more characters that add up to at least 64k. 
    - [ ] Affected source code:
    - [Link 1] https://core.trac.wordpress.org/browser/branches/4.2/src/wp-admin/post-new.php
    
2. Authenticated Stored Cross-Site Scripting via Image Filename
  - [ ] Summary: 
  This is a Cross-site scripting XSS vulnerability that opens a window if uploaded to wordpress in the title part. According to what I read, WordPress performs insufficient validation 
  
  on the file name of uploaded media types and in specific images. The file name of an image is used as image Title (meta) in so called ‘attachment pages’ (HTML). An attacker can exploit this vulnerability by crafting an image file name with Cross-Site Scripting payload and lure an admin into uploading the image with the malicious file name. 
  
    - Vulnerability types: XSS 
    - Tested in version: 4.2
    - Fixed in version: 4.2.10
  - [ ] GIF Walkthrough: [Image_2] https://github.com/alfarozavalae/Weeks-7-8-Project-WordPress-vs.-Kali/blob/master/2.gif
  - [ ] Steps to recreate: 
  Open Word Press and upload the an image with the name cengizhansahinsumofpwn<img src=a onerror=alert(document.cookie)>.jpg afterwards, create a new post or page and paste cengizhansahinsumofpwn<img src=a onerror=alert(document.cookie)>.jpg as the title. 
  
  - [ ] Affected source code:
    - [Link 2] https://core.trac.wordpress.org/browser/branches/4.2/src/wp-admin/post-new.php
    
    
3. Authenticated Cross-Site Scripting (XSS) via Media File Metadata
  - [ ] Summary: 
  The audio playlist functionality of WordPress is affected by Cross-site scripting. It has been discovered that there are two vulnerabilities in it. Once the files are uploaded if they are added to posts or pages they trigger two windows popping up. 
  
    - Vulnerability types: XSS
    - Tested in version: 4.2  
    - Fixed in version: 4.2.13
  - [ ] GIF Walkthrough: [Image_3] https://github.com/alfarozavalae/Weeks-7-8-Project-WordPress-vs.-Kali/blob/master/3.gif
  - [ ] Steps to recreate: 
  Create a file with the name /advisory/SFY20160742/xss or download the one available at https://sumofpwn.nl/advisory/2016/wordpress_audio_playlist_functionality_is_affected_by_cross_site_scripting.html. procede to upload it into the media files in Wordpress and add it to a post or page. 
     
    
    
4. Authenticated Stored Cross-Site Scripting (XSS) in YouTube URL Embeds
  - [ ] Summary: 
  This is another vulnerability where JavaScript code can be executed through an embedded youtube URL.
    - Vulnerability types:XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.13
  - [ ] GIF Walkthrough: [Image_4] https://github.com/alfarozavalae/Weeks-7-8-Project-WordPress-vs.-Kali/blob/master/4.gif
  - [ ] Steps to recreate: 
  With the walkthrough steps from the vlunerability link https://blog.sucuri.net/2017/03/stored-xss-in-wordpress-core.html crete your own youtube embedded code to add it in the content section of a post in WordPress.
  - [ ] Affected source code:
    - [Link 4] https://github.com/WordPress/WordPress/commit/419c8d97ce8df7d5004ee0b566bc5e095f0a6ca8


## Assets

List any additional assets, such as scripts or files

## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).


## License

    Copyright [2019] [Elaheh Jamali]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
