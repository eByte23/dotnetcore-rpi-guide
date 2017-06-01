# dotnetcore-rpi-guide
How to run dotnet core on a raspberry pi

All info found here https://github.com/dotnet/core/blob/master/samples/RaspberryPiInstructions.md

### RaspberryPi Pre-req
```sudo apt-get install -y libunwind8 libunwind8-dev gettext libicu-dev liblttng-ust-dev liblttng-ust-dev libcurl4-openssl-dev libssl-dev uuid-dev unzip```


### Note: Currently only Raspbery Pi 2 & 3 are supported
It seems as though currently the pi 1 and pi zero's are unsupported due to the absense of hardware floating point.

### SDK: Not there yet
Currently there is not sdk support for 32bit arm. What does this actually mean? It means that there is no Cli and ability to build .net apps directly on the pi.
However you can build and publish on any other platform targeting your application for ```linux-arm```!

### How to get started

To get started download the latest version or .Net Core 2.0 (currently in preview) here https://www.microsoft.com/net/core/preview#windowscmd or https://github.com/dotnet/core/blob/master/release-notes/download-archives/2.0.0-preview1-download.md

Once you have install this you can now go ahead and either re-target your current .net core app or create a new one.

Lets create a ```Hello World``` ConsoleApp
Create a new folder and run the command in a command prompt ```dotnet new console```
This will create you a fresh dotnet core app.
You will now need to change your csproj to target linux-arm

You need to add or modify the ```RuntimeIdentifiers``` Tag
your csproj may look similar to this

```
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.0</TargetFramework>
    <RuntimeIdentifiers>win7-x64;win-arm;linux-arm</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```
