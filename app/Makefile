# Make it useful for Linux
all: keyboard.c keyboard.h usb.c
	cd ../build;make
install: ../build/app/i2c_puppet.uf2 
	cp ../build/app/i2c_puppet.uf2 /media/${USER}/RPI-RP2

