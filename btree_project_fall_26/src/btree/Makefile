# Portable Makefile for the Minibase B+ tree project.
# Tested for Omega's system Java; no user-specific paths are required.

PROJECT_ROOT := $(abspath ../..)
LIBRARY      := $(PROJECT_ROOT)/lib/btreelib.jar
SOURCE_ROOT  := $(PROJECT_ROOT)/src
CLASSPATH    := $(LIBRARY):$(SOURCE_ROOT)

JAVAC      ?= javac
JAVACFLAGS ?=

.PHONY: all together clean

all: BTreeFile.class

# Keep the historical target name for compatibility with older instructions.
together: BTreeFile.class

BTreeFile.class: BTreeFile.java $(LIBRARY)
	$(JAVAC) $(JAVACFLAGS) -classpath "$(CLASSPATH)" BTreeFile.java

# Remove only the class generated from the student-editable source file.
# The other supplied .class files must remain in place.
clean:
	$(RM) BTreeFile.class
