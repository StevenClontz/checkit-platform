# Generators

To define the randomized elements of a CheckIt exercise, a generator
function is defined using a programming language. Currently, we support
the [SageMath](https://www.sagemath.org/) computer algebra system
as it has built-in support for a wide range of mathematics and is
based upon the widely-known Python programming language. But support
for other programming languages is planned for the future.

## Minimal Example

Each generator must define a parameterless function named `generator`, which
returns a dictionary of key/value pairs.

```python
def generator():
    x = var("x")
    f = x^2+1
    x1 = randrange(-5,6)
    x2 = x1
    while x2==x1:
        x2 = randrange(-5,6)
    return {
        "function": f,
        "values": [
            {"x": x1, "fx": f(x=x1)},
            {"x": x2, "fx": f(x=x2)},
        ],
    }
```

Note that CheckIt will automatically convert special SageMath objects such as the
function `f` to LaTeX for insertion into exercise templates.

Note that this function cannot use any `print()` statements!

## Learning SageMath

The brief [Tour of Sage](https://doc.sagemath.org/html/en/a_tour_of_sage/index.html)
and more detailed tutorial [Guided Tour](https://doc.sagemath.org/html/en/tutorial/tour.html)
are good places to get started learning how to leverage SageMath to represent mathematics.

The [Random Numbers with Python](https://doc.sagemath.org/html/en/reference/misc/sage/misc/prandom.html)
is a good reference for producing randomized elements.

### CheckIt-exclusive functionality

- `shuffled_equation(*terms)` produces an equation with terms randomly shuffled to each side. For example,
  `shuffled_equation(x^2,1)` might produce `x^2+1==0`, `x^2==-1`, `1==-x^2`, or `0==-x^2-1`.

## Tips and Tricks

### Don't oversimplify multiplication

Sage is sometimes over-eager to factor when multiplying, but this can be overridden.

```
sage: x^2*(2*x+2)
2*(x + 1)*x^2
```

```
sage: (x^2).mul(2*x+2,hold=True)
(2*x + 2)*x^2
```

### Bugfixing

Errors caused by generator code can be difficult to bugfix. To get a clearer traceback of your error,
copy-paste your generator code into a code cell at <https://checkit.clontz.org> and add a final
line with `generator()` to test things.

![image](https://user-images.githubusercontent.com/1559632/126003922-c30686d5-93de-4a8f-bca7-4ef2ec7dcbb3.png)

### Side by side editing in CoCalc

It's possible (but not obvious how) to edit generators and templates side-by-side with the dashboard in CoCalc.

- Open the dashboard, then click the horizontal split button in the toolbar.

![image](https://user-images.githubusercontent.com/1559632/126040861-cb4c0e8b-5c3d-43e2-81e4-8a39369ec32d.png)

- Switch one of the panes to "Terminal"

![image](https://user-images.githubusercontent.com/1559632/126040864-3d13ae69-9c75-4570-9b0b-63b685ab5933.png)

- Type `open banks/BANK/outcomes/XYZ.xml` (replacing `BANK` with your bank and `XYZ` with your outcome) and hit Enter.

![image](https://user-images.githubusercontent.com/1559632/126040957-517a198d-7304-40f1-9d3c-478ff59951ba.png)

- Repeat with `open banks/BANK/outcomes/XYZ.sage`. The template and generator should now be open in separate panes, and the terminal pane may be closed.

![image](https://user-images.githubusercontent.com/1559632/126040904-0b8370ae-55f9-452e-a588-f5d87f4d10e9.png)


