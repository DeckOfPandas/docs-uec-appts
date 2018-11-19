# How to test, preview and deploy this website using netlify

## What is Netlify?

[Netlify](https://www.netlify.com/) is a platform-as-a-service product that can deploy and host web sites on its cloud servers. Netlify can build a jekyll site from a GitHub repository, offering advantages over 'vanilla' GitHub Pages hosting such as:
* The ability to deploy mutltiple branches independently of each other
* The ability to use multiple custom domain names and aliases
* The ability to deploy specific branches to specific subdomains

## Netlify deployments for this website

The production branch for this repository is `master`, which is currently deployed on Netlify and is available at the site's base URL: https://cabbagepopsicle.com .

Netlify will build changes pushed to Pull Requests against nominated branches of this repository, making a preview deployment available via one-off URLs that will be posted in the comments thread for a PR (if a build succeeds). Further pushes to a given PR will trigger further builds on Netlify, with the deployments being avaiable at the same URL.

When ready to make the new work available as part of the team's working process, the PR can be merged, and the deployment will then be made available at nominated subdomains of the site's URL.

Currently, the nominated branches for stable Netlify deployments are:
* `master`: current production deployment --> https://cabbagepopsicle.com
* `preview`: current proposed work made available for peer review --> https://preview.cabbagepopsicle.com
* `development`: current working branch for the team --> https://development.cabbagepopsicle.com

Example workflow for a developer:
* Work on the website locally, testing on localhost
* Commit and push changes to branch `foo`
* Open a Pull Request from `foo` against `development`
* See a comment in the PR thread posted by Netlify stating that the build has started, which will be updated on success or fail, with a one-off Netlify URL if successful
* View the temporary deployment, noting changes that need to be made
* Push more changes from local machine to branch `foo`, noting the Netlify comment that another build has started
* Request review as appropriate, merge as appropriate

## Extra options for site administrators

If desired, Netlify can build all pushes to any branch of this repository, not just nominated branches; however, in order to view deployments of a contribution outside a PR against a nominated branch, a developer will require access to the Netlify account themselves.

To view all deployments:
* Open the Netlify control panel for this website, and click the "Deploys" tab
* You will see something like "Branch Deploy: foo@a3ef1ea" at the top of the list of recent deploys
  * Red flair "failed" if the build failed, with full console output available
* Click on the list item to open the status window for that deployment, the click "Preview deploy" to open
* Note that there is a button "Publish deploy" below the "preview" link, and that clicking this button will deploy the current build to the production URL, that is, without requiring a PR and merge on GitHub
