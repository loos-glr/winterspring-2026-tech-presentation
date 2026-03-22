# Marp Template for Grafisch Lyceum Rotterdam

Marp is a Markdown format for creating presentations. For more information about how it works, [check their website](https://marp.app). 

This repository contains a custom theme for Grafisch Lyceum Rotterdam.

To use a custom theme in Marp you need to add the `theme.css` file to your VS `code markdown.marp.themes` config. In the JSON config that would look like this:

```json
"markdown.marp.themes": [
    "theme.css"
]
```

Make sure this theme.css file is in the root of your workspace.
You will also need the images folder if you want to use the backgrounds and logo.

If you want to make use of css animations you can also include the `animate.min.css` file in your workspace root.

When all files are in place you can create a markdown file with the following set-up:

```markdown
---
marp: true
theme: glr
---

<!-- _class: logo-slide -->

<img class="animate__animated animate__rubberBand" width="400" src="images/image70.png" />

![bg cover](images/image11.png)

---
```

See the `template-simple.md` file for a full example of all pages.