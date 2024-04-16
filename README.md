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

The `Makefile` is configured to automatically detect dependencies as they are
used in the TeX files. If there are issues, you may need to manually add
additional dependencies to the prerequisites for the `$(TARGET)` target in the
`Makefile`.

Run `make open` to open in PDF viewer (open command is configured in `open_cmd`
cookiecutter variable). Run `make watch` to automatically rebuild on changes.

See `Makefile` for more details.

## Requirements

Requires `make`, `latexmk`, `pdflatex`,
[`pplatex`](https://github.com/stefanhepp/pplatex), and additional LaTeX
packages as necessary.
