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
  - [Sequencer Basics](#sequencer-basics)

{% capture content %}
TO-DO: Write these sections:
- General
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

A "thread" is an _instance_ of a stack. Whenever a stack runs, it is being run by a thread. You can imagine it as an invisible object that causes the code of a stack to run, stepping through its blocks one at a time (well, actually, multiple at a time, but we will get to that in the next section).

If a stack is running multiple times at once, for example, if two clones are both running the `when I start as a clone` stack, there will be multiple threads executing that stack, one for each clone. Conversely, if a stack is not being executed at all, there will be no threads executing that stack.

<video alt="Figure 1" src="assets/Stacks & Threads - Figure 1.mp4" width="480" controls></video><br>
_Figure 1_

When custom blocks are executed, they do not create a new thread. They are executed by the same thread running the stack that calls them.

<img alt="Figure 2" src="assets/Stacks & Threads - Figure 2.gif" width="480"></img><br>
_Figure 2_

### Sequencer Basics

The "sequencer" is an internal system of PenguinMod that manages different threads running simultaneously[^1]. The way it does this is not actually by running them in parallel, but rather by alternating between threads, stepping them through some of their code, then moving on to the next thread. The order by which it does this is the order that the threads appear in the "thread queue", a.k.a. "threads array"[^2].

The sequencer has three important time units: "steps", "ticks", and "frames". Frames will be discussed in detail in the next section, but for now, you can think of ticks and frames as the same thing.

Every tick, the sequencer will trigger a step in every thread in the queue, one after another. This means that steps occur inside of ticks, which occur inside of frames. Steps are thread-specific, meaning they apply to a single thread, but ticks and frames are global, meaning they apply to the entire project.

<video alt="Figure 1" src="assets/Sequencer Basics - Figure 1.mp4" width="480" controls></video><br>
_Figure 1_

In figure 1, notice how the sequencer alternates between the running threads, and steps each of them once. A tick is one full alternation where both thread 1 and 2 are stepped. If this code were to be run in realtime, you would never see the small sizes. This is because thread 2 always was stepped last at the end of every tick, so the only frames you see are the ones right after thread 2.

Also notice how on each step, the thread instantly advances to the next `wait [1] seconds` block, instantly executing the `set size to [SIZE]%` block in the process. This is because each step will continue running blocks until a "yield" happens. The `wait [1] seconds` block is a block that yields over and over until 1 second has elapsed. Because it yields, the steps end during the execution of this block, pausing that thread until it is stepped again.

Finally, notice how there are some ticks of inactivity, where even though the threads are stepped, the pointer doesn't move and is still on the `wait [1] seconds` block. This is because as previously mentioned, that block yields _repeatedly_, meaning that not only does it end a step once, but it actually will also immediately end multiple steps that come after it, in this case until 1 second has elapsed.

[^1]: Technically pseudo-simultaneously.

[^2]: This can be retrieved with the [`(threads)`](https://the-can-of-soup.github.io/penguinmod/threads_extension/docs/reference.html#codethreadscode--gt-arraythread) block in the Threads extension.
