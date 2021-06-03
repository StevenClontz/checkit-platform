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

## Learning SageMath

The brief [Tour of Sage](https://doc.sagemath.org/html/en/a_tour_of_sage/index.html)
and more detailed tutorial [Guided Tour](https://doc.sagemath.org/html/en/tutorial/tour.html)
are good places to get started learning how to leverage SageMath to represent mathematics.

The [Random Numbers with Python](https://doc.sagemath.org/html/en/reference/misc/sage/misc/prandom.html)
is a good reference for producing randomized elements.
