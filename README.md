# Hugo for Pen-y-Fan site

[Hugo](https://gohugo.io/getting-started/quick-start/) static site generator
for [Pen-y-Fan.github.io](https://github.com/Pen-y-Fan/Pen-y-Fan.github.io)

## Installation

Required

- [Go](https://go.dev/) download and install or use a docker container
- [Hugo](https://gohugo.io/getting-started/) download and add to your PATH to allow it to be executable

Recommended:

- [Git](https://git-scm.com/downloads)

### Clone

See [Cloning a repository](https://help.github.com/en/articles/cloning-a-repository) for details on how to create a
local copy of this project on your computer.

e.g.

```sh
git clone git@github.com:Pen-y-Fan/hugo-pen-y-fan.git
```

```sh
cd hugo-pen-y-fan
```

### Add theme

The [congo theme](https://jpanther.github.io/congo/docs/installation/#install-using-hugo) has been included as a git
submodule, it will need to be initialised before first run.

```shell
git submodule update --init
```

Or to update the theme

```shell
git submodule update --remote --merge
```

## Commands

Basic commands

### Create a post

To create a new post **index.md** in the **content/posts/2023/<post-name>/** directory. Note the kebab case (url
friendly) for the directory name.

Example:

```shell
hugo new posts/2023/how-to-update-the-php-version/index.md
```

Open content > 2023 > <post-name> to see index.md. Update the default layout as required.

The default layout has an image placeholder. Search [Unsplash](https://unsplash.com], download the photo, create 
an **images** sub-folder, update the link and arbitration.

### Server

Use the hugo server to check the current state of the development site (-D includes draft pages)

```shell
hugo server -D
```

The website can be accessed from <localhost:1313>

### Deploy

Once the new content has been checked, you are ready to deploy

1. check **draft: false** is set in the front matter
2. deploy the latest additions to the **public** directory:

```shell
hugo --minify
```

The **public** folder is configured as a git submodule, open in PhpStorm, commit and push the changes 😀

## License

MIT License (MIT). Please see [License File](LICENSE.md) for more information.


