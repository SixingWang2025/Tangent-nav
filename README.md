# Tangent Nav

Hugo-powered navigation site at [sixingwang2025.github.io/nav](https://sixingwang2025.github.io/nav/), built with [WebStack-Hugo](https://github.com/shenweiyan/WebStack-Hugo) theme.

## Local Dev

```bash
hugo server
```

## Deploy

Build Hugo locally, then push — `public/` is committed to the repo. GitHub Actions deploys `./public` to the `gh-pages` branch and triggers the main site rebuild.

```bash
hugo --minify --baseURL "https://sixingwang2025.github.io/nav/"
git add public/ && git commit -m "update nav" && git push
```
