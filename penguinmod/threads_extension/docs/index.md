---
title: Threads Documentation
header_url: "/penguinmod/threads_extension/docs/"
---

[← Back to Home](/penguinmod/threads_extension)

### Pages
- [Reference Manual](reference.html)
- [Dev Notes](dev_notes.html)

### Table of Contents
- [General](#general)
  - [Threads & Stacks](#threads-amp-stacks)

{% capture content %}
TO-DO: Write these sections:
- General
  - Sequencer Basics (threads array, steps vs ticks vs frames, etc.)
  - Redraw Conditions (work timer, graphics updated, turbo mode, etc.)
  - Monitor Threads
  - Executable Hat Threads & Predicate Steps
  - Full Timeline of a Frame- Threads Extension
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
{% include admonitions/info.md content=content %}

## General

### Threads & Stacks

... TODO ...

<video src="assets/Threads%20&%20Stacks.mp4" width="480" controls>

... TODO ...
