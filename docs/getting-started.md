# Getting Started

## Install

Important: Ensure you have Python 3.6, or above, installed on your system.

Install using pip:

```sh
    pip install -U preql-lang
```

## Run the interpreter in the console (REPL)

To start the interpreter, run the following in your shell:

```sh
    preql
```

Preql will use Sqlite's memory database by default.

### Explore an existing database

When you start the interpreter, you can specify which database to connect to.

```sh
    # Postgresql
    preql postgres://user:pass@host/dbname

    # MySQL
    preql mysql://user:pass@host/dbname

    # Sqlite (use existing or create new)
    preql sqlite:///path/to/file
```

When already inside the Preql interactive prompt, or in a Jupyter Notebook, use the `connect()` method.:

```go
    connect("sqlite:///path/to/file")
```

Use introspective methods to see a list of the tables, and of the available functions:

```go
    // Get a list of all tables in database
    >> tables()

    // Get help regarding how to use Preql
    >> help()

    // For example:
    >> help(connect)
    func connect(uri, load_all_tables, auto_create) = ...

        Connect to a new database, specified by the uri
        ...
```

## Run in Jupyter Notebook

1. Install the Preql kernel into the jupyter:

```sh
    preql --install-jupyter
```

2. Run Jupyter Notebook as usual:
```sh
    jupyter notebook
```

3. create a new notebook with the `Preql` kernel, or open an existing one.

Inside the notebook, use the `connect()` function to connect to a database.

For an example, view the following Jupyter notebook: [Tutorial: Exploring a database with Preql](https://github.com/erezsh/Preql/blob/master/docs/chinook_tutorial.ipynb)

## Use as a Python library

```python
from preql import Preql
p1 = Preql()                             # Use memory database
p2 = Preql("sqlite:///path/to/file")     # Use existing or new file

assert p1('sum([1..10])') == 45
```

## Run as a REST / GraphQL server

Coming soon!

## Further reading

- [Learn the language](language.md)
- [Read the tutorial](tutorial.md)