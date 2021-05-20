---
title: Error: Could not load file or assembly 'Telerik.Web.UI, Version=XXXXX.X.XXXX.X, Culture=neutral, PublicKeyToken=XXXX' or one of its dependencies
description: Error: Could not load file or assembly 'Telerik.Web.UI, Version=XXXXX.X.XXXX.X, Culture=neutral, PublicKeyToken=XXXX' or one of its dependencies in RadEditor dialogs. Check it now!
type: how-to
page_title: Error: Could not load file or assembly 'Telerik.Web.UI, Version=XXXXX.X.XXXX.X, Culture=neutral, PublicKeyToken=XXXX' or one of its dependencies
slug: error-could-not-load-file-or-assembly-telerikwebui-versionxxxxxxxxxxx-cultureneutral-publickeytokenxxxx-or-one-of-its-dependencies
res_type: kb
---


  
## PROBLEM  
It is possible to receive the following error message after upgrading your web project with Telerik ASP.NET AJAX controls to another version: Could not load file or assembly 'Telerik.Web.UI, Version=XXXXX.X.XXXX.X, Culture=neutral, PublicKeyToken=XXXXXXXXXXXXX' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)
   
## DESCRIPTION
The problem is due to the fact that the RadEditor's **DialogHandler** and **SpellCheckHandler** **httpHandlers **are registered in the web.config file with their fully qualified names and their versions are not updated.  
   
## SOLUTION
 After upgrading your project to another version, you should update not only the Telerik.Web.UI.dll in the /bin folder, but also the **DialogHandler** and **SpellCheckHandler** **httpHandlers **declarations in web.config file as shown below: 

````XML
<httpHandlers>
      ...
      <add path="Telerik.Web.UI.DialogHandler.aspx" verb="*" type="Telerik.Web.UI.DialogHandler, Telerik.Web.UI, Version=2007.2.1107.0, Culture=neutral, PublicKeyToken=121fae78165ba3d4"
        validate="false" />
      <add path="Telerik.Web.UI.SpellCheckHandler.axd" verb="*" type="Telerik.Web.UI.SpellCheckHandler, Telerik.Web.UI, Version=2007.2.1107.0, Culture=neutral, PublicKeyToken=121fae78165ba3d4"
        validate="false" />
</httpHandlers>
````
 
You should write the fully qualified names only if the Telerik.Web.UI.dll is registered in the GAC. If the Telerik.Web.UI.dll file is placed in the /bin folder of your project you can register the **SpellCheckHandler** **httpHandlers** in the web.config file with their short names, e.g.:
 
 ````XML
<httpHandlers>
    ...
    <add path="Telerik.Web.UI.DialogHandler.aspx" verb="*" type="Telerik.Web.UI.DialogHandler, Telerik.Web.UI"
 validate="false" />
    <add path="Telerik.Web.UI.SpellCheckHandler.axd" verb="*" type="Telerik.Web.UI.SpellCheckHandler, Telerik.Web.UI"  validate="false" />
</httpHandlers>
````


