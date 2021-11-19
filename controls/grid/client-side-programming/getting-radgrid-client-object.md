---
title: Getting RadGrid Client Object
page_title: Getting RadGrid Client Object - RadGrid
description: Check our Web Forms article about Getting RadGrid Client Object.
slug: grid/client-side-programming/getting-radgrid-client-object
tags: getting,radgrid,client,object
published: True
position: 1
---

# Getting RadGrid Client Object



## 

There are two possible means to reference the client grid object:

* Using the **$find(id)** method (shortcut for the findComponent() method) of the ASP.NET AJAX framework:

````JavaScript
<telerik:RadCodeBlock ID="RadCodeBlock1" runat="server">
var grid = $find("<%=RadGrid1.ClientID %>");
//execute some logic here 
</telerik:RadCodeBlock>			
````



* Subscribing to the **OnGridCreated** client-side event of the control. In its handler the **sender** argument (first argument passed in the handler) will reference the client grid object. For more info you can review [this example](https://demos.telerik.com/aspnet-ajax/grid/examples/client/clientsideevents/defaultcs.aspx) from the product's QSF.

Additionally, to get reference to the *div wrapper* or the * html table element * rendered by the RadGrid instance, you can use the **$get(id)** method (shortcut for the document.getElementById() javascript method).

Check out this article for more examples: [Get Client-side Reference to a Control Object]({%slug general-information/get-client-side-reference%})

More info about the $find and $get shortcut methods exposed by the ASP.NET AJAX framework you can find visiting the links below:

* [Sys.Application $find Method](https://docs.microsoft.com/en-us/previous-versions/bb397441(v=vs.140))
* [Sys.Application.findComponent Method](https://docs.microsoft.com/en-us/previous-versions/bb397522(v=vs.140))
* [Sys.Application Class](https://docs.microsoft.com/en-us/previous-versions/bb310856(v=vs.140))
  
    
