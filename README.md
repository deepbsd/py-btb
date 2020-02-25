#  Python - Beyond the Basics

It's been quite some time since I delved into Python.  I've been working
through the Exercism exercises (www.exercism.io), but as far as actually
re-visiting theory, it's been a while (like 2015 since my last course).  This
course covers a lot of things I haven't thought about for a good while, and the
language itself has changed quite a bit. `` It used to be Python 3.4 when I first
studied it, and now we're up to Python 3.7.6 on my Red Hat box here.  I'd like
to see what parts of the language have changed since I last visited it.

## Organizing Larger Programs

Packages contain Modules and sometimes other Packages.  A package will
sometimes contain a `__init__.py` that will initialize the top package from
subordinate modules and packages.  To do this Packages follow a directory
structure with a sys.path

The included 'Reader' package includes a bzipped package and gzipped package.
Here's an example of the directory structure using the Linux 'tree' command:

```
.
├── reader
│   ├── __main__.py
│   ├── __pycache__
│   │   └── __main__.cpython-37.pyc
│   └── reader
│       ├── compressed
│       │   ├── bzipped.py
│       │   ├── gzipped.py
│       │   ├── __init__.py
│       │   └── __pycache__
│       │       ├── bzipped.cpython-37.pyc
│       │       ├── gzipped.cpython-37.pyc
│       │       └── __init__.cpython-37.pyc
│       ├── __init__.py
│       ├── __pycache__
│       │   ├── __init__.cpython-37.pyc
│       │   └── reader.cpython-37.pyc
│       └── reader.py
├── reader.zip
├── test.bz2
└── test.gz
```

The submodule is 'compressed'.  The `__pycache__` directories contain compiled
python code (code that is compiled into byte-code).  

Notice that there is no `__init__.py` at the top level.  These are 'Namespace Packages'.  Instead there is a
`__main__.py` that gets executed instead when the package is imported.  The idea is to prevent clobbering of
existing namespaces and keep all that is germane to the Reader package *inside* the package and not pollute
anything outside of the package where it is being deployed.

Relative imports can be dangerous and should usually be avoided.

Importing all subordinate packages and modules can be accomplished with `import *` 
and defining the `__all__` list.  It's pronounced "Dunder All"

# Beyond Basic Functions
