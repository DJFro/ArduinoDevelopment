## Steps to configure Visual Studio Code for Arduino development

This document describes the steps to setup Visual Studio Code for Arduino development.
This guide is aimed at windows users, if on a mac replace `F1` with `command` + `shift` + `p` and `Ctrl` + `Alt` with `option` + `command`

- Install latest __Arduino Ide__: [Download here](https://www.arduino.cc/en/Main/Software) 
- Instal __Visual Studio Code__: [Download here](https://code.visualstudio.com/download)
- Install the __Arduino extension__ from de VSCode market place
- Reload VSCode
- Press `F1`, type `"Open User Settings"`, hit `Enter`
- Add the following line to the User Settings main json object: 

   `"C_Cpp.intelliSenseEngine": "Tag Parser"`

- Press `F1`, type `"Arduino: Examples"`, hit `Enter`
- Select the __Blink__ example from the list and open it. Location: `"Built-In-Examples\01.Basics\Blink"`
- Note the `.vscode` folder and it's contents:
  - `arduino.json` Contains the basic settings for your sketch and arduino board configuration.
  - `c_cpp_properties.json` Contains the global arduino settings and where libraries are located.
  - Every Arduino sketch should have these files to let the compiler and intellisense engine know where libraries are located. These are user specific so should not be included in source control.

----------

## Steps before you can compile and upload code to the board
Before you can compile and run your code on your arduino you have to let VSCode know what Arduino Board you are using and to which port it is connected.

- Press `F1`, type `"Arduino: Board Config"`, hit `Enter`
  - Select your Arduino board from the list.
  - Save and quit: `Ctrl` + `s` and close tab.

- Press `F1`, type `"Arduino: Select Serial Port"`, hit `Enter`
  - Select the port your Arduino is connected to.

- Open the __blink.ino__ file and press `F1`, type `"Arduino: Verify"`, hit `Enter` (or use `Ctrl` + `Alt`+ `R`)  
   The Arduino sketch is now compiled.

- Press `F1`, type `"Arduino: Upload"`, hit `Enter` (or use `Ctrl` + `Alt`+ `U`)  
   The Arduino sketch is now uploaded to your board.


----

## Handy VSCode Arduino development tips

- You can use the build in Library manager to install __3rd party libraries__ in the proper global location.
  - Press `F1`, type `"Arduino: Library Manager"`, hit `Enter`
  - Search the 3rd party libraries you need and click `install`

- You can add __3rd party Arduino Board__ configurations and packages by overwriting the `Additional Board Manager URLs`
  - Press `F1`, type `"Open User Settings"`, hit `Enter`
  - Add the following attribute to your settings.json (opened in the editor on the right by the command above): `"arduino.additionalUrls"`
  - Specify urls of 3rd party package sources as a comma seperated list or string array. i.e.:

    ```json
    "arduino.additionalUrls": 
    [
        "https://adafruit.github.io/arduino-board-index/package_adafruit_index.json",
        "https://raw.githubusercontent.com/sparkfun/Arduino_Boards/master/IDE_Board_Manager/package_sparkfun_index.json"
    ]
    ```
  - To install a 3rd party board package:
    - Press `F1`, type `"Arduino: Board Manager"`, hit `Enter`
    - Install the (new) board packages from the list.

----
