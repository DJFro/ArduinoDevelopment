## Arduino development tips

### 1. Delay
Avoid using: 
```arduino 
delay(DELAY_IN_MILLISECONDS);
``` 
This freezes the microcontroller completely for the specified time. Instead use a pattern like this:

   ```arduino
   #define DELAY_IN_MILLISECONDS 100
   unsigned long _lastUpdated = 0;

   void loop()
   {
        if(millis() - _lastUpdated >= DELAY_IN_MILLISECONDS)
        {
            _lastUpdated = millis();
            //Do work here
        }
   }
   ```
-----
----
## Advanced Arduino development

### 1. Folder structure and Object Oriented Programming
If you want to write custom libraries or OOP code you need to include the files and folders in a `/src` folder in within the Arduino sketch folder. If the files are in anything other the the `/src` folder the Arduino compiler __ignores__ them completely. Your Arduino solution should look like this:

```
arduino_sketch_name/
|
|── .vscode/                      //Folder .vscode is only here if you use Visual Studio Code
|   |── arduino.json
|   └── c_cpp_properties.json
|
|── src/                          //Folder where you should include your custom classes.
|   |── keyword.txt
|   |── CustomClass.cpp
|   |── CustomClass.h
|   |
|   └── nested/                   //This can be nested in other folders as long as they are a subfolder of /src
|       |── keyword.txt
|       |── CustomNestedClass.cpp
|       └── CustomNestedClass.h
|
└── arduino_sketch_name.ino       //Your main sketch file.
```

Custom classes in the source folder can then be included between `""`. Thrid party libraries are still included between `<>`.
In your sketch this looks as follows:
```arduino
/*Third party library form the global library folder*/
#include <ThirdPartyLibrary.h>

/*Custom classes from within the /src folder located in the sketch folder*/
#include "src/CustomClass.h"
#include "src/nested/CustomNestedClass.h"
```
