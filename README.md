# screener-circleci-jekyll

## Overview

This repo includes a CircleCI configuration that:

- Sets up a sample Jekyll website.
- Installs the jekyll-sitemap plugin to auto-generate sitemap.xml.
- Sets hostname on CI Server to "ci.server".
- Runs Jekyll server on default port 4000.
- Starts a Screener Tunnel that exposes CI server to Screener Cloud browsers.
- Runs a Screener test that crawls the Jekyll site's sitemap.xml file, automatically capturing a snapshot of each url in the sitemap.

## How To Run

### Create Test in Screener

In Screener Dashboard:

1. **Create New Test Group:**

<img src="https://s3-us-west-2.amazonaws.com/screener.io/github/screener-circleci-jekyll/add-test-group.png" width="500">

2. **Add a Browser:**
    - Click `+ Browser` to open the Browser dialog.
    - Then click "Save" to add the default Chrome browser and resolution.

3. **Add path to Sitemap:**
    - Click `Pages` to open the Pages Dialog.
    - Add the path `/sitemap.xml` to pages. (Screener will automatically prefix this path with the Base Url added above)
    - Then click "Save".

<img src="https://s3-us-west-2.amazonaws.com/screener.io/github/screener-circleci-jekyll/add-sitemap-pages.png" width="500">

**Note:** Alternatively, you can add individual page paths to Screener instead of including the sitemap.xml.


### Add Environment Variables

The following Environment Variables need to be added to your CircleCI project:

- **SCREENER_API_KEY**
- **SCREENER_GROUP_ID**

Both these values can be copied from your Screener Dashboard.


### Push Code

Push code to Github to run tests in CircleCI.

When tests are complete, you can view the results in Screener (see screenshots below). If regressions are found, Screener will notify you (via email and/or [Slack](https://screener.io/docs/notifications)).


<img src="https://s3-us-west-2.amazonaws.com/screener.io/github/screener-circleci-jekyll/test-dashboard.png" width="500">

Test Results in Dashboard.

<img src="https://s3-us-west-2.amazonaws.com/screener.io/github/screener-circleci-jekyll/test-snapshots.png" width="500">

List of Test Snapshots.
