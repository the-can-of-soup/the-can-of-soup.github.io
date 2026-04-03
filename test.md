---
title: Page-Specific Title
header_url: "https://www.youtube.com/watch?v=dQw4w9WgXcQ"
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

{% capture content %}
example note
{% endcapture %}
{% include admonitions/info.md content=content %}

{% capture content %}
example tip
{% endcapture %}
{% include admonitions/tip.md content=content %}

{% capture content %}
example important note
{% endcapture %}
{% include admonitions/important.md content=content %}

{% capture content %}
example warning
{% endcapture %}
{% include admonitions/warning.md content=content %}

{% capture content %}
example caution
{% endcapture %}
{% include admonitions/caution.md content=content %}
