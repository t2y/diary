# diary

Contents repository for GitHub Pages

## Install Hugo

See Install Hugo:

* https://gohugo.io/getting-started/installing/

Confirm that you can run `hugo` command and the version.

```bash
$ hugo version
hugo v0.84.4 linux/amd64 BuildDate=unknown
```

## Checkout repository

Clone this repository.

```bash
$ git clone git@github.com:t2y/diary.git
$ cd diary/
```

### Run only once after the repository was cloned

This repository include Hugo's theme as `submodule`.
So you have to initialize/update theme repository for the first time when you cloned this repository.

```bash
$ git submodule update --init
```

Confirm [Terminal](https://github.com/panr/hugo-theme-terminal) theme files are cloned.

```bash
$ ls diary/themes/terminal/
```

## Build static site

Build contents and run as server.
The `server` command is useful since it automatically rebuild when you modify a content.

```bash
$ cd diary/
$ hugo server
```

Open http://localhost:1313/ via web browser.

## Create Contents

To create new contents, use the `new` command with the path in contents directory.

```bash
$ hugo new posts/2021/0927.md
path/to/diary/diary/content/posts/2021/0927.md created
```

Or

```bash
$ hugo new posts/2025/0301/index.md
Content "path/to/diary/diary/content/posts/2025/0301/index.md" created
```

## License

Copyright © Tetsuya Morimoto for contents, however some source code is come from Hugo and Terminal theme and comply with their licenses.
