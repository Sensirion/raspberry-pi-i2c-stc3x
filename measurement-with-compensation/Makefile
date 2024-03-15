src_dir = ..
common_sources = ${src_dir}/sensirion_config.h ${src_dir}/sensirion_common.h ${src_dir}/sensirion_common.c
i2c_sources = ${src_dir}/sensirion_i2c_hal.h ${src_dir}/sensirion_i2c.h ${src_dir}/sensirion_i2c.c
driver_sources = ${src_dir}/sht4x_i2c.h ${src_dir}/sht4x_i2c.c ${src_dir}/stc3x_i2c.h ${src_dir}/stc3x_i2c.c

i2c_implementation ?= ${src_dir}/sensirion_i2c_hal.c

CFLAGS = -Os -Wall -fstrict-aliasing -Wstrict-aliasing=1 -Wsign-conversion -fPIC -I${src_dir} -I.

ifdef CI
    CFLAGS += -Werror
endif

.PHONY: all clean

all: stc3x_i2c_measurement_with_compensation

stc3x_i2c_measurement_with_compensation: clean
	$(CC) $(CFLAGS) -o $@  ${driver_sources} ${i2c_sources} \
		${i2c_implementation} ${common_sources} stc3x_i2c_measurement_with_compensation.c

clean:
	$(RM) stc3x_i2c_measurement_with_compensation