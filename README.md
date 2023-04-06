# Windows Installer using WiX Toolset
## Creating an upgradable Windows Installer for a testing app


1. cd into the directory of your choice and clone the repository
2. Open the project with Visual Studio (WiX toolset neeeds to be installed)
3. Build the project
4. Build the installer (supports x86 and x64)
5. Once built, it will automatically create a folder named 'Installers', which is where the .msi files will be located. 


## Notes
* The installer for this project was created with [WiX Toolset](https://wixtoolset.org/) v3.11.2. 
* The code is easy to reuse to create an installer for other projects because it works with variables (preprocessor and localization) instead of hard-coded values. 

For example:
```
$(var.MyProject.ProjectName)
```

will query the correct project name at build time even if I change the name of the referenced project after the reference is added. [Read more.](https://wixtoolset.org/docs/v3/votive/votive_project_references/)

Most of the changes have to be made inside the 'local.wxl' and the [.wixproj](https://wixtoolset.org/docs/v3/msbuild/authoring_first_msbuild_project/) file. 
* The code can create a 32 and 64 bit installer (don't forget to replace all the GUIDs!).
* It is upgradable.
* It uses the *WixUI_Minimal* UI template. More templates can be found [here.](https://wixtoolset.org/docs/v3/wixui/wixui_dialog_library/)
* Additionally, this project uses [Heat.exe](https://wixtoolset.org/docs/v3/overview/heat/) to harvest registry files without the need of doing it manually.  




