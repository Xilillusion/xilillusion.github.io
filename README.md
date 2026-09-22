# xilillusion.github.io

This repository contains Yingwen Liu's personal website and blog. It is a
static [Quarto](https://quarto.org/) website whose source pages are the
`.qmd` files in this repository.

## Prerequisites

The site was built with:

- Quarto 1.10.18
- `uv` 0.12.8
- R 4.6.1

`uv` and R are listed for the broader course/project environment, but this
repository currently contains no Python or R code and does not require either
runtime to render the site. There is no `renv.lock` in this repository, so
there is no R package environment to restore. If an `renv.lock` is added in
the future, `renv` can bootstrap and restore it with the following command
from the repository root:

```r
if (!requireNamespace("renv", quietly = TRUE)) {
  install.packages("renv", repos = "https://cloud.r-project.org")
}
renv::restore()
```

## Build from a fresh clone

Run the following shell commands in a terminal. The `cd` command makes the
repository root the working directory for the remaining commands:

```sh
git clone https://github.com/Xilillusion/xilillusion.github.io.git
cd xilillusion.github.io

# Confirm the installed versions (the versions used for this site are above).
quarto --version
uv --version
R --version

# From the repository root, bootstrap and restore renv only if this project
# has an renv.lock file. This is currently a no-op because it has no lockfile.
Rscript -e 'if (file.exists("renv.lock")) { if (!requireNamespace("renv", quietly = TRUE)) install.packages("renv", repos = "https://cloud.r-project.org"); renv::restore() }'

# Render the website.
quarto render
```

The R command above is the shell form of this R code, also run from the
repository root:

```r
if (file.exists("renv.lock")) {
  if (!requireNamespace("renv", quietly = TRUE)) {
    install.packages("renv", repos = "https://cloud.r-project.org")
  }
  renv::restore()
}
```

The `quarto render` command writes the built site to `docs/`, as configured in
[`_quarto.yml`](_quarto.yml). To open it locally after rendering, serve that
directory from the repository root:

```sh
python3 -m http.server 8000 --directory docs
```

Then visit <http://localhost:8000/> in a browser. The checked-in `docs/`
directory is also the publishable site output.

## Data and network access

This site has no external data pipeline. Its content comes from the tracked
Quarto source files (`index.qmd`, `about.qmd`, `blog.qmd`, and
`posts/first-weeks/index.qmd`) and local images under `images/` and `posts/`.
After Quarto is installed, `quarto render` does not fetch data from the
network; it can be run offline. Network access is only needed to clone the
repository or install missing tools/packages.