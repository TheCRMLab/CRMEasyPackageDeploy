# CRM Easy Package Deploy

A simple pre-built template so you can use the Package Deployer tool without having to open Visual Studio.

Using this template you can create a package that will work with the CRM Package Deployer tool to install one or more CRM solutions along with any data imports.

There are two main limitations to using this template and not starting with the Visual Studio template
- You do not have the ability to run custom code to do that you would need to use the full Visual Studio Approach
- You can't create two or more packages with this template and have them used by one instance of the Package Deployer tool.  

The full Visual Studio Package Deployer package preparation documentation can be found here - https://msdn.microsoft.com/en-us/library/dn688182.aspx

Steps for using this template:

- Download the TemplatePackage.zip and unzip locally - you can download it from here
https://github.com/davidyack/CRMEasyPackageDeploy/raw/master/TemplatePackage.zip

- Edit the EasyCRMPackage.json file and change the following text
    "ShortName": "Package Short Name Here",
    "LongName": "Package Long Name Here",
    "Description": "Description Goes Here",

  For example it might look like the following
    "ShortName": "Dave's Cool Tools'",
    "LongName": "Dave's Really Long Cool Name",
    "Description": "This is a great tool to use on your project",

- Edit the PkgFolder\Content\en-us\WelcomeHtml\HTML\default.htm file and change the title and description 

- Edit the PkgFolder\Content\en-us\EndHtml\HTML\default.htm file and change the title and description 

- Copy your CRM Solution Files to PkgFolder

- Edit the ImportConfig.xml file

- Change the Solutions element to contain your list of Solutions to import - for example :
 <solutions>
    <configsolutionfile solutionpackagefilename="solutionFile1.zip" />
    <configsolutionfile solutionpackagefilename="solutionFile2.zip" />
  </solutions>

 - If you used the Configuraton Migration tool to extract data and you want to import it you can provide the name using the crmmigdataimportfile="" element 
 e.g crmmigdataimportfile="data.zip"

 You should be able to make most of the changes documented here - https://msdn.microsoft.com/en-us/library/dn688182.aspx that don't involve code using this approach

 - Download the CRM SDK

 - Copy $SDK\Tools\PackageDeployer folder to a new folder

 - Copy your template folder contents to that same folder

 - Run Package Deployer and you should see your package listed

WARNING: Currently AppSource packaging is not supported using CRMEasyPackageDeployer. Use this only for reference. Do not try to publish your package using this template at this time.

The latest version includes support for creating an AppSource package without any need for code. Building on top of the no code standalone package deployer. @thecrmlab added support for creating an AppSource package. There are a few more files that will need to be edited in order to setup your AppSource package. 

Steps for using this template:

- Download the AppSourcePackage.zip and unzip locally - you can download it from here
https://github.com/TheCRMLab/CRMEasyPackageDeploy/blob/master/AppSourcePackage.zip
- NOTE: You may need to right click the downloaded zip file and select Properties -> Unblock File -> Apply in order to unblock the downloaded file. 
- Follow the instructions above for editing the package elements in the package.zip file located in the root of the downloaded template. NOTE: You will need to extract the package.zip from the AppSourcePackage.zip in order to edit the files. Take note of the structure of the entire zip file to ensure that the package.zip only contains the files necessary and not a nested folder.
- Update the appicon_32_32.png for your app's icon
- Update the privacy.htm and terms.htm to include your privay statement and terms and conditions for your app. Sample privacy and terms are included by default.
- That's it. You're AppSource package is ready for publishing. You can test your package locally using the same steps as above with the CRMEasyPackageTemplate.zip.
- To publish your AppSource package and for more information on AppSource publishing follow the instructions here https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/publish-app-appsource 
