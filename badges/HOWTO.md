# How to create you own badge

- We usually use the logos available in [Simple Icons](https://simpleicons.org) to create our badges, so to create one we just pick
  a logo and mount the badge url with name and color (RGB or [css color name](https://www.w3schools.com/cssref/css_colors.php)) like so:
```py
name = "devcontainers"
color = "2753E3"
logo = "launchpad"

badge = f"https://img.shields.io/badge/-{name}-{color}?logo={logo}&logoColor=white&style=for-the-badge"
```
- Then we use it in our markdown like so:
```md
  <a href="https://containers.dev/">
    <img alt="Devcontainers" src="https://img.shields.io/badge/-devcontainers-2753E3?logo=launchpad&logoColor=white&style=for-the-badge" />
  </a>
```

## When a logo isn't available in Simple Icons
- Fear not! We can always create our own logos, based on a svg image!
1. Retrieve the `base64` encoding of your desired image like:
```bash
$ base64 java.svg
PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiIHN0YW5kYWxvbmU9Im5vIj8+Cjwh
[long long string...]
IDwvZz4KPC9zdmc+
```
2. Now we just create the badge using this image instead of the `logo` like so:
```py
name = "F%2A" # URL encoded F*, check https://www.urlencoder.org/
color = "white" 
svgb64 = "PD9[long long string...]IDwvZz4KPC9zdmc+"

badge = f"https://img.shields.io/badge/-{name}-{color}?style=for-the-badge&logo=data:image/svg%2bxml;base64,{svgb64}"
```
- For readability purposes I'm also saving these kinds of badges in this folder, to avoid the huge base64 strings in my markdown file
  so I used them like so:
```md
  <a href="https://fstar-lang.org/">
    <img alt="f-star" src="./badges/F_star-badge.svg" />
  </a>
```
