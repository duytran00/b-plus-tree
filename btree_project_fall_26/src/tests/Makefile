# Portable Makefile for the Minibase B+ tree tests.
# Tested for Omega's system Java; no user-specific paths are required.

PROJECT_ROOT := $(abspath ../..)
LIBRARY      := $(PROJECT_ROOT)/lib/btreelib.jar
SOURCE_ROOT  := $(PROJECT_ROOT)/src
BTREE_CLASS  := $(SOURCE_ROOT)/btree/BTreeFile.class
CLASSPATH    := $(LIBRARY):$(SOURCE_ROOT)

JAVAC      ?= javac
JAVA       ?= java
JAVACFLAGS ?=
JAVAFLAGS  ?=

TEST_CLASSES := BTTest.class TestDriver.class BTDriver.class GetStuff.class

.PHONY: all BTTest bttest clean

all: BTTest.class

# Build the project implementation first if it is missing or out of date.
$(BTREE_CLASS): $(SOURCE_ROOT)/btree/BTreeFile.java $(LIBRARY)
	$(MAKE) -C $(SOURCE_ROOT)/btree

BTTest.class: BTTest.java TestDriver.java $(BTREE_CLASS) $(LIBRARY)
	$(JAVAC) $(JAVACFLAGS) -classpath "$(CLASSPATH)" BTTest.java TestDriver.java

# Keep the historical target name for compatibility with older instructions.
BTTest: BTTest.class

bttest: BTTest.class
	$(JAVA) $(JAVAFLAGS) -classpath "$(CLASSPATH)" tests.BTTest

# Remove only the classes generated from BTTest.java and TestDriver.java.
clean:
	$(RM) $(TEST_CLASSES)
