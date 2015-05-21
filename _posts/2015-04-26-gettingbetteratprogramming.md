---
title: "Don't Over-Engineer It"
date: 2015-04-26
tags:
  -
    productivity
  -
    programming
---

I'm going to try and switch up my blogs with a bit more programming content nowadays, just because I don't like posting about extremely controversial topics that generate so many problems with both sides of the argument. We want straight-forwardness and we want things to make sense, especially as programmers or mathers or really all problem solvers, so writing about social, human topics sometimes feels very biased or can feel very absolute and make me seem unreasonable. That's a problem with taking a stance and writing a side online, but I feel like it would be a even more productive use of my time to insert some more concrete arguments in there when the time is right. Let's try it out and see how I feel about it. I've been blogging for 3 years, and I've put out about 60 posts, which is really good I feel. One post every two weeks sounds about right. Time to try to push the quality of the posts up now :)

# Programming

One of the weirdest things I get told is that I over-engineer things. It's hard to say why, because I don't think that's a problem. During our classes at school,


~~~~~~~ Makefile

CC := g++ # This is the main compiler
# CC := clang --analyze # and comment out the linker last line for sanity

SRC_DIR := src
BUILD_DIR := build

PROJECT_TARGET := bin/legoizer
TEST_TARGET := bin/tester

SRC_EXT := cpp
SOURCES := $(shell find $(SRC_DIR) -type f -name *.$(SRC_EXT))
OBJECTS := $(patsubst $(SRC_DIR)/%, $(BUILD_DIR)/%, $(SOURCES:.$(SRC_EXT)=.o))

TEST_SOURCE := test/tester.cpp

CFLAGS := -g # -Wall

LIB := \
    -L /usr/local/lib/ \

INC := \
    -I include \

$(PROJECT_TARGET): $(OBJECTS)
    @echo "  Linking..."
    @echo "  $(CC) $^ -o $(PROJECT_TARGET) $(LIB)"; $(CC) $^ -o $(PROJECT_TARGET) $(LIB)

$(BUILD_DIR)/%.o: $(SRC_DIR)/%.$(SRC_EXT)
    @mkdir -p $(@D) # make directories
    @echo "  $(CC) $(CFLAGS) $(INC) -c -o $@ $<"; $(CC) $(CFLAGS) $(INC) -c -o $@ $<

clean:
    @echo "  Cleaning...";
    @echo "  $(RM) -r $(BUILD_DIR) $(PROJECT_TARGET)"; $(RM) -r $(BUILD_DIR) $(PROJECT_TARGET)

test:
    $(CC) $(CFLAGS) $(TEST_SOURCE) $(INC) $(LIB) -o $(TEST_TARGET)

.PHONY: clean

print-%: ; @echo $*=$($*)

~~~~~~~
