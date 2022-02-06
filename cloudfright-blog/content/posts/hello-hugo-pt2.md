---
title: "Hello Hugo - part 2"
date: 2022-02-05T15:36:30Z
draft: true

summary: "So now we have a Hugo blog running locally, how do we make it visible to others? In this post I'll show you how I hosted the blog and how I update it when new Markdown files are pushed to the repository."

categories: ["coding"]
tags: ["hugo"]
series: ["Building a Hugo blog"]

params:
    ShowShareButtons: true
    ShowReadingTime: true

---

There are [many ways](https://gohugo.io/hosting-and-deployment/) to host a Hugo site. From AWS, to GitHub, Netlify, GitLab, CDNs etc. I was looking for a way to host the site for free and so I chose to explore [Azure Static Web Apps](https://azure.microsoft.com/en-gb/services/app-service/static/#overview). Not only is there a free tier, but you get up to 2 custom domains and a free TLS certificate. Static Web Apps can also host [Azure Functions](https://docs.microsoft.com/en-us/azure/azure-functions/functions-overview) as well as the static content. It's free to [sign up](https://azure.microsoft.com/en-gb/free/) to Microsoft Azure and you also get USD200 credits in the first month. 

![static web app block diagram](/hugo-how-to/swa-block.jpg)

There are a couple of different ways to create an instance of a Static Web App - either manually in the portal, or via Infrastructure as Code with [Bicep](https://docs.microsoft.com/en-us/azure/azure-resource-manager/bicep/overview?tabs=bicep).

![azure portal create resource dialog ](/hugo-how-to/azure-create-resource.jpg)



If you choose to manually create the resource in the Azure portal, you'll see a dialog like this, where you can choose the pricing tier and the location.

![azure portal static web app create dialog ](/hugo-how-to/swa-create.jpg)


The free hosting plan offers the following features:

![azure portal static web app pricing](/hugo-how-to/swa-pricing.jpg)


	- Creating a token

![azure static web app deployment token](/hugo-how-to/swa-deployment-token.jpg)

Repository / Secrets / Actoipns 
AZURE_STATIC_WEB_APPS_API_TOKEN

![github repository secret](/hugo-how-to/github-secret.jpg)


Github Profile / settings / developer settings  / personal access tokens

	- Setting a API DEPLOYMENT token secret
	- Creating infrastructure 
	- Creating a personal access token

	- Set up a CNAME in DNS
	- Set up custom domain in static web app
	
	- Building github actions 



In part 2, I'll look at options for gathering some web analytics and explore more of the configuration options.  