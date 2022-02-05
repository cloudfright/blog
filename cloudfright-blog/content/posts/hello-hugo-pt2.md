---
title: "Hello Hugo - part 2"
date: 2022-02-05T15:36:30Z
draft: true
---

So now we have a Hugo blog running locally, how do we make it visible to others? In this post I'll show you how I hosted the blog and update it when new Markdown files are pushed to the repository.

I was looking for a way to host the site for free and so I chose to adopt [Azure Static Web Apps](https://azure.microsoft.com/en-gb/services/app-service/static/#overview). Not only is there a free tier, but you get up to 2 custom domains and a free TLS certificate. Static Web Apps can also host Functions as well as the static content. It's free to [sign up](https://azure.microsoft.com/en-gb/free/) to Microsoft Azure and you also get USD200 credits in the first month. 

![static web app block diagram](/hugo-how-to/swa-block.jpg)

There are a couple of different ways to create an instance of a Static Web App - either manually in the portal, or via Infrastructure as Code with [Bicep](https://docs.microsoft.com/en-us/azure/azure-resource-manager/bicep/overview?tabs=bicep).

If you choose to manually create the resource in the Azure portal, you'll see a dialog like this, where you can choose the pricing tier and the location.

![azure portal static web app creation dialog ](/hugo-how-to/swa-create.jpg)

The free hosting plan 


	- Creating a token
	- Setting a API DEPLOYMENT token secret
	- Creating infrastructure 
	- Creating a personal access token

	- Set up a CNAME in DNS
	- Set up custom domain in static web app
	
	- Building github actions 



In part 2, I'll look at options for gathering some web analytics and explore more of the configuration options.  