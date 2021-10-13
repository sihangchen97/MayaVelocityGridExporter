# MayaVelocityGridExporter
 Export velocity grid data from a Maya fluid container to UE.
 
 Modified from <strong>Engine\Extras\MayaVelocityGridExporter</strong> in Unreal Engine installation directory.
***
## Improvements
### Fix Running Error using Maya 2018 or Above
The original code would crash in Maya 2018 or above. The reason is a wrong type setting at grid resoluion variable. To solve it, just modify the type of <em>res[]</em> variable from <em>float[]</em> to <em>int[]</em>.

### Add 'Select' and 'Open' Buttons for Folder Path
'Select' and 'Open' Buttons would offer artists convenience when exporting .fga files without being have to copy Folder Path seperately.

### Provide Debug Code and Convertion Methods for Further Improvements

The debug version code is in [debug folder](./debug). Translation methods between shelf version and debug version will be provided in [Debug part](##Debug) .


***
## Installation
1. Copy the contents of the 'icons' directory to the location of your Maya user preference 'icons' directory, which located in: 
    > C:\Users\<username>\Documents\maya\<version>\prefs\icons\

2. Now copy the content of the 'shelves' directory to the location of your Maya user preferences 'shelves' directory, which located in: 
    > C:\Users\<username>\Documents\maya\<version>\prefs\shelves\

3. Launch Maya. You should now have a shelf tab named "UE4velocityGridExporter" with a blue icon in the shelf. Clicking this icon will launch the .fga exporter window.



***
## Debug
### fga Files could not be saved in certain directories
If your exported file could not be saved, the main reason would be that Maya has no permission to write your output direectories. Please try to save your .fga files to <strong>~/Documents</strong> , <strong>D:\\</strong>, etc.., rather than <strong>C:\\</strong>, the root directory of your system disk, or other directories need administrator permission.

### Convert Shelf Code to Debug Code

To convert Shelf Code to Debug Code, you just need to copy the string after "-command" in [Shelf Code](./Shelves/shelf_UE4velocityGridExporter.mel) and print it in Maya Script Editor. 

Mel Code would be like this: (Remember to add comma at the end)

> print("// Copyright Epic Games ...... gridExport();");

And that's how you can get Debug Code for debugging and further developing.

### Convert Debug Code to Shelf Code
Remind that Maya would simplify your Shelf Code and clean "unnecessary" codes in shelf .mel files when finish running. In our case, if you directly use Debug Code as Shelf Code, all proc would be removed after 1 launch of Maya, which is unexpected. 

To solve this problem, we need to translate our debug code into a mel string and replace what after "-command" in [Shelf Code](./Shelves/shelf_UE4velocityGridExporter.mel) with it. Main Steps are provided below:

> 1. Open a powerful Text Editor(e.g. Sublime Text);
> 2. Find all [ \ ] and replace them with [ \\ ];
> 3. Find all [ " ] and replace them with [ \" ];
> 4. Find all [ sign for enter ] and replace them with [ \n ], and now you have got a one line text;
> 5. Add [ " ] at the beginning and the ending of the line;
> 6. Now you can copy this string and paste it after "-command" in [Shelf Code](./Shelves/shelf_UE4velocityGridExporter.mel).

***

## Have a Nice Maya Day!