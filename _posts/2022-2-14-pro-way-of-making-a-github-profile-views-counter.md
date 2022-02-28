---
layout: post
title: Pro way of making a GitHub Profile views-counter
description: <p>You might want to see how many times your GitHub profile has been viewed. It reflects your popularity on GitHub.</p> <p>There are many tools for similar purposes <a href=https://github.com/search?q=github+profile+counter>on GitHub</a>, but here, we are using <strong>Bitly link</strong>.</p>
author: cycool29
permalink: /post/000002.html
tags: github profile readme tutorial
read-time: 5
---

---

## Table of Contents

- [Step 1: Create Bitly Link](#step-1)
- [Step 2: Embed to your GitHub Profile](#step-2)
- [Bonus: Show GitHub Profile Views badge](#bonus)
- [How it works](#how-it-works)
  - [How a Bitly link count profile views? ](#bitly-link-how)
  - [How the badge is generated?](#badge-how)

---

You might want to see how many times your GitHub profile has been viewed. It reflects your popularity on GitHub.

There are many tools for similar purposes [on GitHub](https://github.com/search?q=github+profile+counter), but here, we are using **Bitly link**.

Before starting, you will need to create a Profile README. GitHub Docs has [nice documentation](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-github-profile/customizing-your-profile/managing-your-profile-readme) on it.

<h2><span id="step-1">Step 1: Create Bitly Link</span></h2>

- Go to https://bitly.com/, if you don't have a Bitly account, create one. And if you have one, just log in.

- Click **Create**.

![Create button](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/3k23ljrgygm9hb2kiq43.png)

- In the **ENTER LONG URL** box, type `https://example.com/`.  

- Leave all other fields default and click **Create**.

![Create link](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/icv8hrztf5fgaw5o1svh.png)

- Enter any name you'd like for your link in the **TITLE** box. For me, it is `Profile Views`.

- Then, click the **Copy** button to copy your Bitly link.
  After that, click **Save**.

![Save](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ss1ow5ans840cnaug0y0.png)

Now, you've got your Bitly link set up!

<h2><span id="step-2">Step 2: Embed to your GitHub Profile</span></h2>

- Head over to your GitHub profile repository.

- Put `![]([your-bitly-link])` at the end of the README file. For example: `![](https:/bit.ly/abcd123)`. Don't panic if you forgot your Bitly link, just head back to bitly.com and you can copy it again there.

- Click **Commit changes**.

Now your GitHub Profile Counter is done!
You can check how many people land on your profile at bitly.com.

<h2><span id="bonus">Bonus: Show GitHub Profile Views badge</span></h2>

You may notice [my GitHub Profile](https://github.com/cycool29) has a `GitHub Profile Views` badge.

![GitHub Profile Views](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ci9u3klbnd8sz9jt5qoy.png)

Here is how to create it.

- First, back to https://bitly.com.

- Launch Developer Tools by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>I</kbd>

- Go to the `Network` tab.

- Press <kbd>Ctrl</kbd>+<kbd>R</kbd> to refresh the tab.

- From a list of network requests, find a line named `clicks`.

![DevTools](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/tbwfe26lnfc2b1u4p1i2.png)

- Right-click at that line, click `Copy`, and `Copy as cURL`.

- Now back to your GitHub profile repository

- Go to `Settings` -> `Secrets` -> `Actions`

- Click **New repository secret**.

- Fill `PROFILE_VIEWS` in the **Name** field and paste the cURL command in the **Value** field. Then, click `Add secret`.

- Create a file `.github/workflows/update-profile-views.yml` in your GitHub profile repository.

- Copy these lines to the file.

```yml
name: Update Profile Views

on:
  schedule:
    - cron: "*/5  * * * *"
  workflow_dispatch:
  push: { branches: ["main"] }

env:
  COLOR: 00ff00

jobs:
  update-profile-views:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout
        uses: actions/checkout@v2

      - name: Update Profile Views
        run: |
          VIEWS="$(${{ secrets.PROFILE_VIEWS }} 2>/dev/null | jq | grep -B 2 '"hash": "YOUR_HASH"' | head -n 1 | grep -o "[1234567890]*")"          
          echo '<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="214" height="20" role="img" aria-label="${{ github.actor }}&apos;s GitHub Profile Views: 259"><title>${{ github.actor }}&apos;s GitHub Profile Views: 259</title><linearGradient id="s" x2="0" y2="100%"><stop offset="0" stop-color="#bbb" stop-opacity=".1"/><stop offset="1" stop-opacity=".1"/></linearGradient><clipPath id="r"><rect width="214" height="20" rx="3" fill="#${{ env.COLOR }}"/></clipPath><g clip-path="url(#r)"><rect width="183" height="20" fill="#000"/><rect x="183" width="31" height="20" fill="#4c1"/><rect width="214" height="20" fill="url(#s)"/></g><g fill="#${{ env.COLOR }}" text-anchor="middle" font-family="Verdana,Geneva,DejaVu Sans,sans-serif" text-rendering="geometricPrecision" font-size="110"><text aria-hidden="true" x="925" y="150" fill="#010101" fill-opacity=".3" transform="scale(.1)" textLength="1730">${{ github.actor }}&apos;s GitHub Profile Views</text><text x="925" y="140" transform="scale(.1)" fill="#${{ env.COLOR }}" textLength="1730">${{ github.actor }}&apos;s GitHub Profile Views</text><text aria-hidden="true" x="1975" y="150" fill="#${{ env.COLOR }}" fill-opacity=".3" transform="scale(.1)" textLength="210">259</text><text x="1975" y="140" transform="scale(.1)" fill="#000" textLength="210">259</text></g></svg>' | sed "s/259/$VIEWS/g" > profile-views.svg
          git config user.email "41898282+github-actions[bot]@users.noreply.github.com"
          git config user.name "github-actions[bot]"
          git pull
          git add -A
          git diff-index --quiet HEAD || git commit -m "Update profile views to ${VIEWS}"
          git push
```

- Replace `YOUR_HASH` with your Bitly link hash (the text after `bit.ly/` in your Bitly link).
  You can also customize the color by replacing `00ff00` with the HEX code of the color you want

- Click **Commit new file**.

- Place this line of code anywhere in the file you'd like to show the badge. Replace `[your-github-username]` with your GitHub username.

```
[<img src="https://raw.githubusercontent.com/[your-github-username]/[your-github-username]/main/profile-views.svg" height="50"/>](https://github.com/[your-github-username])
```

- Click **Commit changes** to save your changes.

Well done! You should see a beautiful badge in your GitHub profile!

<h2><span id="how-it-works">How it works</span></h2>

<h3><span id="bitly-link-how">How a Bitly link count profile views? </span></h3>

The principle is very simple.

We made the link in a `img` tag. Hence, everytime when users loads your profile page, GitHub will requests to the link.
Although actually it is not an image, the request is still recorded in the Bitly server.

<h3><span id="badge-how">How the badge is generated? </span></h3>

As of the Profile Views badge, we just created a GitHub workflow to automatically update our profile views from Bitly and create a SVG image in the profile repository root every five minutes (it is not _exactly_ five minutes, it runs about 2 to 3 times each hour). And we just simply embed the image in our profile README.
