---
title: "Hello Hugo - part 2"
date: 2022-02-05T15:36:30Z
draft: false

summary: "So now we have a Hugo blog running locally, how do we make it visible to others? In this post I'll show you how I hosted the blog and how I update it when new Markdown files are pushed to the repository."

cover: 
    image: /hugo-how-to/azure-logo2.png
    alt: "microsoft azure logo"

categories: ["coding"]
tags: ["hugo"]
series: ["Building a Hugo blog"]

params:
    ShowShareButtons: true
    ShowReadingTime: true

---

In [part 1](/posts/hello-hugo-pt1/), we installed and configured Hugo to run on a local machine. Now we're going to publish the blog on the Internet. 

There are [many ways](https://gohugo.io/hosting-and-deployment/) to host a Hugo site. From AWS, to GitHub, Netlify, GitLab, CDNs etc. I was looking for a way to host the site for free and so I chose to explore [Azure Static Web Apps](https://azure.microsoft.com/en-gb/services/app-service/static/#overview) in combination with GitHub and GitHub actions. Not only do Azure Static Web Apps offer a free tier, but you get up to 2 custom domains and a free TLS certificate. Static Web Apps can also host [Azure Functions](https://docs.microsoft.com/en-us/azure/azure-functions/functions-overview) as well as the static content. It's free to [sign up](https://azure.microsoft.com/en-gb/free/) to Microsoft Azure and you also get USD200 credits in the first month. 

![static web app block diagram](/hugo-how-to/swa-block.jpg)

## Creating a Static Web App

There are a couple of different ways to create an instance of a Static Web App - either manually in the portal, or via Infrastructure as Code with [Bicep](https://docs.microsoft.com/en-us/azure/azure-resource-manager/bicep/overview?tabs=bicep). Here, I'll be showing how to create a Static Web App in the Azure Portal - we'll come back to Bicep another time.

Once you've singed into the [Azure Portal](https://portal.azure.com/#home), you can create a new resource.

![azure portal create resource dialog ](/hugo-how-to/azure-create-resource.jpg)

From the list of available resources, search for *Static Web App*.

When you click create, you'll see a dialog like this, where you can create a resource group if necessary, choose the pricing tier, and set the location.

![azure portal static web app create dialog ](/hugo-how-to/swa-create.jpg)
You can connect straight to a GitHub repository (and have a GitHub action automatically created), or set that up later. I'll choose to configure that manually.

We're going to select the free hosting plan which offers the following features:

![azure portal static web app pricing](/hugo-how-to/swa-pricing.jpg)

## Deployment configuration

Once the Static Web App has been created, you'll need get the API deployment token and copy that to the clipboard. 

![azure static web app deployment token](/hugo-how-to/swa-deployment-token.jpg)

Next we'll create a repository secret in the GitHub project by navigating the repository and choosing the Secrets / Actions menu. We'll create a secret called **AZURE_STATIC_WEB_APPS_API_TOKEN** and set the value as the Static Web App API token we found in the previous step.

![github repository secret](/hugo-how-to/github-secret.jpg)

We need one last piece of configuration before we look at GitHub Actions to build and deploy the Hugo site.

We need to create a GitHub [Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) so the GitHub Action can access the repository.

Head over to your GitHub profile -> Settings -> Developer Settings and selecting Personal Access Tokens. Create a token by selecting the repo, workflow and write packages permission boxes.

![github repository secret](/hugo-how-to/github-pat.jpg)

## GitHub Actions

Now comes the fun bit, let's configure a GitHub action to build the Hugo site and deploy it to the Static Web App.

In your .github/workflows folder you can define a yml file like this:

```yaml
name: Blog Build and Deploy
on:
  push:
    branches:
      - main
  pull_request:
    types: [opened, synchronize, reopened, closed]
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Git checkout
        uses: actions/checkout@v2

      - name: Hugo update theme
        run: git submodule update --init --recursive

      - name: Hugo setup 
        uses: peaceiris/actions-hugo@v2
        with:
          hugo-version: "0.92.0"

      - name: Hugo build
        run: hugo --source "./cloudfright-blog" --minify

      - name: Deploy to SWA
        id: deploy
        uses: Azure/static-web-apps-deploy@v1
        with:
          azure_static_web_apps_api_token: ${{ secrets.AZURE_STATIC_WEB_APPS_API_TOKEN }}
          repo_token: ${{ secrets.GITHUB_TOKEN }} 
          action: "upload"
          app_location: "/cloudfright-blog/public" 
          
```
So now we have a GitHub Action that will execute every time commit to main or use a pull request. 

## Custom Domains

The Static Web App creates a random URL, but has the facility to assign a custom domain. In this instance, I wanted to set the custom domain name to blog.cloudfright.com. 

From the Static Web App, select *Custom Domains* 

![github repository secret](/hugo-how-to/custom-domain.jpg)

Then go to your domain management provider (I use [dnsimple](https://dnsimple.com/)) and add a CNAME record, with the content provided by the Static Web App custom domain dialog. Now we're all set to start contributing to our Hugo blog.

	
## Summary

In this post, we created an Azure Static Web App in the Azure portal and configured a GitHub Action to build and deploy the Hugo site.

You can find the github repository for this blog [here](https://github.com/cloudfright/blog).

In [part 3](/posts/hello-hugo-pt3/), we'll look at options for gathering some web analytics and explore more of the Hugo configuration options.  