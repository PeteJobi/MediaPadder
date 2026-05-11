## Media Padder
This provides a reuseable WinUI 3 page with an interface that allows for padding the dimensions of videos and images. With this, you can do things like [letterboxing](https://www.merriam-webster.com/dictionary/letterboxing), or quickly giving an image a solid border. Only supports Windows 10 and 11 (not tested on other versions of Windows). Powered by FFMPEG.

<img width="1786" height="1075" alt="image" src="https://github.com/user-attachments/assets/7161a45f-c8bb-4f61-bc97-0480aa65d382" />

## How to build
You need to have at least .NET 9 runtime installed to build the software. Download the latest runtime [here](https://dotnet.microsoft.com/en-us/download). If you're not sure which one to download, try [.NET 9.0 Version 9.0.203](https://dotnet.microsoft.com/en-us/download/dotnet/thank-you/sdk-9.0.203-windows-x64-installer)

In the project folder, run the below
```
dotnet publish -c Release -p:Platform=x64 -p:WindowsAppSDKSelfContained=true -p:WindowsPackageType=None
```
When that completes, go to `\bin\Release\net<version>-windows\win-x64` and you'll find the **MediaPadder.exe**.

## Run without building
You can also just download the release builds if you don't wish to build manually. Unfortunately packages created in WinUI 3 have to be signed with a certificate, and certificates sourced from trusted companies cost hundreds of dollars. If you wish to install the package, you'll have to install a certificate signed by myself, as described [here](https://github.com/PeteJobi/MediaPadder/releases/tag/cert). You only need to do this once - future updates will not require different certificates.

## How to use
When you open the program, you will be prompted to upload a media file. Once that is done, you will be taken to the padder interface page. You are able to resize or move the input media within the padding space, which itself can be resized too. For better precision, you are able to manipulate coordinates/dimension numbers in the right panel. 

Also, by default, the media is locked to the center and the aspect ratio is maintained. Uncheck the "**Lock aspect ratio**" checkbox to resize the media freely. Dragging the media will uncheck the "**Lock to center**" checkbox, and checking it again will move it back to the center. The padding is set to a square aspect ratio by default. 

There are a bunch of aspect ratio presets you can set the padding to without having to manually resize. You can lock the aspect ratio of the padding as well, but note that switching to other aspect ratio presets won't work as expected while in this state.

You can set the colour of the padding to **Black**, **White**, **Grey** or an arbitrary colour by selecting the **Custom** option in the **Padding colour** options. If **Custom** is selected, enter a hex string (starting with a '#' and followed by 6 hexadecimal characters) that represents the desired colour into the **Custom colour** textbox that appears.

Right-clicking on the padding space or the input media provides you with a context menu of useful options.

Input menu options:
- **Move to**: This provides options to move the input to certain areas of the canvas quickly and with accuracy.
- **Match padding**: This provides options to match the input's width, height or both to that of the padding. This may be limited if the input's aspect ratio is locked.

Padding menu options:
- **Match content**: This provides options to match the padding's width, height or both to that of the input. This may be limited if the padding's aspect ratio is locked.

This app can also be used for re-scaling media to arbitrary dimensions without any padding. Setting the X and Y coordinates of the input to 0, and the input's size to match the padding size, eliminates the padding, and is equivalent to just scaling the media.

When you're satisfied with the positioning/dimensioning, click the **Pad** button to start the padding process. If you have a GPU, you can offload the processing to it for faster results, depending on your GPU's power, by ticking the **Hardware acceleration** checkbox (before starting the padding process).
