#IAN MICHEAL Ported SDL+OPENGL USING SDL[DREAMHAL][GLDC][KOS2.0]
#2021

TARGET = SDLQUAD

KOS_CFLAGS+= -I$(KOS_BASE)/addons/include/SDL -I$(KOS_BASE)/addons/include -I. -DDREAMCAST

KOS_CFLAGS+= -O3 -ffast-math -fno-common -fno-builtin -fno-exceptions -fstrict-aliasing 


KOS_CPPFLAGS=-fno-operator-names -fno-exceptions $(KOS_CFLAGS)

all: $(TARGET).bin

include $(KOS_BASE)/Makefile.rules


OBJS =	main.o

clean:
	rm -f $(OBJS) $(TARGET).elf $(TARGET).bin

$(TARGET).elf: $(OBJS)
	$(KOS_CC) $(KOS_CFLAGS) $(KOS_LDFLAGS) -o $(TARGET).elf $(KOS_START) \
	$(OBJS) $(OBJEXTRA) -lSDL_gl_1213DH -lGL -lm $(KOS_LIBS)

$(TARGET).bin: $(TARGET).elf
	$(KOS_OBJCOPY) -R .stack -O binary $(TARGET).elf $(TARGET).bin


run: $(TARGET).bin 
	$(KOS_LOADER) $(TARGET).bin

