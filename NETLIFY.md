# How to test, preview and deploy this website using netlify

## What is Netlify?

[Netlify](https://www.netlify.com/) is a platform-as-a-service product that can deploy and host web sites on its cloud servers. Netlify can build a jekyll site from a GitHub repository, offering advantages over 'vanilla' GitHub Pages hosting such as:
* The ability to deploy mutltiple branches independently of each other
* The ability to use multiple custom domain names and aliases
* The ability to deploy specific branches to specific subdomains

## Netlify deployments for this website

Our Netlify service has been set up to assume that this site is built with jekyll into a folder named `_site`. On trigger, Netlify has been instructed to execute `jekyll build`, with the branch `master` being the production branch, ...and that's it.

The production branch, `master`, is currently deployed on Netlify and is available at the site's base URL: https://cabbagepopsicle.com . There are a total of three branches deployed under subdomains:
* `master`: current production deployment --> https://cabbagepopsicle.com
* `preview`: current proposed work made available for peer review --> https://preview.cabbagepopsicle.com
* `development`: current working branch for the team --> https://development.cabbagepopsicle.com

Netlify will build and deploy *all* branches of this repository, with builds triggered by creation of new branches or by updates to existing ones. Note that making any changes at all to any branch will trigger builds on Netlify, whether made by merging Pull Requests or directly in-browser, or by pushing from a local machine. 

If a Pull Request is opened from a new branch against an existing one, Netlify will post a one-off URL that will be in the comments thread for that PR if the build succeeds, or a link to console output if it fails (admin only). Further pushes to a given PR will trigger further builds on Netlify, with the deployments being available at the same temporary URL. 

Changes made to the nominated stable branches detailed above will trigger Netlify builds and deployments available at the specified externally facing URLs, not just at one-off URLs as for other branches. With this in mind, it is recommended that workflow is managaed entirely via Pull Requests, as this will reduce the likelihood of work being made available at reserved URLs in error. Another recommendation is to protect direct pushing to these nominated branches.

Example workflow for a developer:
* Work on the website locally, testing on localhost
* Commit and push changes to branch `foo`
* Open a Pull Request from `foo` against `development`, which is a nominated branch
* See a comment in the PR thread posted by Netlify stating that the build has started, which will be updated on success or fail, with a one-off Netlify URL if successful
* View the temporary deployment, noting changes that need to be made
* Push more changes from local machine to branch `foo`, noting the Netlify comment that another build has started
* Request review as appropriate, merge as appropriate

## Extra options for site administrators

To view all deployments, whether part of PRs or not:
* Open the Netlify control panel for this website, and click the "Deploys" tab
* You will see something like "Branch Deploy: foo@a3ef1ea" at the top of the list of recent deploys
  * Red flair "failed" if the build failed, with full console output available
* Click on the list item to open the status window for that deployment, the click "Preview deploy" to open
* Note that there is a button "Publish deploy" below the "preview" link, and that clicking this button will deploy the current build to the production URL, that is, without requiring a PR and merge on GitHub
