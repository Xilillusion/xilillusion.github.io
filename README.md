# xilillusion.github.io

This repository contains my personal website and blog. It is a
static [Quarto](https://quarto.org/) website whose source pages are the
`.qmd` files in this repository.

## Prerequisites

The site was built with:

- Quarto 1.10.18
- `uv` 0.12.8
- R 4.6.1

The blog relies on both Python and R to execute code blocks and render data visualizations.

R packages:

- ggplot2
- nycflights13
- dplyr
- reticulate

Python packages:

- pandas
- seaborn
- matplotlib

## Build from a fresh clone

Run the following shell commands in a terminal:

```sh
git clone https://github.com/Xilillusion/xilillusion.github.io.git
cd xilillusion.github.io

# Render the website.
uv sync
uv run quarto render
```

The `quarto render` command writes the built site to `docs/`, as configured in
[`_quarto.yml`](_quarto.yml). To open it locally after rendering, serve that
directory from the repository root:

```sh
python3 -m http.server 8000 --directory docs
```

Then visit <http://localhost:8000/> in a browser. The checked-in `docs/`
directory is also the publishable site output.

## Site Landing

> Run it locally by running the following shell command in a terminal:

```sh
git clone https://github.com/Xilillusion/xilillusion.github.io.git
```

> Open `xilillusion.github.io/docs/index.html` with browser

OR

> This website is also hosted on [GitHub Pages](https://pages.github.com/) and is available at https://xilillusion.github.io/ 

## Data and network access

The application fetches the fishing dataset directly from [Rdatasets](https://github.com/vincentarelbundock/Rdatasets):

* **Source URL:** `https://raw.githubusercontent.com/vincentarelbundock/Rdatasets/master/csv/COUNT/fishing.csv`
* **Format:** CSV