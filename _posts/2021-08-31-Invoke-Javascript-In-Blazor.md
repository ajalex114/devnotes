---
title:  "How to invoke Javascript function from within C# in Blazor" 
categories: [dev]
description: Web App using Blazor and Azure Static Web Apps
tags: [blazor, javascript, csharp]
--- 

Previously, I <a href="{{ site.baseurl }}/posts/Guid-Gen-Web-App//">wrote about having developed and deployed a web app</a> to [generate GUID](https://guid.ajalex.com/) using `Blazor` and deployed using `Azure Static Web App`.  

I came across this challenge of wanting to invoke a Javascript function in the web app.  Well, this is how you do it.  

First of all, I was using `Blazor WebAssembly App`, and in my scenario using javascript instead of C# seemed the right and easy way to go for it.

This is how your `razor` file would look like.

``` csharp
@page "/"
@inject IJSRuntime jsRuntime

<div class="copy-div">
    <i class="fa fa-copy copy-button" @onclick="()=>CopyItem("item")"></i>
    <img class="arrow" src="./img/blue.png" />
</div>

</div>

@code {
    private void CopyItem(string item)
    {
        jsRuntime.InvokeAsync<String>("copyItem", item);
    }
}
```

Now, create the file `Something.js` (or, in this example CopyItem.js) in the `wwwroot` folder (in this example, it is `wwwroot\js`). Write the javascript function to this file.

``` javascript
function copyItem(item) {
    console.log(item);
    navigator.clipboard.writeText(item);
}
```

Don't forget to add the script reference to `index.html` file.

``` html
<script src="./js/Something.js"></script>
```

This should do the trick.

You can checkout a complete solution implementation [here](https://github.com/ajalex114/guid-gen).
