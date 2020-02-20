---
title: "My Summer Internship Experience at CPS Products, Inc."
header:
  image: /assets/images/cps-logo.png
date: 2019-08-25
categories:
  - Career
  - Hot Take
tags:
  - JavaScript
  - TypeScript
  - Ionic
  - WordPress
  - Coding
---

This summer, I was an Engineering/Web Intern at CPS Products, Inc. Throughout my internship, I learned and refined lots of skills that I'll be taking back and using in my career for years to come. The internship encompassed many different categories, including Web Development/WordPress Management, Software/Mobile App Development, Competitive Analysis and Research, and more. Over the course of the internship, I discovered TypeScript and added it to my skillset, and was able to refine and modernize my Apache Cordova experience with the newer Ionic framework, and was able to apply my skills to create a production-grade application that's in the works of being deployed today. Additionally, with some of the knowledge I amassed throughout the internship, I was able to develop a standalone app that allows you to communicate with a BLE (Bluetooth Low Energy), device as a terminal. I also learned some helpful tools to optimize a WordPress Website, and even managed to increase PageSpeed Insights by more than 50 points on several sites.

## Ionic and the Future of App Development

![](/assets/images/ionic-title.jpg)
<i style="font-size:smaller">Ionic has become my favorite tool for quickly creating desktop, web, and mobile apps beautifully and efficiently.</i>

One of the most impactful technologies I learned throughout the internship was Ionic, the new app development framework. I had some previous experience with Apache Cordova throughout my last internship, but overall, pure Cordova felt a bit dated and clunky. Ionic also has the advantage of having an incredible CLI, which allowed me to create projects, add components to my projects, generate resources such as splash screens and app icons, and compile and run on an emulator or connected device. Additionally, Ionic uses TypeScript and Angular by default, both of which I had to learn in order to create the apps I did this summer. Ionic is my favorite method to creating apps because it allows you to use web-heavy development to produce Native code on Android, iOS, and more. This summer I was assigned the task of developing an application that interfaces with BLE devices and sends and receives information that is gained from the sensors onboard the various Bluetooth Devices CPS Products uses.

<img width="300px" src="/assets/images/bluetooth-terminal.jpg" style="display: block; margin: 0 auto">
<i style="font-size:smaller">My Bluetooth Terminal app running on Android.</i>

In order to learn the workflow of creating Ionic applications and handling BLE devices, I created a separate [BLE Terminal](https://github.com/LeoSaucedo/BluetoothTerminal) on my own time that actually became a really powerful tool I was able to use to test the subsequent apps I was developing. Though simple, the Terminal app proved to be extremely useful, and allows both sending and receiving of ASCII text to and from a BLE device with an optionally adjustable characteristic and service UUID sets. Learning how BLE works and applying it to my existing code was one of the most difficult tasks I had to undertake while on this internship, but once I was able to create a base class in TypeScript that performed all of the Bluetooth Functions, I was set.

I ended up using Apache Cordova instead of the newer capacitor, because of my previous experience with Cordova and because of the increased plugin support. This ended up being just as efficient though, especially when creating an application with heavy third-party plugin requirements.

## Making WordPress More Efficient

<img src="https://cdn4.wpbeginner.com/wp-content/uploads/2019/02/wpspeedupguide.png" style="display: block; margin: 0 auto">
<i style="font-size:smaller">
<a href="https://www.wpbeginner.com/wordpress-performance-speed/">Source</a>
</i>

Another one of the useful takeaways from the internship was being able to learn some effective steps to make any WordPress site more efficient, through things such as [WP Super Cache](https://wordpress.org/plugins/wp-super-cache/), [Autoptimize](https://wordpress.org/plugins/autoptimize/), and using CDNs. Though I'd had previous experience managing WordPress websites, page speed wasn't ever a priority, but I was able to really focus on it during this internship and was able to improve the [PageSpeed Insight Score](https://developers.google.com/speed/pagespeed/insights/) of all 3 CPS Products websites by 50 points or more.

Another really important procedure I was able to develop was a workflow to automatically make uploaded images be resized, compressed, and served through a CDN instead of through the website itself. This dramatically increased website speeds and was by far the biggest improvement to the PageSpeed Insight Score. In the future, I hope to take this knowledge and be able to apply it to the improvement of many WordPress sites, especially those with high traffic that depend on low latency.

## Competitive Analysis for Research and Development

The last big contribution I was able to make to the team, though not quite related to Software Engineering, was working with the Research and Development as well as the Marketing and Sales teams in order to conduct competitive analyses for different products that were in the pipeline for release or were being considered for development. This was an interesting insight on how similar companies compete to gain an improving market share, and provided lots of information on the HVAC/R industry as well as general business knowledge that gave me more information on how different sectors of a company I'm not traditinally working with directly operate and function, as well as integrate with engineering teams I tend to be more often a part of.

## Conclusion

Over the summer, I did a wide variety of things and was able to dramatically improve my Software Engineer experience as well as my overall business fluency in an entirely new industry. I'm extremely thankful to CPS for having provided me this opportunity, and look forward to seeing where the experience I've gained takes me!
