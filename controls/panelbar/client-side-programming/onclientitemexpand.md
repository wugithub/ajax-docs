---
title: OnClientItemExpand
page_title: OnClientItemExpand - RadPanelBar
description: Check our Web Forms article about OnClientItemExpand.
slug: panelbar/client-side-programming/onclientitemexpand
tags: onclientitemexpand
published: True
position: 8
---

# OnClientItemExpand



## 

The **OnClientItemExpand** client-side event occurs after the user has expanded a panel item.

The event handler receives two parameters:

1. The instance of the panel bar firing the event.

1. An eventArgs parameter containing the following methods:

	* **get_item** returns a reference to the **RadPanelItem** that has been expanded.

	* **get_domEvent()** returns the DOM event object.

````ASPNET
<script>
    function OnClientItemExpand(sender, args) {
        alert("The " + args.get_item().get_text() + " item has been expanded");
    }           
</script>
<telerik:radpanelbar id="RadPanelBar1" runat="server" onclientitemexpand="OnClientItemExpand">
  ...
</telerik:radpanelbar>
````

Note that even though **OnClientItemExpand** occurs after click event is queued, it will fire before the panel item is expanded. Content in panel item will not be available to the event handler. In the case where the event handler needs to access panel content after the item is expanded, execute code using setTimeout with an appropriate delay for the panel item to expand. The example below shows an approach to ensuring the content of a panel item is scrolled into view after the item is expanded.

````ASPNET
<script>
    function OnClientItemExpand(sender, args) {
        window.setTimeout(ScrollToItem, 500);
    }           
    function ScrollToItem() {
        document.getElementById("RadPanelBar1Bottom").scrollIntoView();
    }
</script>
<telerik:radpanelbar id="RadPanelBar1" runat="server" onclientitemexpand="OnClientItemExpand">
  <Items>
    <telerik:radpanelitem id="RadPanelItem1" runat="server">
      <ContentTemplate>
        ...
        <div id="RadPanelBar1Bottom></div>
      </ContentTemplate>
    </telerik:radpanelitem>
</telerik:radpanelbar>
````

# See Also

 * [OnClientItemCollapse]({%slug panelbar/client-side-programming/onclientitemcollapse%})
