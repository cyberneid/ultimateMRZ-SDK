- [Pre-built binaries](#prebuilt)
- [Building](#building)
  - [Android](#building-android)
  - [iOS](#building-ios)
  - [Windows](#building-windows)
  - [Generic GCC](#building-generic-gcc)
  - [Raspberry Pi (Raspbian OS)](#building-rpi)
- [Testing](#testing)
  - [Usage](#testing-usage)
  - [Examples](#testing-examples)

This sample application validates MRZ fields (document number, birth date, expiry date...). The algorithm is explained at https://www.doubango.org/SDKs/mrz/docs/Data_validation.html.

This sample is standalone application with no dependencies.

<a name="prebuilt"></a>
# Pre-built binaries #

If you don't want to build this sample by yourself then, use the pre-built versions:
 - Windows: [validation.exe](../../../binaries/windows/x86_64/validation.exe) under [binaries/windows/x86_64](../../../binaries/windows/x86_64)
 - Linux: [validation](../../../binaries/linux/x86_64/validation) under [binaries/linux/x86_64](../../../binaries/linux/x86_64). Built on Ubuntu 18.
 - Raspberry Pi: [validation](../../../binaries/raspbian/armv7l/validation) under [binaries/raspbian/armv7l](../../../binaries/raspbian/armv7l)
 - Android: check [android](../../android) folder
 - iOS: check [ios](../../ios) folder
 
On **Windows**, the easiest way to try this sample is to navigate to [binaries/windows/x86_64](../../../binaries/windows/x86_64/) and run [binaries/windows/x86_64/validation.bat](../../../binaries/windows/x86_64/validation.bat). You can edit this file to use your own txt file and configuration options.

<a name="building"></a>
# Building #

This sample contains [a single C++ source file](main.cxx) and is easy to build.

<a name="building-android"></a>
## Android ##
Please check [android](../../android) folder for Android samples.

<a name="building-ios"></a>
## iOS ##
Please check [iOS](../../ios) folder for iOS samples.

<a name="building-windows"></a>
## Windows ##
You'll need Visual Studio to build the code. The VS project is at [validation.vcxproj](validation.vcxproj). Open it.
 1. You will need to change the **"Command Arguments"** like the [below image](../../../VC++_config.jpg). Default value: `$(ProjectDir)..\..\..\assets\samples\td1.txt`
 
![VC++ config](../../../VCpp_config.jpg)
 
You're now ready to build and run the sample.

<a name="building-generic-gcc"></a>
## Generic GCC ##
Next command is a generic GCC command:
```
cd ultimateMRZ-SDK/samples/c++/validation

g++ main.cxx -O3 -o validation
```
- If you're cross compiling then, you'll have to change `g++` with the correct triplet. For example, on Android ARM64 the triplet would be equal to `aarch64-linux-android-g++`.

<a name="building-rpi"></a>
## Raspberry Pi (Raspbian OS) ##

To build the sample for Raspberry Pi you can either do it on the device itself or cross compile it on [Windows](../README.md#cross-compilation-rpi-install-windows), [Linux](../README.md#cross-compilation-rpi-install-ubuntu) or OSX machines. 
For more information on how to install the toolchain for cross compilation please check [here](../README.md#cross-compilation-rpi).

```
cd ultimateMRZ-SDK/samples/c++/validation

arm-linux-gnueabihf-g++ main.cxx -O3 -o validation
```
- On Windows: replace `arm-linux-gnueabihf-g++` with `arm-linux-gnueabihf-g++.exe`
- If you're building on the device itself: replace `arm-linux-gnueabihf-g++` with `g++` to use the default GCC

<a name="testing"></a>
# Testing #
After [building](#building) the application you can test it on your local machine.

<a name="testing-usage"></a>
## Usage ##

`validation` is a command line application with the following usage:
```
validation <path-to-file-containing mrz-lines>
```
- `<path-to-file-containing mrz-lines>` Path to txt file containing MRZ lines to parse. You can use default files at [../../../assets/samples/*.txt](../../../assets/samples).

<a name="testing-examples"></a>
## Examples ##

For example, on **Raspberry Pi** you may call the validation application using the following command:
```
chmod +x ./validation
./validation ../../../assets/samples/td1.txt
```


