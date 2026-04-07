---
title: Threads Documentation
header_url: "/penguinmod/threads_extension/docs/"
---

[← Back to Threads Home](/penguinmod/threads_extension)

### Pages
- [Reference Manual](reference.html)
- [Dev Notes](dev_notes.html)

### Table of Contents
- [General](#general)
  - [Stacks & Threads](#stacks-amp-threads)

{% capture content %}
TO-DO: Write these sections:
- General
  - Sequencer Basics (threads array, steps vs ticks vs frames, etc.)
  - Redraw Conditions (work timer, graphics updated, turbo mode, etc.)
  - Monitor Threads
  - Executable Hat Threads & Predicate Steps
  - Full Timeline of a Frame
- Threads Extension
  - Thread Type (reporter bubble formatting, `toString` and `toJSON` behavior, serialization, etc.) **(actually probably put this in reference manual)**
  - Thread Variables
  - Atomic Loop Blocks
  - Broadcast Blocks
  - Common Patterns (thread manager, `data` thread variable when creating a new thread, `__label__` thread variable, etc.)
- Vanilla Block Reimplementations
  - Vanilla Loop Blocks
  - Vanilla Broadcast Blocks
  - Vanilla New Thread Block
  - Vanilla All At Once Block
- Threads Block Reimplementations
  - Broadcast Blocks
  - Atomic Loop Blocks
{% endcapture %}
{% include admonitions/note.md content=content %}

## General

### Stacks & Threads

PenguinMod code is made of "stacks". A stack is a group of code blocks that all are connected to the same hat; i.e., if you drag a hat block in the editor with your mouse, all blocks that are in the same stack as it will move as well.

A "thread" is an _instance_ of a stack. Whenever a stack runs, it is being run by a thread. You can imagine it as an invisible object that causes the code of a stack to run, stepping through its blocks one at a time (well, actually, multiple at a time, but we will get to that later).

If a stack is running multiple times at once, for example, if two clones are both running the `when I start as a clone` stack, there will be multiple threads executing that stack, one for each clone. Conversely, if a stack is not being executed at all, there will be no threads executing that stack.

<video alt="Figure 1" src="assets/Stacks & Threads - Figure 1.mp4" width="480" controls />

When custom blocks are executed, they do not create a new thread. They are executed by the same thread running the stack that calls them.

<img alt="Figure 2" src="assets/Stacks & Threads - Figure 2.gif" width="480" />
