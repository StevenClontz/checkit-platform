# CheckIt Templates

CheckIt templates are written in an XML language called *SpaTeXt*. SpaTeXt is isomorphic to a subset of
the [PreTeXt](https://pretextbook.org/) markup language, but designed for use in SPAs (Single Page
web Apps) and other browser-based applications, such as the CheckIt Viewer at <https://checkit.clontz.org>.

Insertion of randomized elements is done using the [Mustache](https://mustache.github.io/)
templating system.

## SpaTeXt

Each template begins with some XML boilerplate, followed by an `<exercise/>`
(or more verbosely, `<exercise></exercise>`) which
contains a `<statement/>` and `<answer/>`. The statement describes the problem the
student is expected to solve, and the answer is a "final answer" used to verify
that the student's calculations are correct (but it should not be a full explanation
of the solution).

Here's a minimal working example.

```xml
<?xml version='1.0' encoding='UTF-8'?>
<exercise xmlns="https://spatext.clontz.org" version="0.0">
    <statement>
        <p>Your question.</p>
    </statement>
    <answer>
        <p>Its answer.</p>
    </answer>
</exercise>
```

## SpaTeXt Features

### Paragraphs

All text content should be defined within one or more paragraphs `<p/>`.

```xml
<statement>
    <p>First line.</p>
    <p>Second line.</p>
</statement>
```

### Mathematical notation

Mathematics is written in LaTeX. It can be included either within a paragraph
using *inline math* `<m/>`:

```xml
<statement>
    <p>
        Here's the Pythagorean theorem:
        <m>a^2+b^2=c^2</m>.
    </p>
</statement>
```

Or it can be typeset separate from the paragraph using *display math* `<me/>`:

```xml
<statement>
    <p>
        The Pythagorean theorem is shown below.
    </p>
    <me>
        a^2+b^2=c^2
    </me>
</statement>
```

### Lists

Ordered lists (labeled as lowercase letters, e.g. as parts of a problem)
are marked up as `<ol/>`. Unordered lists (using bullets) are marked up
as `<ul/>`. Each item of the list is given as `<li/>`. Don't forget to wrap
all text content with `<p/>` paragraphs!

```xml
<statement>
    <p>Compute each of these.</p>
    <ol>
        <li><p>The sum of <m>1</m> and <m>2</m>.</p></li>
        <li><me>10-4</me></li>
    </ol>
</statement>
<answer>
    <ol>
        <li><p>The sum is <m>3</m>.</p></li>
        <li><p>The difference is <m>6</m>.</p></li>
    </ol>
</answer>
```

### Comments

Comments in the source may be added as
`<!-- comments -->`.

```xml
<statement>
    <p>
        The Law of Cosines is shown below.
    </p>
    <!-- TODO: fix this! -->
    <me>
        a^2+b^2=c^2
    </me>
</statement>
```

### Special Characters `<`, `>`, `&`

Three characters have special meaning inside XML: `<`, `>`, `&`.
However they can be inserted using the following codes:

- `&lt;` for `<`
- `$gt;` for `>`
- `&amp;` for `&`

### Images

Images are not currently implemented, but are planned for the future.
The delay is due to the lack of a universal markup language designed
for humans to describe figures that is understood by all the different
applications that use CheckIt (LaTeX, LMSs, web apps, etc). There are
workarounds, but I don't want to rush into an inelegant solution that
will cause authors headaches down the road.


## Mustache

To describe randomized exercises, a programming language is used
to generate the randomized data to be inserted into a template. The
widely-supported Mustache templating system is used to do this.

Full documentation on Mustache is available at
[https://mustache.github.io/](https://mustache.github.io/mustache.5.html).
Briefly, we cover a simple example below.

Suppose that your generator produced the following "JSON" data
object.

```json
{
    "function": "x^2+1",
    "values": [
        {"x": "1", "fx": "2"},
        {"x": "-3", "fx": "10"}
    ]
}
```

Then values can be inserted using mustaches (curly braces) `{{key}}`,
and lists may be looped over by wrapping with the pound sign `{{#key}}`
and forward slash `{{/key}}`.

```xml
<?xml version='1.0' encoding='UTF-8'?>
<exercise xmlns="https://spatext.clontz.org" version="0.0">
    <statement>
        <p>For each value of <m>x</m>, find <m>f(x)</m>.</p>
        <me>f(x)={{function}}</me>
        <ol>
            {{#values}}
                <li><m>{{x}}</m></li>
            {{/values}}
        </ol>
    </statement>
    <answer>
        <ol>
            {{#values}}
                <li><m>{{fx}}</m></li>
            {{/values}}
        </ol>
    </answer>
</exercise>
```

This would produce the following result.

```xml
<?xml version='1.0' encoding='UTF-8'?>
<exercise xmlns="https://spatext.clontz.org" version="0.0">
    <statement>
        <p>For each value of <m>x</m>, find <m>f(x)</m>.</p>
        <me>f(x)=x^2+1</me>
        <ol>
                <li><m>1</m></li>
                <li><m>-3</m></li>
        </ol>
    </statement>
    <answer>
        <ol>
                <li><m>2</m></li>
                <li><m>10</m></li>
        </ol>
    </answer>
</exercise>
```

### Choosing scenarios

A common pattern in word problems is having several scenarios to choose from.
Here's a recommended way to implement this.

First, have your generator randomly choose which scenario your exercise will
use:

```python
def generator():
    random_scenario = choice(["apples","bananas"])
    return {
        "scenario": {random_scenario: True},
    }
```

Then you can change how your template looks based on scenario as follows:

```xml
<statement>
    {{#scenario}}
        {{#apples}}
            <p>I like apples.</p>
        {{/apples}}
        {{#bananas}}
            <p>I hate bananas.</p>
        {{/bananas}}
    {{/scenario}}
</statement>
```

### True/False

If you need to display different content based on whether certain criteria apply,
check these criteria in your generator and pass an appropriate True/False boolean
as demonstrated below:

```python
def generator():
    random_number = randrange(10)
    is_even = bool(random_number % 2 == 0) # returns True or False
    return {
        "number": random_number,
        "even": is_even,
    }
```

Then this boolean value can be checked using `{{#key}}show if true{{/key}}{{^key}}show if false{{/key}}`:

```xml
<answer>
    {{#even}}
        <p>{{number}} is even.</p>
    {{/even}}
    {{^even}}
        <p>{{number}} is odd.</p>
    {{/even}}
</answer>
```
