OBJECTS = main.o
TARGET = hello
all: $(TARGET)
$(TARGET): $(OBJECTS)
 $(CC) -o $@ $^
main.o: | new_header
main.o: version.h
new_header:
	@sed -e "s/<version>/$$(git describe)/g" \
	< version.h.in > version.h.tmp
	@if diff -q version.h.tmp version.h >/dev/null 2>&1; \
	then \
	rm version.h.tmp; \
	else \
	echo "version.h.in => version.h" ; \
	mv version.h.tmp version.h; \
	fi
clean:
	rm -f $(TARGET) $(OBJECTS) version.h
.PHONY: all clean
