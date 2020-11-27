---
title: "Getting Better At Programming"
date: 2015-04-26 00:00
tags:
  -
    productivity
  -
    programming
---

I'm going to try and switch up my blogs with a bit more programming content nowadays, just because I don't like posting about extremely controversial topics that generate so many problems with both sides of the argument. We want straight-forwardness and we want things to make sense, especially as programmers or mathers or really all problem solvers, so writing about social, human topics sometimes feels very biased or can feel very absolute and make me seem unreasonable. That's a problem with taking a stance and writing a side online, but I feel like it would be a even more productive use of my time to insert some more concrete arguments in there when the time is right. Let's try it out and see how I feel about it. I've been blogging for 3 years, and I've put out about 60 posts, which is really good I feel. One post every two weeks sounds about right. Time to try to push the quality of the posts up now :)

# Engineering

One of the most bewildering things I get told, is that I over-engineer things. I'm usually a bit peeved about it, but I don't think it's actually that bad of a thing. During most of our coursework, a lot of people just do the minimal amount of work to satisfy the requirements. Often times, we tend to only focus on exactly the project, and not remember some of the context surrounding it. For example, my CS247 class in my 2B term was a very heavy C++ class that introduced Makefiles halfway through. A lot of us just got to the point of the minimal Makefile in order to get the process going, and that's it. And for future C++ coursework, we just modified it slightly to fit the new builds. However, currently in my 4A term, I have an *excessive* amount of knowledge on Makefiles.

This is a sample Makefile I've found works very well.

~~~~~~~ Makefile

CC := g++ # This is the main compiler
# CC := clang --analyze # and comment out the linker last line for sanity

SRC_DIR := src
BUILD_DIR := build

PROJECT_TARGET := bin/exec
TEST_TARGET := bin/tester

SRC_EXT := cpp
SOURCES := $(shell find $(SRC_DIR) -type f -name *.$(SRC_EXT))
OBJECTS := $(patsubst $(SRC_DIR)/%, $(BUILD_DIR)/%, $(SOURCES:.$(SRC_EXT)=.o))

TEST_SOURCE := test/tester.cpp

CFLAGS := -g # -Wall

LIB := \
    -L lib \
    -l library \

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

The over-engineering here, is that you need to have a [include, build, src, bin, lib] folders before this Makefile will work, and that there are subtle things such as backslashes to make each item in a list on a new line. For a 2 week project, would having a better project structure be unnecessary? I'm not entirely sure I can say 100% because I'd be biased, but I feel the flexibility and cleanliness of having a proper build system and project structure is always useful, especially because it can be transferred project to project.

And the most important part is that this is information gained over a couple years of side projects and school projects with continual improvements to a Makefile and project structure that I move project to project.

I feel like as future Software Engineers, we should pride ourselves in continually building up and finding efficiencies that make yourself happy in the future.

# Structured Coding

One of the hardest problems I have is proper naming. Sometimes it comes very clearly, but other times there are insane debates about which one word makes the most sense in this context.

When I have a project, I like splitting files logically into different sections based on some sort of criteria, maybe Models and Views and Controllers, or maybe Visualizer and Parser and Framework. I like having very loosely coupled files with rules such as only one class per file in order to force myself to plan the architecture of the project more carefully. Even for code unmarked school work, I force myself to avoid globals or to use singletons sparingly or to rewrite inheritance or composition structures in order to improve my code. And I try as much as I can to read some of my classmates' code to discover new techniques and to enforce my knowledge of problem areas.

In terms of productivity, I think there are trade-offs between both sides. Without this structure, I can get to the meat of problems much more quickly. But without the structured style, I also have to deal with a lot of overhead in case things change.

But at the end of the day, I've realized that all of this structure is much more relevant during a job, where structure is important for the next person to work on. And when you finally start noticing your own self-discovered strategies or improvements in real code alongside all these other newer, better ideas, it slightly re-inforces that idea of learning and getting better.

The process of getting better is gradual. Continual adjustments and stronger habits helps re-inforce concepts a lot more strongly, and for someone trying to get better in the field, over-engineering it is a good way to start.
