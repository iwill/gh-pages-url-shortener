[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
![Total Lines](https://img.shields.io/tokei/lines/github/iwill/url?color=green)
![GitHub stars](https://img.shields.io/github/stars/iwill/url?style=social)

# 🔗 GitHub Pages URL Shortener

This is a minimal URL shortener that can be entirely hosted on GitHub pages. It
does not need the maintenance of any servers or databases and can be hosted
entirely on GitHub for free!

<details>
    <summary>See Hacker News & GitHub Trending</summary>

[Yay! We got to the top of HN!](https://news.ycombinator.com/item?id=25110879)

<img src="https://i.imgur.com/ZfD7XGt.png" alt="Top of HN" width="240px">

And on GitHub Trending!

<img src="https://i.imgur.com/OkYCSOx.png" alt="GitHub Trending" width="240px">

</details>

## 👨🏿‍🏫 Demo

1. [iwill.im/url/1](https://iwill.im/url/1) should link to this repo, and
   [iwill.im/url/2](https://iwill.im/url/2) should link to an awesome Calculator.

1. To add a new short link, [add an issue](https://github.com/iwill/url-db/issues/new?template=url-shortener-template.md&title=`short-url`+-+accepts+256+characters&body=`loooong-url`%20-%20accepts%2065536%20characters)
   with the body or title being the full URL you want to shorten to
   [iwill/url-db](https://github.com/iwill/url-db).

1. The newly created short URL can be accessed via `iwill.im/url/{issue_number}`

## ☕️ Features

1. Unlike many URL shorteners, this one ~~does not need a database~~ uses a
   "database" in the form of GitHub issues and can be entirely hosted on GitHub
   pages.

1. There is no need for the pound symbol - short URLs look clean like this:
   `iwill.im/url/1` instead of looking like this: `iwill.im/url/#1`.

## 💡 How does this work?

_Thanks to @kidGodzilla for the pretty neat explanation
[here](https://github.com/nelsontky/gh-pages-url-shortener/issues/5#issuecomment-728040879)._

> 1. 404.html handles all requests
> 1. Small javascript snippet fetches a JSON representation of the GitHub issue
>    via the JSON API, and redirects to the issue body or title, as a URL.
> 1. Profit?

## 😎 This is so cool! How can I use this with my own domain?!

_Disclaimer: This method of creating a URL shortener is hacky and not meant to
be reliable. Do proceed at your own risk!_

1. Fork the repo before cloning your fork.
1. Set up GitHub pages for your forked repo.
   1. In your forked repo, **click the Settings tab** and scroll down to the
      GitHub Pages section.
   1. Then select the **main branch** source and click on the **Save** button.
   1. <img src="https://i.imgur.com/kjinFX9.png" alt="How to create GitHub page" height="176px">
1. If you are using your own domain:
   1. [Set your domain up for GitHub pages.](https://docs.github.com/en/free-pro-team@latest/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site#configuring-an-apex-domain)
   1. Change the URL in `CNAME` file to your domain.
1. If you are using GitHub page's default domain i.e. Something like
   `https://<username>.github.io/<repo-name>/`
   1. Delete the `CNAME` file.
   1. Change `var PATH_SEGMENTS_TO_SKIP = 0;` at the top of `404.html` to
      `var PATH_SEGMENTS_TO_SKIP = 1;`.
      1. This is as GitHub domains have an additional path segment (the repo
         name) after the host name.
1. Create a new repo as a database. (Or you could use your forked repo)
   1. Update `var GITHUB_ISSUES_LINK = "<your-github-issues-link>";` at the top
      of `404.html` accordingly afterwards.
      1. Format for `GITHUB_ISSUES_LINK`:
         `https://api.github.com/repos/{owner}/{repo}/issues/`
      1. Remember the trailing `/`!
1. Push your changes to your forked repo, and your low cost and cool as heck URL
   shortener will be ready for use!

## 🍴 Featured forks

To feature your fork here, edit this section and open a PR!

- [nlsn.cf](https://nlsn.cf/1) - The repo which I forked from.
- [iwill.im/url/](https://github.com/iwill/url) - This repo, which supports
  loooong URL by using issue body (or use title if body is not a valid URL,
  body/title accepts up to 65536/256 characters), e.g. [iwill.im/url/2](https://iwill.im/url/2)
  shortened a super long URL.
