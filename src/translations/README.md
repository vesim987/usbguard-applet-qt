How to generate translation files for USBGuard Qt Applet
========================================================

To generate the translation file, you'll need the Qt Linguist tools.

Steps:

 1. Run the lupdate tool to generate a .ts file:

    `$ lupdate -source-language en_US -target-language <LANG> . -ts translations/<LANG>.ts`

 2. Add your translation .ts file to the usbguard-applet-qt.pro project file:
 
    `TRANSLATIONS += translations/<LANG>.ts`

 3. Use the Qt linguist tool to translate the .ts file into
    `<LANG>`.

 4. Release your translation and add the .qm file to the usbguard-applet-qt.qrc resource file as following:
 
    `<file>translations/<LANG>.qm</file>'`


To Update the .ts files and build the corresponding .qm files you need to take the following steps:

 1. Update all translation files

    `$ lupdate -verbose usbguard-applet-qt.pro`

 2. Release the translations
  
    `$ lrelease usbguard-applet-qt.pro`

Hint: lupdate might mark some strings as "vanished". This will cause those strings to not be translated when you open the application despite having translated all strings correcly as lrelease will not add them to the .qm file. As workaround remove the "vanished" attributes in the .ts file and re-execute lrelease.
