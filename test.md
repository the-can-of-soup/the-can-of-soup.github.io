---
title: some other title
header_url: "/testefvwfve.html"
---

# test.md
This is a test markdown file

_lorem ipsum dolor sit amet_

```javascript
// javascript code block
let foo = 'bar';
class MyClass {
  constructor(a, b = null) {
    return a?.example;
  }
  static staticMethod(a, b, ...) {
    let x = 4;
    return x;
  }
}
MyClass.staticMethod(1, 2);
function example({a, b, c}) {
  let x = d => d + 1;
  let y = (function(d){ return d + 1; });
  return (d, e) => (d + e);
}
if (true) {
  try {
  } catch {
  }
}
while (false) {
}
do {
  debugger;
  break;
  continue;
} while (false);
/* multiline comment
second line */
```

1. numbered
2. list

- bullet
- list

> blockquote

horizontal rule:

---

inline code: `foo + 'bar' === 'baz'`

footnote top[^1]

[^1]: footnote bottom

|table|other column|
|-|-|
|a|b|
|c|d|

<blockquote class="note">example note</blockquote>

<blockquote class="tip">example tip</blockquote>

<blockquote class="important">example important note</blockquote>

<blockquote class="warning">example warning</blockquote>

<blockquote class="caution">example caution</blockquote>
