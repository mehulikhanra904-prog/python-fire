# Quickstart

Python Fire turns a Python object into a command-line interface (CLI). This
short guide shows the smallest useful setup and how to try the generated CLI.

## 1. Install Fire

Install the package in the environment used by your project:

```bash
python -m pip install fire
```

## 2. Expose a function

Create `hello.py`:

```python
import fire


def greet(name='World', excited=False):
  """Return a greeting."""
  message = f'Hello, {name}'
  return message + '!' if excited else message


if __name__ == '__main__':
  fire.Fire(greet)
```

Run it from the directory containing the file:

```bash
python hello.py
python hello.py Ada
python hello.py --name=Ada --excited
python hello.py -- --help
```

The first command uses the default value. The next commands pass a positional
argument and named flags. Fire's own flags, such as help, go after an isolated
`--`.

## 3. Expose a class

Fire can also create a CLI from a class:

```python
import fire


class Calculator:
  def add(self, left, right):
    return left + right

  def multiply(self, left, right):
    return left * right


if __name__ == '__main__':
  fire.Fire(Calculator)
```

Try `python calculator.py add 3 4` or
`python calculator.py multiply --left=6 --right=7`.

## Next steps

- [Using a Fire CLI](using-cli.md) explains argument parsing and built-in flags.
- [The Python Fire Guide](guide.md) covers more object types and features.
- [Troubleshooting](troubleshooting.md) lists common setup and usage issues.
