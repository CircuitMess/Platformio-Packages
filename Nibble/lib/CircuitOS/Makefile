name = Settings
dir = examples/Settings
port = /dev/ttyUSB0
board = cm:esp8266:nibble

ACLI = /home/cm/.arduino/arduino-cli

srcFiles = $(shell find $(dir)/src/ -name '*.cpp') $(shell find src/ -name '*.cpp')
headerFiles = $(shell find $(dir)/src/ -name '*.h')

.PHONY: upload clean

build: $(dir)/build/$(name).bin

$(dir)/build/$(name).bin: $(srcFiles) $(headerFiles) $(dir)/$(name).ino
	@mkdir -p $(dir)/build
	cd $(dir); \
	$(ACLI) compile --fqbn $(board) -o build/$(name).bin $(name).ino

upload: $(dir)/build/$(name).bin
	@cd $(dir); \
	$(ACLI) upload --fqbn $(board) -p $(port) -i build/$(name).bin

clean:
	cd $(dir); \
	rm -rf build