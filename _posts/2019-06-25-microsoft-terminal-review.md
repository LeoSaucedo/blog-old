---
title: "Exploring the New Microsoft Terminal"
header:
  image: /assets/images/ms-terminal-ubuntu.png
  image-alt: "The summer's hottest new programming tool is here."
date: 2019-06-25
toc: true
toc_label: "Table of Contents"
toc_icon: "list-alt"
categories:
  - Hot Take
tags:
  - Windows Terminal
  - Microsoft
  - Ubuntu
---

It's officially summertime, and with that comes the hottest-anticipated programming product for Windows users: the Windows Terminal! In this post, I'll be running through my quick thoughts about it, and how it will be affecting my programming workflow, as well as the specific settings that I modified it to give it the "Carlos Way" touch.

# Preface

The Windows Terminal is still in early alpha, and many of its features will be changing. This is definitely not anything near what the final product will look like, and shouldn't be your final judgement on whether you should be using it or not. However, it does provide a good insight into what your workflow might look like if you end up using it, so it's still worth a look!

# Interface

![](/assets/images/ms-terminal-cmd.png)
<i style="font-size:smaller">The Windows Terminal with an active CMD tab.</i>

I'm actually quite pleased with how the terminal looks. Aside from a couple of design discrepancies, in my own opinion, the Windows Terminal is a _huge_ improvement over the traditional command prompt, and has some impressive theming options that bring it to the 21st century. It has an optional, customizable transparency setting, which, just like the new Calculator app, glosses over the contents behind it in a sleek, modern style. It also has a nice, tabbed interface that reminds me more of a Google Chrome dark theme than a terminal interface. It has the ability to display emoji, and has hyperlinks you can click on, like the terminal in VSCode.

## Tabs

One of the most acclaimed new features of the Windows Terminal, the tabbed interface is just that - the ability to have more than one instance within a Windows Terminal window. Unlike other terminal programs for Windows and Unix, however, the Windows Terminal allows tabs of different environments and operating systems within one window, a new feature I will be using greatly.

When you click on the new tab button, a new tab from the default profile appears, but if you want to open a tab in another profile, you can select it from the dropdown button right next to it:

<div style="text-align:center"><img src="/assets/images/ms-terminal-selector.png" /></div>
<i style="font-size:smaller">The tabs selector is fully customizable with profiles in the settings menu.</i>

Every aspect of these dropdown options is able to be customized, from the titles and icons to the precise shell they are running. Your existing shells, both WSL and Microsoft, should be automatically populated, but they are easy to add if for some reason they have not been.

## Customization

In my opinion, the customization process is probably what needs the most work so far. However, much to the style of Visual Studio Code, almost everything about the Windows Terminal can be customized. When clicking on the settings button in the dropdown, as shown above, you are met with a Visual Studio Code instance of the `JSON` settings file, and can edit it just as you would any other text file:

<div style="text-align:center"><img src="/assets/images/ms-terminal-settings.png" /></div>
<i style="font-size:smaller">The settings dialogue.</i>

While more hardened programmers will find this a possible positive change, more casual terminal users might find this slightly difficult to work with, especially those not so familiar with JSON. For my purposes, VSCode with a [Color Info Plugin](https://marketplace.visualstudio.com/items?itemName=bierner.color-info) did an amazing job at letting me adjust theming and organize everything the way I needed it to. When opening the JSON file, your first relevant find will be all of the keybindings. I chose to leave them be for the time being, but it's good to know that they're all completely modular. Second, the list of profiles defines what kinds of tabs you can open:

### Profiles

Profiles should be initially generated for you when you first install and run Windows Terminal. However, if you ever need to edit them to fit your specific needs - I adjusted the `fontSize`, `cursorShape`, and `colorScheme` to a custom scheme I created just for my Ubuntu instance, which you'll see below. The settings are pretty self explanatory, but if you don't know what you're doing you probably don't want to be prodding around and accidentally break your terminal.

When designing my Ubuntu profile, I was aiming for making it as similar to the Ubuntu Unity color scheme, with a little bit of transparency for an added touch of modernity.

Here's my final adjusted Ubuntu profile:

```json
"profiles" :
[
    {
        "acrylicOpacity" : 0.75,
        "closeOnExit" : true,
        "colorScheme" : "Ubuntu",
        "commandline" : "wsl.exe -d Ubuntu-18.04",
        "cursorColor" : "#DCDFE4",
        "cursorShape" : "filledBox",
        "fontFace" : "Ubuntu Mono",
        "fontSize" : 16,
        "guid" : "{c6eaf9f4-32a7-5fdc-b5cf-066e8a4b1e40}",
        "historySize" : 9001,
        "icon" : "ms-appx:///ProfileIcons/{9acb9455-ca41-5af7-950f-6bca1bc9722f}.png",
        "name" : "Ubuntu-18.04",
        "padding" : "0, 0, 0, 0",
        "snapOnInput" : true,
        "useAcrylic" : true
    }
]
```

### Themes

Themes are also one of the hottest features new to the Windows Terminal. While the antiquated Command Prompt did have some limited theming options, I always found it underwhelming and lacking in color displays. However, since it was so ingrained into my Windows instance, there was no choice but to use it - and I had to resort to flimsy

If you want a profile to use with your Ubuntu instance, here are the settings I adapted from the [internet](https://medium.com/@jgarijogarde/make-bash-on-ubuntu-on-windows-10-look-like-the-ubuntu-terminal-f7566008c5c2):

```json
"schemes": [
  {
      "background" : "#300A24",
      "black" : "#0C0C0C",
      "blue" : "#729FCF",
      "brightBlack" : "#555753",
      "brightBlue" : "#61AFEF",
      "brightCyan" : "#34E2E2",
      "brightGreen" : "#8AE234",
      "brightPurple" : "#AD7FA8",
      "brightRed" : "#EF2929",
      "brightWhite" : "#D3D7D9",
      "brightYellow" : "#FCE94F",
      "cyan" : "#06989A",
      "foreground" : "#EEEEEE",
      "green" : "#4E9A06",
      "name" : "Ubuntu",
      "purple" : "#AD7FA8",
      "red" : "#CC0000",
      "white" : "#DCDFE4",
      "yellow" : "#C4A000"
  }
]
```

# Performance

Because this is a pre-alpha release, I found several bugs that were quite finnicky and caused things to crash. Every time I closed all of the tabs in the terminal, a clear window would hang for several seconds before finally closing. Only the small white section in the top right allowed the window to be properly dragged as well, which gets a lot more irritating than you think after a while. The app would stop responding ever time I closed a PowerShell session, forcing me to lose all of my progress made in the other tabs of the window. And miscellaneously, I would experience flickers on the window and slow minmization, maximization, resizing, and moving of the windows. I truly would not recommend you to use Windows Terminal as your main terminal emulator just yet, but since it will be an Open Source Windows product, I'm confident that it will eventually become just as stable as your old-school CMD. That's the struggles of being a bleeding-edge early adopter, however, and we sign up for this!

# Conclusion

The Windows Terminal is definitely something I'm going to have to keep an eye on. I'm already using it little by little in my less important projects, and just to pull up `htop` on my VPS instances to make sure that everything is running smoothly. My go-to for programming is still the VSCode terminal, but since that can't pop out or be opened in a new window, it is still fairly difficult to integrate to a multi-monitor workflow. Thanks for reading, and happy coding!
