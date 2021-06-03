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

### Images

Images are not currently implemented, but are planned for the future.
The delay is due to the lack of a universal markup language designed
for humans to describe figures that is understood by all the different
applications that use CheckIt (LaTeX, LMSs, web apps, etc). There are
workarounds, but I don't want to rush into an inelegant solution that
will cause authors headaches down the road.