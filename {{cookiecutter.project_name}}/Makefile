BUILD_DIR = {{cookiecutter.build_dir}}
PROJECT_NAME = {{cookiecutter.project_name}}

TEX_FILES = $(wildcard *.tex)
BIB_FILES = $(wildcard *.bib)

# List of figures that are generated as part of the build process and put in
# BUILD_DIR
GEN_FIGS =

OUT_PDF = $(BUILD_DIR)/$(PROJECT_NAME).pdf
LOG_FILE = $(BUILD_DIR)/$(PROJECT_NAME).log

LATEXMK = latexmk \
	-pdf \
	-pdflatex="pdflatex -shell-escape -interaction=nonstopmode" \
	-outdir="$(BUILD_DIR)"

ifeq ($(WATCH), 1)
	LATEXMK += -pvc
endif

.PHONY: all
all: $(OUT_PDF)

.PHONY: open
open: $(OUT_PDF)
	{{cookiecutter.open_cmd}} "$^" >/dev/null 2>&1

$(OUT_PDF): $(TEX_FILES) $(BIB_FILES) $(addprefix $(BUILD_DIR)/,$(GEN_FIGS))
	$(LATEXMK) $(PROJECT_NAME)

.PHONY: pplog
pplog:
	pplatex -i $(LOG_FILE)

.PHONY: pperrors
pperrors:
	pplatex -q -i $(LOG_FILE)

.PHONY: clean
clean:
	rm -rf $(BUILD_DIR)
