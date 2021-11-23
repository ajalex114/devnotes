---
title:  "GUID Generator Web App using Blazor and Azure Static Web Apps" 
categories: [dev, webapp, blogging]
description: Web App using Blazor and Azure Static Web Apps
tags: [blazor, azure, dotnet, csharp, 'static-site']
--- 

As a developer, I often come across the need to generate GUID to use at random places.  
I always jump online, search for "_`generate guid online`_", click on a link, wait for it to load... you know the drill.  
Almost all the online guid generation tools are hefty.  
It takes forever to load. Its filled with ads. It looks ugly. Whatever..  

But you may ask, aren't you a C# developer? `Visual Studio` provides the ability to generate GUID. Why not use it?  
Fair Question..  
Truth is, I never think of it when I need it.  
Plus, I needed an excuse to try out something new.  

I'm not a frontend developer. `Javascript` never really excited me. In fact, all it did was confused me. `CSS`? don't even get me started. `HTML` is the good old kid from long ago. Its managable. But, the main factor that kept me from even trying out frontend was Javascript, although I still hope to master it one day.

The news of [Blazor](https://dotnet.microsoft.com/apps/aspnet/web-apps/blazor) excited me from day One. I mean, I can finally make meaningful web apps without having to worry about Javascript anymore. The only thing that was pending?  
_Motivation. A push. A need. A meaning._

That is when the I read about `Azure Static Web Apps`. Its ease of use and support of multiple frameworks. And Blazor was among them.  
This gave me an opportunity to bring back my old dream about building a web app to generate GUIDs, which I hope to keep simple, clean, neat.

Its a win-win situation. I get to learn something new. People get to use something useful. There is growth and there is impact.  
I set out for it.

## Blazor

`Blazor` was easy to start with. `Visual Studio` provides out of the box template.  
I opted for `Blazor WebAssembly App` for the web application. The default template contains a `hello world` kind of a home page, a click counter page and a weather page.  
I right away removed all the content and tried out few buttons and C# code.
The usual onclick button will only work for Javascript functions.  
Instead, if you want to run `C#` code, you need to use `@onclick` event.  
You can pass in a method to this. This method has to have a return type of `void` and no parameters.  
If you want to pass a parameter, then use a lambda expression.  
`@onclick="()=>Foo(item)"`  

I was quite happy with Blazor. It seemed very simple, but then it struck me. You cannot achieve everything with plain old `C#`.  
You need `Javascript` for certain tasks. In my case, I wanted to add a button to copy the GUID to clipboard. I found it tricky to find it in `C#` which works in `Blazor`. Javascript seemed like the right way to go.  
But that brought together another question. How do I execute Javascript functions? I was not able to add `<script>` tag in the same page. I did some digging and found that we can execute `Javascript` function from inside the `C#` code itself. Its fairly _simple_. I have written a separate <a href="{{ site.baseurl }}/posts/Invoke-Javascript-In-Blazor/">article</a> on this.  

Rest was simple, make the page look good. I got some help from my sister who is a frontend developer. We played around with `CSS` and got it right.  

## Azure Static Web Apps

Microsoft has done a pretty decent job at documenting `How to build a static web app using Blazor in Azure Static Web Apps`.  
In fact they have provided basic templates in Github repositories which you could just take up and deploy directly to Azure Static Web Apps. Pretty neat.  

I selected the Blazor template from Github, created a new repository in my Github and tried to edit it.  
I soon realized my existing app which I used to learn is much simpler. So, I decided to go with it.  
I just took it, created a new Github repository and pushed it.

Now, creating Azure Static Web Apps is very simple.  
Go to `Azure Portal`. Create a new `Azure Static Web App`.  
Connect to Github account. Select the repository, branch, the folders applicable.  
Now, Azure Static Web App will automatically create a new `Github Action workflow` which it uses to take the blazor app code from the repository and deploy to Azure Static Web App.  
Yes, its that simple.  
Azure does it all for you.  
All you have to do is, push your changes to the specified branch.  

Azure Static Web App even creates you a staging environment if you raise a pull request against the selected branch. `Cool...`  

### Custom Domain

By default, when the web app is generated, Azure assigns a URL for you. But, if you own a domain, you can link the web app to the custom domain.

### SSL Certificates

Azure automatically takes care of the SSL Certificate. You don't have to do anything for it. Azure automatically renews the same for you.  
Just be at peace. Its all covered.

## How much did it cost me?

__Nothing__.  
Well except for the domain (which I don't think counts).  

|        |      |
|--------|------|
| Github | Free |
| Azure Static Web App | Free |
| Custom Domain Mapping | Free |
| SSL Certificate | Free |
| Staging Environment | Free - up to 3 staging environments |

I now have a web app up and running free of cost, managed by Azure. How cool is that!  

And by the way, if you need to generate GUIDs, give [this](https://guid.ajalex.com/) a shot.

### Reference

* [Blazor](https://dotnet.microsoft.com/apps/aspnet/web-apps/blazor)  
* [Getting started with Azure Static Web Apps](https://docs.microsoft.com/en-us/azure/static-web-apps/deploy-blazor#:~:text=%20Tutorial%3A%20Building%20a%20static%20web%20app%20with,is%20created%2C%20create%20a%20static%20web...%20More%20)  
* [Source Code](https://github.com/ajalex114/guid-gen)
* [GuidGen](https://guid.ajalex.com/)
