ofxTtb
=====================================

[Intel's Threading Building Blocks](https://www.threadingbuildingblocks.org/) for openFrameworks. This is still a work in progress. 

Introduction
------------
This addon dos not do much by itself but its aim is to make integration of openFrameworks with [Intel's Threading Building Blocks](https://www.threadingbuildingblocks.org/) a lot easier. Esentially it will add the necesary includes, library links and search paths to your OF project.


Installation
------------
Install as any regular addon; put it in  `openframeworks_folder/addons`
Use the Project Generator to add to your project.

So far this is working on macos but it will be implemented on all platforms.

### macos
Currently this library is built as a dynamic library, and needs to be linked properly. Unfortunatelly the Project Generator does not support the needed linking flags to be generated automatically but the fix is easy. 
Open this addons `addon_config.mk` file and modify the line that says 

```
ADDON_LDFLAGS =  -rpath /path/to/your/openFrameworks/folder/addons/ofxTbb/libs/tbb/lib/osx
```
by changing where it says `/path/to/your/openFrameworks/folder` for the **absolute** path to your openFrameworks folder. It is important that this is the absolute path.
For example, I have my openFrameworks folder inside my home folder, so in my case it reads like the following 
```
ADDON_LDFLAGS =  -rpath /Users/roy/openFrameworks/addons/ofxTbb/libs/tbb/lib/osx
```

If you are not sure about the absolute path of this folder, an easy trick is to open the terminal (type terminal on the spotlight search and press enter) and drag and drop the openFrameworks folder into the terminal window that you just opened. there it will show the absolute path to the folder you just dragged, select that text copy and paste into `addon_config.mk`. :)

Now the projects you create will be linked properly to the TBB library.
The downside of this approach is that you will not be able to share this app, as you'll need the other person to install the TBB in the exact same path that you defined, which is quite unlikely, but it will work for you while creating this app.
If you want to make this app sharable you need to do the following.


