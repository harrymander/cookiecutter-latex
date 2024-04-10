# LaTeX project boilerplate

Personal [cookiecutter](https://github.com/cookiecutter/cookiecutter) template
for LaTeX.

## Usage

To download:

```
cookiecutter gh:harrymander/cookiecutter-latex
```

and follow the prompts.

Builds `{{project_name}}.pdf` to `{{build_dir}}` via `make`.

Run `make open` to open in PDF viewer. (Open command is configured in `open_cmd`
cookiecutter variable.)

See `Makefile` for more details.

## Requirements

Requires `make`, `latexmk`, `pdflatex`,
[`pplatex`](https://github.com/stefanhepp/pplatex), and additional LaTeX
packages as necessary.
