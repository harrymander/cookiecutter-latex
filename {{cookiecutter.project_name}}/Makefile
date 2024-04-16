BUILD_DIR ?= {{cookiecutter.build_dir}}
MAIN_TEX ?= {{cookiecutter.project_name}}.tex

TARGET = $(BUILD_DIR)/$(MAIN_TEX:.tex=.pdf)
.PHONY: all
all: $(TARGET)

$(BUILD_DIR):
	@mkdir -p $@

DEPFILE = $(TARGET).d
LATEXMK_CMD = latexmk \
	-pdf \
	-pdflatex="pdflatex -shell-escape -interaction=nonstopmode" \
	-outdir=$(BUILD_DIR) \
	-M -MF $(DEPFILE) \
	-use-make \
	$(MAIN_TEX)

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
