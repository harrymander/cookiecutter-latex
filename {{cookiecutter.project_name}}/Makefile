BUILD_DIR ?= {{cookiecutter.build_dir}}
MAIN_TEX ?= {{cookiecutter.project_name}}.tex

LATEXMK ?= latexmk
PDFLATEX ?= pdflatex

TARGET = $(BUILD_DIR)/$(MAIN_TEX:.tex=.pdf)
.PHONY: all
all: $(TARGET)

$(BUILD_DIR):
	@mkdir -p $@

DEPFILE = $(TARGET).d

PDFLATEX_FLAGS += -shell-escape -interaction=nonstopmode
LATEXMK_FLAGS += \
	-pdf \
	-pdflatex="$(PDFLATEX) $(PDFLATEX_FLAGS)" \
	-outdir=$(BUILD_DIR) \
	-M -MF $(DEPFILE) \
	-use-make

LATEXMK_CMD = $(LATEXMK) $(LATEXMK_FLAGS) $(MAIN_TEX)

$(TARGET): $(MAIN_TEX) | $(BUILD_DIR)
	$(LATEXMK_CMD)

-include $(DEPFILE)

.PHONY: open
open: $(TARGET)
	{{cookiecutter.open_cmd}} $<

.PHONY: watch
watch: | $(BUILD_DIR)
	$(LATEXMK_CMD) -pvc

.PHONY: clean
clean:
	rm -rf $(BUILD_DIR)

LOG_FILE = $(BUILD_DIR)/$(MAIN_TEX:.tex=.log)

.PHONY: pplog
pplog:
	pplatex -i $(LOG_FILE)

.PHONY: pperrors
pperrors:
	pplatex -q -i $(LOG_FILE)
