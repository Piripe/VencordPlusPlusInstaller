# Vencord++ Installer

The Vencord Installer allows you to install [Vencord++, the best Discord Desktop client mod](https://github.com/Piripe/VencordPlusPlus)

![image](https://user-images.githubusercontent.com/45497981/226734476-5fb42420-844d-4e27-ae06-4799118e086e.png)

## Usage

### Windows

> **Warning**
**Do not** run the installer as Admin

Download [VencordInstaller.exe](https://github.com/Piripe/VencordPlusPlusInstaller/releases/latest/download/VencordInstaller.exe) and run it

If the above doesn't work/open, for example because you're using Windows 7, 32 bit, or have a bad GPU, you can instead use our terminal based installer.

To do so, open Powershell, run the following command, then follow along with the instructions/prompts

```ps1
iwr "https://raw.githubusercontent.com/Piripe/VencordPlusPlusInstaller/main/install.ps1" -UseBasicParsing | iex
```

### Linux

Run the following command in your terminal and follow along with the instructions/prompts

```sh
sh -c "$(curl -sS https://raw.githubusercontent.com/Piripe/VencordPlusPlusInstaller/main/install.sh)"
```

### MacOs

Download the latest [MacOs build](https://github.com/Piripe/VencordPlusPlusInstaller/releases/latest/download/VencordInstaller.MacOS.zip), unzip it, and run `VencordInstaller.app` 

If you get a `VencordInstaller can't be opened` warning, right-click `VencordInstaller.app` and click open.

This warning shows because the app isn't signed since I'm not willing to pay 100 bucks a year for an Apple Developer license.

___

## Building from source

### Prerequisites 

You need to install the [Go programming language](https://go.dev/doc/install) and GCC, the GNU Compiler Collection (MinGW on Windows)

<details>
<summary>Additionally, if you're using Linux, you have to install some additional dependencies:</summary>

#### Base dependencies
```sh
apt install -y pkg-config libsdl2-dev libglx-dev libgl1-mesa-dev
```

#### X11 dependencies
```sh
apt install -y xorg-dev
```

#### Wayland dependencies
```sh
apt install -y libwayland-dev libxkbcommon-dev wayland-protocols extra-cmake-modules
```

</details>

### Building

#### Install dependencies

```sh
go mod tidy
```

#### Build the GUI

##### Windows / Mac / Linux X11
```sh
go build
```

##### Linux Wayland
```sh
go build --tags wayland
```

#### Build the CLI
```
go build --tags cli
```

You might want to pass some flags to this command to get a better build.
See [the GitHub workflow](https://github.com/Vendicated/VencordInstaller/blob/main/.github/workflows/release.yml) for what flags I pass or if you want more precise instructions
