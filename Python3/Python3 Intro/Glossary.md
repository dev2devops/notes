#Python3
 **Glossary**

`>>>`

The default Python prompt of the interactive shell. Often seen for code examples which can be executed interactively in the interpreter.

`...`

Can refer to:

-   The default Python prompt of the interactive shell when entering the code for an indented code block, when within a pair of matching left and right delimiters (parentheses, square brackets, curly braces or triple quotes), or after specifying a decorator.
    
-   The [`Ellipsis`](https://docs.python.org/3/library/constants.html#Ellipsis "Ellipsis") built-in constant.
    

2to3

A tool that tries to convert Python 2.x code to Python 3.x code by handling most of the incompatibilities which can be detected by parsing the source and traversing the parse tree.

2to3 is available in the standard library as [`lib2to3`](https://docs.python.org/3/library/2to3.html#module-lib2to3 "lib2to3: The 2to3 library"); a standalone entry point is provided as `Tools/scripts/2to3`. See [2to3 - Automated Python 2 to 3 code translation](https://docs.python.org/3/library/2to3.html#to3-reference).

abstract base class

Abstract base classes complement [duck-typing](https://docs.python.org/3/glossary.html#term-duck-typing) by providing a way to define interfaces when other techniques like [`hasattr()`](https://docs.python.org/3/library/functions.html#hasattr "hasattr") would be clumsy or subtly wrong (for example with [magic methods](https://docs.python.org/3/reference/datamodel.html#special-lookup)). ABCs introduce virtual subclasses, which are classes that don’t inherit from a class but are still recognized by [`isinstance()`](https://docs.python.org/3/library/functions.html#isinstance "isinstance") and [`issubclass()`](https://docs.python.org/3/library/functions.html#issubclass "issubclass"); see the [`abc`](https://docs.python.org/3/library/abc.html#module-abc "abc: Abstract base classes according to :pep:`3119`.") module documentation. Python comes with many built-in ABCs for data structures (in the [`collections.abc`](https://docs.python.org/3/library/collections.abc.html#module-collections.abc "collections.abc: Abstract base classes for containers") module), numbers (in the [`numbers`](https://docs.python.org/3/library/numbers.html#module-numbers "numbers: Numeric abstract base classes (Complex, Real, Integral, etc.).") module), streams (in the [`io`](https://docs.python.org/3/library/io.html#module-io "io: Core tools for working with streams.") module), import finders and loaders (in the [`importlib.abc`](https://docs.python.org/3/library/importlib.html#module-importlib.abc "importlib.abc: Abstract base classes related to import") module). You can create your own ABCs with the [`abc`](https://docs.python.org/3/library/abc.html#module-abc "abc: Abstract base classes according to :pep:`3119`.") module.

annotation

A label associated with a variable, a class attribute or a function parameter or return value, used by convention as a [type hint](https://docs.python.org/3/glossary.html#term-type-hint).

Annotations of local variables cannot be accessed at runtime, but annotations of global variables, class attributes, and functions are stored in the `__annotations__` special attribute of modules, classes, and functions, respectively.

See [variable annotation](https://docs.python.org/3/glossary.html#term-variable-annotation), [function annotation](https://docs.python.org/3/glossary.html#term-function-annotation), [**PEP 484**](https://www.python.org/dev/peps/pep-0484) and [**PEP 526**](https://www.python.org/dev/peps/pep-0526), which describe this functionality. Also see [Annotations Best Practices](https://docs.python.org/3/howto/annotations.html#annotations-howto) for best practices on working with annotations.

argument

A value passed to a [function](https://docs.python.org/3/glossary.html#term-function) (or [method](https://docs.python.org/3/glossary.html#term-method)) when calling the function. There are two kinds of argument:

-   _keyword argument_: an argument preceded by an identifier (e.g. `name=`) in a function call or passed as a value in a dictionary preceded by `**`. For example, `3` and `5` are both keyword arguments in the following calls to [`complex()`](https://docs.python.org/3/library/functions.html#complex "complex"):
    
    complex(real=3, imag=5)
    complex(**{'real': 3, 'imag': 5})
    
-   _positional argument_: an argument that is not a keyword argument. Positional arguments can appear at the beginning of an argument list and/or be passed as elements of an [iterable](https://docs.python.org/3/glossary.html#term-iterable) preceded by `*`. For example, `3` and `5` are both positional arguments in the following calls:
    
    complex(3, 5)
    complex(*(3, 5))
    

Arguments are assigned to the named local variables in a function body. See the [Calls](https://docs.python.org/3/reference/expressions.html#calls) section for the rules governing this assignment. Syntactically, any expression can be used to represent an argument; the evaluated value is assigned to the local variable.

See also the [parameter](https://docs.python.org/3/glossary.html#term-parameter) glossary entry, the FAQ question on [the difference between arguments and parameters](https://docs.python.org/3/faq/programming.html#faq-argument-vs-parameter), and [**PEP 362**](https://www.python.org/dev/peps/pep-0362).

asynchronous context manager

An object which controls the environment seen in an [`async with`](https://docs.python.org/3/reference/compound_stmts.html#async-with) statement by defining `__aenter__()` and `__aexit__()` methods. Introduced by [**PEP 492**](https://www.python.org/dev/peps/pep-0492).

asynchronous generator

A function which returns an [asynchronous generator iterator](https://docs.python.org/3/glossary.html#term-asynchronous-generator-iterator). It looks like a coroutine function defined with [`async def`](https://docs.python.org/3/reference/compound_stmts.html#async-def) except that it contains [`yield`](https://docs.python.org/3/reference/simple_stmts.html#yield) expressions for producing a series of values usable in an [`async for`](https://docs.python.org/3/reference/compound_stmts.html#async-for) loop.

Usually refers to an asynchronous generator function, but may refer to an _asynchronous generator iterator_ in some contexts. In cases where the intended meaning isn’t clear, using the full terms avoids ambiguity.

An asynchronous generator function may contain [`await`](https://docs.python.org/3/reference/expressions.html#await) expressions as well as [`async for`](https://docs.python.org/3/reference/compound_stmts.html#async-for), and [`async with`](https://docs.python.org/3/reference/compound_stmts.html#async-with) statements.

asynchronous generator iterator

An object created by a [asynchronous generator](https://docs.python.org/3/glossary.html#term-asynchronous-generator) function.

This is an [asynchronous iterator](https://docs.python.org/3/glossary.html#term-asynchronous-iterator) which when called using the `__anext__()` method returns an awaitable object which will execute the body of the asynchronous generator function until the next [`yield`](https://docs.python.org/3/reference/simple_stmts.html#yield) expression.

Each [`yield`](https://docs.python.org/3/reference/simple_stmts.html#yield) temporarily suspends processing, remembering the location execution state (including local variables and pending try-statements). When the _asynchronous generator iterator_ effectively resumes with another awaitable returned by `__anext__()`, it picks up where it left off. See [**PEP 492**](https://www.python.org/dev/peps/pep-0492) and [**PEP 525**](https://www.python.org/dev/peps/pep-0525).

asynchronous iterable

An object, that can be used in an [`async for`](https://docs.python.org/3/reference/compound_stmts.html#async-for) statement. Must return an [asynchronous iterator](https://docs.python.org/3/glossary.html#term-asynchronous-iterator) from its `__aiter__()` method. Introduced by [**PEP 492**](https://www.python.org/dev/peps/pep-0492).

asynchronous iterator

An object that implements the `__aiter__()` and `__anext__()` methods. `__anext__` must return an [awaitable](https://docs.python.org/3/glossary.html#term-awaitable) object. [`async for`](https://docs.python.org/3/reference/compound_stmts.html#async-for) resolves the awaitables returned by an asynchronous iterator’s `__anext__()` method until it raises a [`StopAsyncIteration`](https://docs.python.org/3/library/exceptions.html#StopAsyncIteration "StopAsyncIteration") exception. Introduced by [**PEP 492**](https://www.python.org/dev/peps/pep-0492).

attribute

A value associated with an object which is referenced by name using dotted expressions. For example, if an object _o_ has an attribute _a_ it would be referenced as _o.a_.

awaitable

An object that can be used in an [`await`](https://docs.python.org/3/reference/expressions.html#await) expression. Can be a [coroutine](https://docs.python.org/3/glossary.html#term-coroutine) or an object with an `__await__()` method. See also [**PEP 492**](https://www.python.org/dev/peps/pep-0492).

BDFL

Benevolent Dictator For Life, a.k.a. [Guido van Rossum](https://gvanrossum.github.io/), Python’s creator.

binary file

A [file object](https://docs.python.org/3/glossary.html#term-file-object) able to read and write [bytes-like objects](https://docs.python.org/3/glossary.html#term-bytes-like-object). Examples of binary files are files opened in binary mode (`'rb'`, `'wb'` or `'rb+'`), `sys.stdin.buffer`, `sys.stdout.buffer`, and instances of [`io.BytesIO`](https://docs.python.org/3/library/io.html#io.BytesIO "io.BytesIO") and [`gzip.GzipFile`](https://docs.python.org/3/library/gzip.html#gzip.GzipFile "gzip.GzipFile").

See also [text file](https://docs.python.org/3/glossary.html#term-text-file) for a file object able to read and write [`str`](https://docs.python.org/3/library/stdtypes.html#str "str") objects.

borrowed reference

In Python’s C API, a borrowed reference is a reference to an object. It does not modify the object reference count. It becomes a dangling pointer if the object is destroyed. For example, a garbage collection can remove the last [strong reference](https://docs.python.org/3/glossary.html#term-strong-reference) to the object and so destroy it.

Calling [`Py_INCREF()`](https://docs.python.org/3/c-api/refcounting.html#c.Py_INCREF "Py_INCREF") on the [borrowed reference](https://docs.python.org/3/glossary.html#term-borrowed-reference) is recommended to convert it to a [strong reference](https://docs.python.org/3/glossary.html#term-strong-reference) in-place, except when the object cannot be destroyed before the last usage of the borrowed reference. The [`Py_NewRef()`](https://docs.python.org/3/c-api/refcounting.html#c.Py_NewRef "Py_NewRef") function can be used to create a new [strong reference](https://docs.python.org/3/glossary.html#term-strong-reference).

bytes-like object

An object that supports the [Buffer Protocol](https://docs.python.org/3/c-api/buffer.html#bufferobjects) and can export a C-[contiguous](https://docs.python.org/3/glossary.html#term-contiguous) buffer. This includes all [`bytes`](https://docs.python.org/3/library/stdtypes.html#bytes "bytes"), [`bytearray`](https://docs.python.org/3/library/stdtypes.html#bytearray "bytearray"), and [`array.array`](https://docs.python.org/3/library/array.html#array.array "array.array") objects, as well as many common [`memoryview`](https://docs.python.org/3/library/stdtypes.html#memoryview "memoryview") objects. Bytes-like objects can be used for various operations that work with binary data; these include compression, saving to a binary file, and sending over a socket.

Some operations need the binary data to be mutable. The documentation often refers to these as “read-write bytes-like objects”. Example mutable buffer objects include [`bytearray`](https://docs.python.org/3/library/stdtypes.html#bytearray "bytearray") and a [`memoryview`](https://docs.python.org/3/library/stdtypes.html#memoryview "memoryview") of a [`bytearray`](https://docs.python.org/3/library/stdtypes.html#bytearray "bytearray"). Other operations require the binary data to be stored in immutable objects (“read-only bytes-like objects”); examples of these include [`bytes`](https://docs.python.org/3/library/stdtypes.html#bytes "bytes") and a [`memoryview`](https://docs.python.org/3/library/stdtypes.html#memoryview "memoryview") of a [`bytes`](https://docs.python.org/3/library/stdtypes.html#bytes "bytes") object.

bytecode

Python source code is compiled into bytecode, the internal representation of a Python program in the CPython interpreter. The bytecode is also cached in `.pyc` files so that executing the same file is faster the second time (recompilation from source to bytecode can be avoided). This “intermediate language” is said to run on a [virtual machine](https://docs.python.org/3/glossary.html#term-virtual-machine) that executes the machine code corresponding to each bytecode. Do note that bytecodes are not expected to work between different Python virtual machines, nor to be stable between Python releases.

A list of bytecode instructions can be found in the documentation for [the dis module](https://docs.python.org/3/library/dis.html#bytecodes).

callback

A subroutine function which is passed as an argument to be executed at some point in the future.

class

A template for creating user-defined objects. Class definitions normally contain method definitions which operate on instances of the class.

class variable

A variable defined in a class and intended to be modified only at class level (i.e., not in an instance of the class).

coercion

The implicit conversion of an instance of one type to another during an operation which involves two arguments of the same type. For example, `int(3.15)` converts the floating point number to the integer `3`, but in `3+4.5`, each argument is of a different type (one int, one float), and both must be converted to the same type before they can be added or it will raise a [`TypeError`](https://docs.python.org/3/library/exceptions.html#TypeError "TypeError"). Without coercion, all arguments of even compatible types would have to be normalized to the same value by the programmer, e.g., `float(3)+4.5` rather than just `3+4.5`.

complex number

An extension of the familiar real number system in which all numbers are expressed as a sum of a real part and an imaginary part. Imaginary numbers are real multiples of the imaginary unit (the square root of `-1`), often written `i` in mathematics or `j` in engineering. Python has built-in support for complex numbers, which are written with this latter notation; the imaginary part is written with a `j` suffix, e.g., `3+1j`. To get access to complex equivalents of the [`math`](https://docs.python.org/3/library/math.html#module-math "math: Mathematical functions (sin() etc.).") module, use [`cmath`](https://docs.python.org/3/library/cmath.html#module-cmath "cmath: Mathematical functions for complex numbers."). Use of complex numbers is a fairly advanced mathematical feature. If you’re not aware of a need for them, it’s almost certain you can safely ignore them.

context manager

An object which controls the environment seen in a [`with`](https://docs.python.org/3/reference/compound_stmts.html#with) statement by defining `__enter__()` and `__exit__()` methods. See [**PEP 343**](https://www.python.org/dev/peps/pep-0343).

context variable

A variable which can have different values depending on its context. This is similar to Thread-Local Storage in which each execution thread may have a different value for a variable. However, with context variables, there may be several contexts in one execution thread and the main usage for context variables is to keep track of variables in concurrent asynchronous tasks. See [`contextvars`](https://docs.python.org/3/library/contextvars.html#module-contextvars "contextvars: Context Variables").

contiguous

A buffer is considered contiguous exactly if it is either _C-contiguous_ or _Fortran contiguous_. Zero-dimensional buffers are C and Fortran contiguous. In one-dimensional arrays, the items must be laid out in memory next to each other, in order of increasing indexes starting from zero. In multidimensional C-contiguous arrays, the last index varies the fastest when visiting items in order of memory address. However, in Fortran contiguous arrays, the first index varies the fastest.

coroutine

Coroutines are a more generalized form of subroutines. Subroutines are entered at one point and exited at another point. Coroutines can be entered, exited, and resumed at many different points. They can be implemented with the [`async def`](https://docs.python.org/3/reference/compound_stmts.html#async-def) statement. See also [**PEP 492**](https://www.python.org/dev/peps/pep-0492).

coroutine function

A function which returns a [coroutine](https://docs.python.org/3/glossary.html#term-coroutine) object. A coroutine function may be defined with the [`async def`](https://docs.python.org/3/reference/compound_stmts.html#async-def) statement, and may contain [`await`](https://docs.python.org/3/reference/expressions.html#await), [`async for`](https://docs.python.org/3/reference/compound_stmts.html#async-for), and [`async with`](https://docs.python.org/3/reference/compound_stmts.html#async-with) keywords. These were introduced by [**PEP 492**](https://www.python.org/dev/peps/pep-0492).

CPython

The canonical implementation of the Python programming language, as distributed on [python.org](https://www.python.org/). The term “CPython” is used when necessary to distinguish this implementation from others such as Jython or IronPython.

decorator

A function returning another function, usually applied as a function transformation using the `@wrapper` syntax. Common examples for decorators are [`classmethod()`](https://docs.python.org/3/library/functions.html#classmethod "classmethod") and [`staticmethod()`](https://docs.python.org/3/library/functions.html#staticmethod "staticmethod").

The decorator syntax is merely syntactic sugar, the following two function definitions are semantically equivalent:

def f(arg):
    ...
f = staticmethod(f)

@staticmethod
def f(arg):
    ...

The same concept exists for classes, but is less commonly used there. See the documentation for [function definitions](https://docs.python.org/3/reference/compound_stmts.html#function) and [class definitions](https://docs.python.org/3/reference/compound_stmts.html#class) for more about decorators.

descriptor

Any object which defines the methods `__get__()`, `__set__()`, or `__delete__()`. When a class attribute is a descriptor, its special binding behavior is triggered upon attribute lookup. Normally, using _a.b_ to get, set or delete an attribute looks up the object named _b_ in the class dictionary for _a_, but if _b_ is a descriptor, the respective descriptor method gets called. Understanding descriptors is a key to a deep understanding of Python because they are the basis for many features including functions, methods, properties, class methods, static methods, and reference to super classes.

For more information about descriptors’ methods, see [Implementing Descriptors](https://docs.python.org/3/reference/datamodel.html#descriptors) or the [Descriptor How To Guide](https://docs.python.org/3/howto/descriptor.html#descriptorhowto).

dictionary

An associative array, where arbitrary keys are mapped to values. The keys can be any object with `__hash__()` and `__eq__()` methods. Called a hash in Perl.

dictionary comprehension

A compact way to process all or part of the elements in an iterable and return a dictionary with the results. `results = {n: n ** 2 for n in range(10)}` generates a dictionary containing key `n` mapped to value `n ** 2`. See [Displays for lists, sets and dictionaries](https://docs.python.org/3/reference/expressions.html#comprehensions).

dictionary view

The objects returned from [`dict.keys()`](https://docs.python.org/3/library/stdtypes.html#dict.keys "dict.keys"), [`dict.values()`](https://docs.python.org/3/library/stdtypes.html#dict.values "dict.values"), and [`dict.items()`](https://docs.python.org/3/library/stdtypes.html#dict.items "dict.items") are called dictionary views. They provide a dynamic view on the dictionary’s entries, which means that when the dictionary changes, the view reflects these changes. To force the dictionary view to become a full list use `list(dictview)`. See [Dictionary view objects](https://docs.python.org/3/library/stdtypes.html#dict-views).

docstring

A string literal which appears as the first expression in a class, function or module. While ignored when the suite is executed, it is recognized by the compiler and put into the `__doc__` attribute of the enclosing class, function or module. Since it is available via introspection, it is the canonical place for documentation of the object.

duck-typing

A programming style which does not look at an object’s type to determine if it has the right interface; instead, the method or attribute is simply called or used (“If it looks like a duck and quacks like a duck, it must be a duck.”) By emphasizing interfaces rather than specific types, well-designed code improves its flexibility by allowing polymorphic substitution. Duck-typing avoids tests using [`type()`](https://docs.python.org/3/library/functions.html#type "type") or [`isinstance()`](https://docs.python.org/3/library/functions.html#isinstance "isinstance"). (Note, however, that duck-typing can be complemented with [abstract base classes](https://docs.python.org/3/glossary.html#term-abstract-base-class).) Instead, it typically employs [`hasattr()`](https://docs.python.org/3/library/functions.html#hasattr "hasattr") tests or [EAFP](https://docs.python.org/3/glossary.html#term-EAFP) programming.

EAFP

Easier to ask for forgiveness than permission. This common Python coding style assumes the existence of valid keys or attributes and catches exceptions if the assumption proves false. This clean and fast style is characterized by the presence of many [`try`](https://docs.python.org/3/reference/compound_stmts.html#try) and [`except`](https://docs.python.org/3/reference/compound_stmts.html#except) statements. The technique contrasts with the [LBYL](https://docs.python.org/3/glossary.html#term-LBYL) style common to many other languages such as C.

expression

A piece of syntax which can be evaluated to some value. In other words, an expression is an accumulation of expression elements like literals, names, attribute access, operators or function calls which all return a value. In contrast to many other languages, not all language constructs are expressions. There are also [statement](https://docs.python.org/3/glossary.html#term-statement)s which cannot be used as expressions, such as [`while`](https://docs.python.org/3/reference/compound_stmts.html#while). Assignments are also statements, not expressions.

extension module

A module written in C or C++, using Python’s C API to interact with the core and with user code.

f-string

String literals prefixed with `'f'` or `'F'` are commonly called “f-strings” which is short for [formatted string literals](https://docs.python.org/3/reference/lexical_analysis.html#f-strings). See also [**PEP 498**](https://www.python.org/dev/peps/pep-0498).

file object

An object exposing a file-oriented API (with methods such as `read()` or `write()`) to an underlying resource. Depending on the way it was created, a file object can mediate access to a real on-disk file or to another type of storage or communication device (for example standard input/output, in-memory buffers, sockets, pipes, etc.). File objects are also called _file-like objects_ or _streams_.

There are actually three categories of file objects: raw [binary files](https://docs.python.org/3/glossary.html#term-binary-file), buffered [binary files](https://docs.python.org/3/glossary.html#term-binary-file) and [text files](https://docs.python.org/3/glossary.html#term-text-file). Their interfaces are defined in the [`io`](https://docs.python.org/3/library/io.html#module-io "io: Core tools for working with streams.") module. The canonical way to create a file object is by using the [`open()`](https://docs.python.org/3/library/functions.html#open "open") function.

file-like object

A synonym for [file object](https://docs.python.org/3/glossary.html#term-file-object).

filesystem encoding and error handler

Encoding and error handler used by Python to decode bytes from the operating system and encode Unicode to the operating system.

The filesystem encoding must guarantee to successfully decode all bytes below 128. If the file system encoding fails to provide this guarantee, API functions can raise [`UnicodeError`](https://docs.python.org/3/library/exceptions.html#UnicodeError "UnicodeError").

The [`sys.getfilesystemencoding()`](https://docs.python.org/3/library/sys.html#sys.getfilesystemencoding "sys.getfilesystemencoding") and [`sys.getfilesystemencodeerrors()`](https://docs.python.org/3/library/sys.html#sys.getfilesystemencodeerrors "sys.getfilesystemencodeerrors") functions can be used to get the filesystem encoding and error handler.

The [filesystem encoding and error handler](https://docs.python.org/3/glossary.html#term-filesystem-encoding-and-error-handler) are configured at Python startup by the `PyConfig_Read()` function: see [`filesystem_encoding`](https://docs.python.org/3/c-api/init_config.html#c.PyConfig.filesystem_encoding "PyConfig.filesystem_encoding") and [`filesystem_errors`](https://docs.python.org/3/c-api/init_config.html#c.PyConfig.filesystem_errors "PyConfig.filesystem_errors") members of [`PyConfig`](https://docs.python.org/3/c-api/init_config.html#c.PyConfig "PyConfig").

See also the [locale encoding](https://docs.python.org/3/glossary.html#term-locale-encoding).

finder

An object that tries to find the [loader](https://docs.python.org/3/glossary.html#term-loader) for a module that is being imported.

Since Python 3.3, there are two types of finder: [meta path finders](https://docs.python.org/3/glossary.html#term-meta-path-finder) for use with [`sys.meta_path`](https://docs.python.org/3/library/sys.html#sys.meta_path "sys.meta_path"), and [path entry finders](https://docs.python.org/3/glossary.html#term-path-entry-finder) for use with [`sys.path_hooks`](https://docs.python.org/3/library/sys.html#sys.path_hooks "sys.path_hooks").

See [**PEP 302**](https://www.python.org/dev/peps/pep-0302), [**PEP 420**](https://www.python.org/dev/peps/pep-0420) and [**PEP 451**](https://www.python.org/dev/peps/pep-0451) for much more detail.

floor division

Mathematical division that rounds down to nearest integer. The floor division operator is `//`. For example, the expression `11 // 4` evaluates to `2` in contrast to the `2.75` returned by float true division. Note that `(-11) // 4` is `-3` because that is `-2.75` rounded _downward_. See [**PEP 238**](https://www.python.org/dev/peps/pep-0238).

function

A series of statements which returns some value to a caller. It can also be passed zero or more [arguments](https://docs.python.org/3/glossary.html#term-argument) which may be used in the execution of the body. See also [parameter](https://docs.python.org/3/glossary.html#term-parameter), [method](https://docs.python.org/3/glossary.html#term-method), and the [Function definitions](https://docs.python.org/3/reference/compound_stmts.html#function) section.

function annotation

An [annotation](https://docs.python.org/3/glossary.html#term-annotation) of a function parameter or return value.

Function annotations are usually used for [type hints](https://docs.python.org/3/glossary.html#term-type-hint): for example, this function is expected to take two [`int`](https://docs.python.org/3/library/functions.html#int "int") arguments and is also expected to have an [`int`](https://docs.python.org/3/library/functions.html#int "int") return value:

def sum_two_numbers(a: int, b: int) -> int:
   return a + b

Function annotation syntax is explained in section [Function definitions](https://docs.python.org/3/reference/compound_stmts.html#function).

See [variable annotation](https://docs.python.org/3/glossary.html#term-variable-annotation) and [**PEP 484**](https://www.python.org/dev/peps/pep-0484), which describe this functionality. Also see [Annotations Best Practices](https://docs.python.org/3/howto/annotations.html#annotations-howto) for best practices on working with annotations.

__future__

A [future statement](https://docs.python.org/3/reference/simple_stmts.html#future), `from __future__ import <feature>`, directs the compiler to compile the current module using syntax or semantics that will become standard in a future release of Python. The [`__future__`](https://docs.python.org/3/library/__future__.html#module-__future__ "__future__: Future statement definitions") module documents the possible values of _feature_. By importing this module and evaluating its variables, you can see when a new feature was first added to the language and when it will (or did) become the default:

>>>

>>> import __future__
>>> __future__.division
_Feature((2, 2, 0, 'alpha', 2), (3, 0, 0, 'alpha', 0), 8192)

garbage collection

The process of freeing memory when it is not used anymore. Python performs garbage collection via reference counting and a cyclic garbage collector that is able to detect and break reference cycles. The garbage collector can be controlled using the [`gc`](https://docs.python.org/3/library/gc.html#module-gc "gc: Interface to the cycle-detecting garbage collector.") module.

generator

A function which returns a [generator iterator](https://docs.python.org/3/glossary.html#term-generator-iterator). It looks like a normal function except that it contains [`yield`](https://docs.python.org/3/reference/simple_stmts.html#yield) expressions for producing a series of values usable in a for-loop or that can be retrieved one at a time with the [`next()`](https://docs.python.org/3/library/functions.html#next "next") function.

Usually refers to a generator function, but may refer to a _generator iterator_ in some contexts. In cases where the intended meaning isn’t clear, using the full terms avoids ambiguity.

generator iterator

An object created by a [generator](https://docs.python.org/3/glossary.html#term-generator) function.

Each [`yield`](https://docs.python.org/3/reference/simple_stmts.html#yield) temporarily suspends processing, remembering the location execution state (including local variables and pending try-statements). When the _generator iterator_ resumes, it picks up where it left off (in contrast to functions which start fresh on every invocation).

generator expression

An expression that returns an iterator. It looks like a normal expression followed by a `for` clause defining a loop variable, range, and an optional `if` clause. The combined expression generates values for an enclosing function:

>>>

>>> sum(i*i for i in range(10))         # sum of squares 0, 1, 4, ... 81
285

generic function

A function composed of multiple functions implementing the same operation for different types. Which implementation should be used during a call is determined by the dispatch algorithm.

See also the [single dispatch](https://docs.python.org/3/glossary.html#term-single-dispatch) glossary entry, the [`functools.singledispatch()`](https://docs.python.org/3/library/functools.html#functools.singledispatch "functools.singledispatch") decorator, and [**PEP 443**](https://www.python.org/dev/peps/pep-0443).

generic type

A [type](https://docs.python.org/3/glossary.html#term-type) that can be parameterized; typically a [container class](https://docs.python.org/3/reference/datamodel.html#sequence-types) such as [`list`](https://docs.python.org/3/library/stdtypes.html#list "list") or [`dict`](https://docs.python.org/3/library/stdtypes.html#dict "dict"). Used for [type hints](https://docs.python.org/3/glossary.html#term-type-hint) and [annotations](https://docs.python.org/3/glossary.html#term-annotation).

For more details, see [generic alias types](https://docs.python.org/3/library/stdtypes.html#types-genericalias), [**PEP 483**](https://www.python.org/dev/peps/pep-0483), [**PEP 484**](https://www.python.org/dev/peps/pep-0484), [**PEP 585**](https://www.python.org/dev/peps/pep-0585), and the [`typing`](https://docs.python.org/3/library/typing.html#module-typing "typing: Support for type hints (see :pep:`484`).") module.

GIL

See [global interpreter lock](https://docs.python.org/3/glossary.html#term-global-interpreter-lock).

global interpreter lock

The mechanism used by the [CPython](https://docs.python.org/3/glossary.html#term-CPython) interpreter to assure that only one thread executes Python [bytecode](https://docs.python.org/3/glossary.html#term-bytecode) at a time. This simplifies the CPython implementation by making the object model (including critical built-in types such as [`dict`](https://docs.python.org/3/library/stdtypes.html#dict "dict")) implicitly safe against concurrent access. Locking the entire interpreter makes it easier for the interpreter to be multi-threaded, at the expense of much of the parallelism afforded by multi-processor machines.

However, some extension modules, either standard or third-party, are designed so as to release the GIL when doing computationally-intensive tasks such as compression or hashing. Also, the GIL is always released when doing I/O.

Past efforts to create a “free-threaded” interpreter (one which locks shared data at a much finer granularity) have not been successful because performance suffered in the common single-processor case. It is believed that overcoming this performance issue would make the implementation much more complicated and therefore costlier to maintain.

hash-based pyc

A bytecode cache file that uses the hash rather than the last-modified time of the corresponding source file to determine its validity. See [Cached bytecode invalidation](https://docs.python.org/3/reference/import.html#pyc-invalidation).

hashable

An object is _hashable_ if it has a hash value which never changes during its lifetime (it needs a `__hash__()` method), and can be compared to other objects (it needs an `__eq__()` method). Hashable objects which compare equal must have the same hash value.

Hashability makes an object usable as a dictionary key and a set member, because these data structures use the hash value internally.

Most of Python’s immutable built-in objects are hashable; mutable containers (such as lists or dictionaries) are not; immutable containers (such as tuples and frozensets) are only hashable if their elements are hashable. Objects which are instances of user-defined classes are hashable by default. They all compare unequal (except with themselves), and their hash value is derived from their [`id()`](https://docs.python.org/3/library/functions.html#id "id").

IDLE

An Integrated Development Environment for Python. IDLE is a basic editor and interpreter environment which ships with the standard distribution of Python.

immutable

An object with a fixed value. Immutable objects include numbers, strings and tuples. Such an object cannot be altered. A new object has to be created if a different value has to be stored. They play an important role in places where a constant hash value is needed, for example as a key in a dictionary.

import path

A list of locations (or [path entries](https://docs.python.org/3/glossary.html#term-path-entry)) that are searched by the [path based finder](https://docs.python.org/3/glossary.html#term-path-based-finder) for modules to import. During import, this list of locations usually comes from [`sys.path`](https://docs.python.org/3/library/sys.html#sys.path "sys.path"), but for subpackages it may also come from the parent package’s `__path__` attribute.

importing

The process by which Python code in one module is made available to Python code in another module.

importer

An object that both finds and loads a module; both a [finder](https://docs.python.org/3/glossary.html#term-finder) and [loader](https://docs.python.org/3/glossary.html#term-loader) object.

interactive

Python has an interactive interpreter which means you can enter statements and expressions at the interpreter prompt, immediately execute them and see their results. Just launch `python` with no arguments (possibly by selecting it from your computer’s main menu). It is a very powerful way to test out new ideas or inspect modules and packages (remember `help(x)`).

interpreted

Python is an interpreted language, as opposed to a compiled one, though the distinction can be blurry because of the presence of the bytecode compiler. This means that source files can be run directly without explicitly creating an executable which is then run. Interpreted languages typically have a shorter development/debug cycle than compiled ones, though their programs generally also run more slowly. See also [interactive](https://docs.python.org/3/glossary.html#term-interactive).

interpreter shutdown

When asked to shut down, the Python interpreter enters a special phase where it gradually releases all allocated resources, such as modules and various critical internal structures. It also makes several calls to the [garbage collector](https://docs.python.org/3/glossary.html#term-garbage-collection). This can trigger the execution of code in user-defined destructors or weakref callbacks. Code executed during the shutdown phase can encounter various exceptions as the resources it relies on may not function anymore (common examples are library modules or the warnings machinery).

The main reason for interpreter shutdown is that the `__main__` module or the script being run has finished executing.

iterable

An object capable of returning its members one at a time. Examples of iterables include all sequence types (such as [`list`](https://docs.python.org/3/library/stdtypes.html#list "list"), [`str`](https://docs.python.org/3/library/stdtypes.html#str "str"), and [`tuple`](https://docs.python.org/3/library/stdtypes.html#tuple "tuple")) and some non-sequence types like [`dict`](https://docs.python.org/3/library/stdtypes.html#dict "dict"), [file objects](https://docs.python.org/3/glossary.html#term-file-object), and objects of any classes you define with an `__iter__()` method or with a `__getitem__()` method that implements [Sequence](https://docs.python.org/3/glossary.html#term-sequence) semantics.

Iterables can be used in a [`for`](https://docs.python.org/3/reference/compound_stmts.html#for) loop and in many other places where a sequence is needed ([`zip()`](https://docs.python.org/3/library/functions.html#zip "zip"), [`map()`](https://docs.python.org/3/library/functions.html#map "map"), …). When an iterable object is passed as an argument to the built-in function [`iter()`](https://docs.python.org/3/library/functions.html#iter "iter"), it returns an iterator for the object. This iterator is good for one pass over the set of values. When using iterables, it is usually not necessary to call [`iter()`](https://docs.python.org/3/library/functions.html#iter "iter") or deal with iterator objects yourself. The `for` statement does that automatically for you, creating a temporary unnamed variable to hold the iterator for the duration of the loop. See also [iterator](https://docs.python.org/3/glossary.html#term-iterator), [sequence](https://docs.python.org/3/glossary.html#term-sequence), and [generator](https://docs.python.org/3/glossary.html#term-generator).

iterator

An object representing a stream of data. Repeated calls to the iterator’s [`__next__()`](https://docs.python.org/3/library/stdtypes.html#iterator.__next__ "iterator.__next__") method (or passing it to the built-in function [`next()`](https://docs.python.org/3/library/functions.html#next "next")) return successive items in the stream. When no more data are available a [`StopIteration`](https://docs.python.org/3/library/exceptions.html#StopIteration "StopIteration") exception is raised instead. At this point, the iterator object is exhausted and any further calls to its `__next__()` method just raise [`StopIteration`](https://docs.python.org/3/library/exceptions.html#StopIteration "StopIteration") again. Iterators are required to have an `__iter__()` method that returns the iterator object itself so every iterator is also iterable and may be used in most places where other iterables are accepted. One notable exception is code which attempts multiple iteration passes. A container object (such as a [`list`](https://docs.python.org/3/library/stdtypes.html#list "list")) produces a fresh new iterator each time you pass it to the [`iter()`](https://docs.python.org/3/library/functions.html#iter "iter") function or use it in a [`for`](https://docs.python.org/3/reference/compound_stmts.html#for) loop. Attempting this with an iterator will just return the same exhausted iterator object used in the previous iteration pass, making it appear like an empty container.

More information can be found in [Iterator Types](https://docs.python.org/3/library/stdtypes.html#typeiter).

**CPython implementation detail:** CPython does not consistently apply the requirement that an iterator define `__iter__()`.

key function

A key function or collation function is a callable that returns a value used for sorting or ordering. For example, [`locale.strxfrm()`](https://docs.python.org/3/library/locale.html#locale.strxfrm "locale.strxfrm") is used to produce a sort key that is aware of locale specific sort conventions.

A number of tools in Python accept key functions to control how elements are ordered or grouped. They include [`min()`](https://docs.python.org/3/library/functions.html#min "min"), [`max()`](https://docs.python.org/3/library/functions.html#max "max"), [`sorted()`](https://docs.python.org/3/library/functions.html#sorted "sorted"), [`list.sort()`](https://docs.python.org/3/library/stdtypes.html#list.sort "list.sort"), [`heapq.merge()`](https://docs.python.org/3/library/heapq.html#heapq.merge "heapq.merge"), [`heapq.nsmallest()`](https://docs.python.org/3/library/heapq.html#heapq.nsmallest "heapq.nsmallest"), [`heapq.nlargest()`](https://docs.python.org/3/library/heapq.html#heapq.nlargest "heapq.nlargest"), and [`itertools.groupby()`](https://docs.python.org/3/library/itertools.html#itertools.groupby "itertools.groupby").

There are several ways to create a key function. For example. the [`str.lower()`](https://docs.python.org/3/library/stdtypes.html#str.lower "str.lower") method can serve as a key function for case insensitive sorts. Alternatively, a key function can be built from a [`lambda`](https://docs.python.org/3/reference/expressions.html#lambda) expression such as `lambda r: (r[0], r[2])`. Also, the [`operator`](https://docs.python.org/3/library/operator.html#module-operator "operator: Functions corresponding to the standard operators.") module provides three key function constructors: [`attrgetter()`](https://docs.python.org/3/library/operator.html#operator.attrgetter "operator.attrgetter"), [`itemgetter()`](https://docs.python.org/3/library/operator.html#operator.itemgetter "operator.itemgetter"), and [`methodcaller()`](https://docs.python.org/3/library/operator.html#operator.methodcaller "operator.methodcaller"). See the [Sorting HOW TO](https://docs.python.org/3/howto/sorting.html#sortinghowto) for examples of how to create and use key functions.

keyword argument

See [argument](https://docs.python.org/3/glossary.html#term-argument).

lambda

An anonymous inline function consisting of a single [expression](https://docs.python.org/3/glossary.html#term-expression) which is evaluated when the function is called. The syntax to create a lambda function is `lambda [parameters]: expression`

LBYL

Look before you leap. This coding style explicitly tests for pre-conditions before making calls or lookups. This style contrasts with the [EAFP](https://docs.python.org/3/glossary.html#term-EAFP) approach and is characterized by the presence of many [`if`](https://docs.python.org/3/reference/compound_stmts.html#if) statements.

In a multi-threaded environment, the LBYL approach can risk introducing a race condition between “the looking” and “the leaping”. For example, the code, `if key in mapping: return mapping[key]` can fail if another thread removes _key_ from _mapping_ after the test, but before the lookup. This issue can be solved with locks or by using the EAFP approach.

locale encoding

On Unix, it is the encoding of the LC_CTYPE locale. It can be set with `locale.setlocale(locale.LC_CTYPE, new_locale)`.

On Windows, it is the ANSI code page (ex: `cp1252`).

`locale.getpreferredencoding(False)` can be used to get the locale encoding.

Python uses the [filesystem encoding and error handler](https://docs.python.org/3/glossary.html#term-filesystem-encoding-and-error-handler) to convert between Unicode filenames and bytes filenames.

list

A built-in Python [sequence](https://docs.python.org/3/glossary.html#term-sequence). Despite its name it is more akin to an array in other languages than to a linked list since access to elements is O(1).

list comprehension

A compact way to process all or part of the elements in a sequence and return a list with the results. `result = ['{:#04x}'.format(x) for x in range(256) if x % 2 == 0]` generates a list of strings containing even hex numbers (0x..) in the range from 0 to 255. The [`if`](https://docs.python.org/3/reference/compound_stmts.html#if) clause is optional. If omitted, all elements in `range(256)` are processed.

loader

An object that loads a module. It must define a method named `load_module()`. A loader is typically returned by a [finder](https://docs.python.org/3/glossary.html#term-finder). See [**PEP 302**](https://www.python.org/dev/peps/pep-0302) for details and [`importlib.abc.Loader`](https://docs.python.org/3/library/importlib.html#importlib.abc.Loader "importlib.abc.Loader") for an [abstract base class](https://docs.python.org/3/glossary.html#term-abstract-base-class).

magic method

An informal synonym for [special method](https://docs.python.org/3/glossary.html#term-special-method).

mapping

A container object that supports arbitrary key lookups and implements the methods specified in the [`Mapping`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Mapping "collections.abc.Mapping") or [`MutableMapping`](https://docs.python.org/3/library/collections.abc.html#collections.abc.MutableMapping "collections.abc.MutableMapping") [abstract base classes](https://docs.python.org/3/library/collections.abc.html#collections-abstract-base-classes). Examples include [`dict`](https://docs.python.org/3/library/stdtypes.html#dict "dict"), [`collections.defaultdict`](https://docs.python.org/3/library/collections.html#collections.defaultdict "collections.defaultdict"), [`collections.OrderedDict`](https://docs.python.org/3/library/collections.html#collections.OrderedDict "collections.OrderedDict") and [`collections.Counter`](https://docs.python.org/3/library/collections.html#collections.Counter "collections.Counter").

meta path finder

A [finder](https://docs.python.org/3/glossary.html#term-finder) returned by a search of [`sys.meta_path`](https://docs.python.org/3/library/sys.html#sys.meta_path "sys.meta_path"). Meta path finders are related to, but different from [path entry finders](https://docs.python.org/3/glossary.html#term-path-entry-finder).

See [`importlib.abc.MetaPathFinder`](https://docs.python.org/3/library/importlib.html#importlib.abc.MetaPathFinder "importlib.abc.MetaPathFinder") for the methods that meta path finders implement.

metaclass

The class of a class. Class definitions create a class name, a class dictionary, and a list of base classes. The metaclass is responsible for taking those three arguments and creating the class. Most object oriented programming languages provide a default implementation. What makes Python special is that it is possible to create custom metaclasses. Most users never need this tool, but when the need arises, metaclasses can provide powerful, elegant solutions. They have been used for logging attribute access, adding thread-safety, tracking object creation, implementing singletons, and many other tasks.

More information can be found in [Metaclasses](https://docs.python.org/3/reference/datamodel.html#metaclasses).

method

A function which is defined inside a class body. If called as an attribute of an instance of that class, the method will get the instance object as its first [argument](https://docs.python.org/3/glossary.html#term-argument) (which is usually called `self`). See [function](https://docs.python.org/3/glossary.html#term-function) and [nested scope](https://docs.python.org/3/glossary.html#term-nested-scope).

method resolution order

Method Resolution Order is the order in which base classes are searched for a member during lookup. See [The Python 2.3 Method Resolution Order](https://www.python.org/download/releases/2.3/mro/) for details of the algorithm used by the Python interpreter since the 2.3 release.

module

An object that serves as an organizational unit of Python code. Modules have a namespace containing arbitrary Python objects. Modules are loaded into Python by the process of [importing](https://docs.python.org/3/glossary.html#term-importing).

See also [package](https://docs.python.org/3/glossary.html#term-package).

module spec

A namespace containing the import-related information used to load a module. An instance of [`importlib.machinery.ModuleSpec`](https://docs.python.org/3/library/importlib.html#importlib.machinery.ModuleSpec "importlib.machinery.ModuleSpec").

MRO

See [method resolution order](https://docs.python.org/3/glossary.html#term-method-resolution-order).

mutable

Mutable objects can change their value but keep their [`id()`](https://docs.python.org/3/library/functions.html#id "id"). See also [immutable](https://docs.python.org/3/glossary.html#term-immutable).

named tuple

The term “named tuple” applies to any type or class that inherits from tuple and whose indexable elements are also accessible using named attributes. The type or class may have other features as well.

Several built-in types are named tuples, including the values returned by [`time.localtime()`](https://docs.python.org/3/library/time.html#time.localtime "time.localtime") and [`os.stat()`](https://docs.python.org/3/library/os.html#os.stat "os.stat"). Another example is [`sys.float_info`](https://docs.python.org/3/library/sys.html#sys.float_info "sys.float_info"):

>>>

>>> sys.float_info[1]                   # indexed access
1024
>>> sys.float_info.max_exp              # named field access
1024
>>> isinstance(sys.float_info, tuple)   # kind of tuple
True

Some named tuples are built-in types (such as the above examples). Alternatively, a named tuple can be created from a regular class definition that inherits from [`tuple`](https://docs.python.org/3/library/stdtypes.html#tuple "tuple") and that defines named fields. Such a class can be written by hand or it can be created with the factory function [`collections.namedtuple()`](https://docs.python.org/3/library/collections.html#collections.namedtuple "collections.namedtuple"). The latter technique also adds some extra methods that may not be found in hand-written or built-in named tuples.

namespace

The place where a variable is stored. Namespaces are implemented as dictionaries. There are the local, global and built-in namespaces as well as nested namespaces in objects (in methods). Namespaces support modularity by preventing naming conflicts. For instance, the functions [`builtins.open`](https://docs.python.org/3/library/functions.html#open "open") and [`os.open()`](https://docs.python.org/3/library/os.html#os.open "os.open") are distinguished by their namespaces. Namespaces also aid readability and maintainability by making it clear which module implements a function. For instance, writing [`random.seed()`](https://docs.python.org/3/library/random.html#random.seed "random.seed") or [`itertools.islice()`](https://docs.python.org/3/library/itertools.html#itertools.islice "itertools.islice") makes it clear that those functions are implemented by the [`random`](https://docs.python.org/3/library/random.html#module-random "random: Generate pseudo-random numbers with various common distributions.") and [`itertools`](https://docs.python.org/3/library/itertools.html#module-itertools "itertools: Functions creating iterators for efficient looping.") modules, respectively.

namespace package

A [**PEP 420**](https://www.python.org/dev/peps/pep-0420) [package](https://docs.python.org/3/glossary.html#term-package) which serves only as a container for subpackages. Namespace packages may have no physical representation, and specifically are not like a [regular package](https://docs.python.org/3/glossary.html#term-regular-package) because they have no `__init__.py` file.

See also [module](https://docs.python.org/3/glossary.html#term-module).

nested scope

The ability to refer to a variable in an enclosing definition. For instance, a function defined inside another function can refer to variables in the outer function. Note that nested scopes by default work only for reference and not for assignment. Local variables both read and write in the innermost scope. Likewise, global variables read and write to the global namespace. The [`nonlocal`](https://docs.python.org/3/reference/simple_stmts.html#nonlocal) allows writing to outer scopes.

new-style class

Old name for the flavor of classes now used for all class objects. In earlier Python versions, only new-style classes could use Python’s newer, versatile features like [`__slots__`](https://docs.python.org/3/reference/datamodel.html#object.__slots__ "object.__slots__"), descriptors, properties, `__getattribute__()`, class methods, and static methods.

object

Any data with state (attributes or value) and defined behavior (methods). Also the ultimate base class of any [new-style class](https://docs.python.org/3/glossary.html#term-new-style-class).

package

A Python [module](https://docs.python.org/3/glossary.html#term-module) which can contain submodules or recursively, subpackages. Technically, a package is a Python module with an `__path__` attribute.

See also [regular package](https://docs.python.org/3/glossary.html#term-regular-package) and [namespace package](https://docs.python.org/3/glossary.html#term-namespace-package).

parameter

A named entity in a [function](https://docs.python.org/3/glossary.html#term-function) (or method) definition that specifies an [argument](https://docs.python.org/3/glossary.html#term-argument) (or in some cases, arguments) that the function can accept. There are five kinds of parameter:

-   _positional-or-keyword_: specifies an argument that can be passed either [positionally](https://docs.python.org/3/glossary.html#term-argument) or as a [keyword argument](https://docs.python.org/3/glossary.html#term-argument). This is the default kind of parameter, for example _foo_ and _bar_ in the following:
    
    def func(foo, bar=None): ...
    

-   _positional-only_: specifies an argument that can be supplied only by position. Positional-only parameters can be defined by including a `/` character in the parameter list of the function definition after them, for example _posonly1_ and _posonly2_ in the following:
    
    def func(posonly1, posonly2, /, positional_or_keyword): ...
    

-   _keyword-only_: specifies an argument that can be supplied only by keyword. Keyword-only parameters can be defined by including a single var-positional parameter or bare `*` in the parameter list of the function definition before them, for example _kw_only1_ and _kw_only2_ in the following:
    
    def func(arg, *, kw_only1, kw_only2): ...
    
-   _var-positional_: specifies that an arbitrary sequence of positional arguments can be provided (in addition to any positional arguments already accepted by other parameters). Such a parameter can be defined by prepending the parameter name with `*`, for example _args_ in the following:
    
    def func(*args, **kwargs): ...
    
-   _var-keyword_: specifies that arbitrarily many keyword arguments can be provided (in addition to any keyword arguments already accepted by other parameters). Such a parameter can be defined by prepending the parameter name with `**`, for example _kwargs_ in the example above.
    

Parameters can specify both optional and required arguments, as well as default values for some optional arguments.

See also the [argument](https://docs.python.org/3/glossary.html#term-argument) glossary entry, the FAQ question on [the difference between arguments and parameters](https://docs.python.org/3/faq/programming.html#faq-argument-vs-parameter), the [`inspect.Parameter`](https://docs.python.org/3/library/inspect.html#inspect.Parameter "inspect.Parameter") class, the [Function definitions](https://docs.python.org/3/reference/compound_stmts.html#function) section, and [**PEP 362**](https://www.python.org/dev/peps/pep-0362).

path entry

A single location on the [import path](https://docs.python.org/3/glossary.html#term-import-path) which the [path based finder](https://docs.python.org/3/glossary.html#term-path-based-finder) consults to find modules for importing.

path entry finder

A [finder](https://docs.python.org/3/glossary.html#term-finder) returned by a callable on [`sys.path_hooks`](https://docs.python.org/3/library/sys.html#sys.path_hooks "sys.path_hooks") (i.e. a [path entry hook](https://docs.python.org/3/glossary.html#term-path-entry-hook)) which knows how to locate modules given a [path entry](https://docs.python.org/3/glossary.html#term-path-entry).

See [`importlib.abc.PathEntryFinder`](https://docs.python.org/3/library/importlib.html#importlib.abc.PathEntryFinder "importlib.abc.PathEntryFinder") for the methods that path entry finders implement.

path entry hook

A callable on the `sys.path_hook` list which returns a [path entry finder](https://docs.python.org/3/glossary.html#term-path-entry-finder) if it knows how to find modules on a specific [path entry](https://docs.python.org/3/glossary.html#term-path-entry).

path based finder

One of the default [meta path finders](https://docs.python.org/3/glossary.html#term-meta-path-finder) which searches an [import path](https://docs.python.org/3/glossary.html#term-import-path) for modules.

path-like object

An object representing a file system path. A path-like object is either a [`str`](https://docs.python.org/3/library/stdtypes.html#str "str") or [`bytes`](https://docs.python.org/3/library/stdtypes.html#bytes "bytes") object representing a path, or an object implementing the [`os.PathLike`](https://docs.python.org/3/library/os.html#os.PathLike "os.PathLike") protocol. An object that supports the [`os.PathLike`](https://docs.python.org/3/library/os.html#os.PathLike "os.PathLike") protocol can be converted to a [`str`](https://docs.python.org/3/library/stdtypes.html#str "str") or [`bytes`](https://docs.python.org/3/library/stdtypes.html#bytes "bytes") file system path by calling the [`os.fspath()`](https://docs.python.org/3/library/os.html#os.fspath "os.fspath") function; [`os.fsdecode()`](https://docs.python.org/3/library/os.html#os.fsdecode "os.fsdecode") and [`os.fsencode()`](https://docs.python.org/3/library/os.html#os.fsencode "os.fsencode") can be used to guarantee a [`str`](https://docs.python.org/3/library/stdtypes.html#str "str") or [`bytes`](https://docs.python.org/3/library/stdtypes.html#bytes "bytes") result instead, respectively. Introduced by [**PEP 519**](https://www.python.org/dev/peps/pep-0519).

PEP

Python Enhancement Proposal. A PEP is a design document providing information to the Python community, or describing a new feature for Python or its processes or environment. PEPs should provide a concise technical specification and a rationale for proposed features.

PEPs are intended to be the primary mechanisms for proposing major new features, for collecting community input on an issue, and for documenting the design decisions that have gone into Python. The PEP author is responsible for building consensus within the community and documenting dissenting opinions.

See [**PEP 1**](https://www.python.org/dev/peps/pep-0001).

portion

A set of files in a single directory (possibly stored in a zip file) that contribute to a namespace package, as defined in [**PEP 420**](https://www.python.org/dev/peps/pep-0420).

positional argument

See [argument](https://docs.python.org/3/glossary.html#term-argument).

provisional API

A provisional API is one which has been deliberately excluded from the standard library’s backwards compatibility guarantees. While major changes to such interfaces are not expected, as long as they are marked provisional, backwards incompatible changes (up to and including removal of the interface) may occur if deemed necessary by core developers. Such changes will not be made gratuitously – they will occur only if serious fundamental flaws are uncovered that were missed prior to the inclusion of the API.

Even for provisional APIs, backwards incompatible changes are seen as a “solution of last resort” - every attempt will still be made to find a backwards compatible resolution to any identified problems.

This process allows the standard library to continue to evolve over time, without locking in problematic design errors for extended periods of time. See [**PEP 411**](https://www.python.org/dev/peps/pep-0411) for more details.

provisional package

See [provisional API](https://docs.python.org/3/glossary.html#term-provisional-API).

Python 3000

Nickname for the Python 3.x release line (coined long ago when the release of version 3 was something in the distant future.) This is also abbreviated “Py3k”.

Pythonic

An idea or piece of code which closely follows the most common idioms of the Python language, rather than implementing code using concepts common to other languages. For example, a common idiom in Python is to loop over all elements of an iterable using a [`for`](https://docs.python.org/3/reference/compound_stmts.html#for) statement. Many other languages don’t have this type of construct, so people unfamiliar with Python sometimes use a numerical counter instead:

for i in range(len(food)):
    print(food[i])

As opposed to the cleaner, Pythonic method:

for piece in food:
    print(piece)

qualified name

A dotted name showing the “path” from a module’s global scope to a class, function or method defined in that module, as defined in [**PEP 3155**](https://www.python.org/dev/peps/pep-3155). For top-level functions and classes, the qualified name is the same as the object’s name:

>>>

>>> class C:
...     class D:
...         def meth(self):
...             pass
...
>>> C.__qualname__
'C'
>>> C.D.__qualname__
'C.D'
>>> C.D.meth.__qualname__
'C.D.meth'

When used to refer to modules, the _fully qualified name_ means the entire dotted path to the module, including any parent packages, e.g. `email.mime.text`:

>>>

>>> import email.mime.text
>>> email.mime.text.__name__
'email.mime.text'

reference count

The number of references to an object. When the reference count of an object drops to zero, it is deallocated. Reference counting is generally not visible to Python code, but it is a key element of the [CPython](https://docs.python.org/3/glossary.html#term-CPython) implementation. The [`sys`](https://docs.python.org/3/library/sys.html#module-sys "sys: Access system-specific parameters and functions.") module defines a [`getrefcount()`](https://docs.python.org/3/library/sys.html#sys.getrefcount "sys.getrefcount") function that programmers can call to return the reference count for a particular object.

regular package

A traditional [package](https://docs.python.org/3/glossary.html#term-package), such as a directory containing an `__init__.py` file.

See also [namespace package](https://docs.python.org/3/glossary.html#term-namespace-package).

__slots__

A declaration inside a class that saves memory by pre-declaring space for instance attributes and eliminating instance dictionaries. Though popular, the technique is somewhat tricky to get right and is best reserved for rare cases where there are large numbers of instances in a memory-critical application.

sequence

An [iterable](https://docs.python.org/3/glossary.html#term-iterable) which supports efficient element access using integer indices via the `__getitem__()` special method and defines a `__len__()` method that returns the length of the sequence. Some built-in sequence types are [`list`](https://docs.python.org/3/library/stdtypes.html#list "list"), [`str`](https://docs.python.org/3/library/stdtypes.html#str "str"), [`tuple`](https://docs.python.org/3/library/stdtypes.html#tuple "tuple"), and [`bytes`](https://docs.python.org/3/library/stdtypes.html#bytes "bytes"). Note that [`dict`](https://docs.python.org/3/library/stdtypes.html#dict "dict") also supports `__getitem__()` and `__len__()`, but is considered a mapping rather than a sequence because the lookups use arbitrary [immutable](https://docs.python.org/3/glossary.html#term-immutable) keys rather than integers.

The [`collections.abc.Sequence`](https://docs.python.org/3/library/collections.abc.html#collections.abc.Sequence "collections.abc.Sequence") abstract base class defines a much richer interface that goes beyond just `__getitem__()` and `__len__()`, adding `count()`, `index()`, `__contains__()`, and `__reversed__()`. Types that implement this expanded interface can be registered explicitly using [`register()`](https://docs.python.org/3/library/abc.html#abc.ABCMeta.register "abc.ABCMeta.register").

set comprehension

A compact way to process all or part of the elements in an iterable and return a set with the results. `results = {c for c in 'abracadabra' if c not in 'abc'}` generates the set of strings `{'r', 'd'}`. See [Displays for lists, sets and dictionaries](https://docs.python.org/3/reference/expressions.html#comprehensions).

single dispatch

A form of [generic function](https://docs.python.org/3/glossary.html#term-generic-function) dispatch where the implementation is chosen based on the type of a single argument.

slice

An object usually containing a portion of a [sequence](https://docs.python.org/3/glossary.html#term-sequence). A slice is created using the subscript notation, `[]` with colons between numbers when several are given, such as in `variable_name[1:3:5]`. The bracket (subscript) notation uses [`slice`](https://docs.python.org/3/library/functions.html#slice "slice") objects internally.

special method

A method that is called implicitly by Python to execute a certain operation on a type, such as addition. Such methods have names starting and ending with double underscores. Special methods are documented in [Special method names](https://docs.python.org/3/reference/datamodel.html#specialnames).

statement

A statement is part of a suite (a “block” of code). A statement is either an [expression](https://docs.python.org/3/glossary.html#term-expression) or one of several constructs with a keyword, such as [`if`](https://docs.python.org/3/reference/compound_stmts.html#if), [`while`](https://docs.python.org/3/reference/compound_stmts.html#while) or [`for`](https://docs.python.org/3/reference/compound_stmts.html#for).

strong reference

In Python’s C API, a strong reference is a reference to an object which increments the object’s reference count when it is created and decrements the object’s reference count when it is deleted.

The [`Py_NewRef()`](https://docs.python.org/3/c-api/refcounting.html#c.Py_NewRef "Py_NewRef") function can be used to create a strong reference to an object. Usually, the [`Py_DECREF()`](https://docs.python.org/3/c-api/refcounting.html#c.Py_DECREF "Py_DECREF") function must be called on the strong reference before exiting the scope of the strong reference, to avoid leaking one reference.

See also [borrowed reference](https://docs.python.org/3/glossary.html#term-borrowed-reference).

text encoding

A codec which encodes Unicode strings to bytes.

text file

A [file object](https://docs.python.org/3/glossary.html#term-file-object) able to read and write [`str`](https://docs.python.org/3/library/stdtypes.html#str "str") objects. Often, a text file actually accesses a byte-oriented datastream and handles the [text encoding](https://docs.python.org/3/glossary.html#term-text-encoding) automatically. Examples of text files are files opened in text mode (`'r'` or `'w'`), [`sys.stdin`](https://docs.python.org/3/library/sys.html#sys.stdin "sys.stdin"), [`sys.stdout`](https://docs.python.org/3/library/sys.html#sys.stdout "sys.stdout"), and instances of [`io.StringIO`](https://docs.python.org/3/library/io.html#io.StringIO "io.StringIO").

See also [binary file](https://docs.python.org/3/glossary.html#term-binary-file) for a file object able to read and write [bytes-like objects](https://docs.python.org/3/glossary.html#term-bytes-like-object).

triple-quoted string

A string which is bound by three instances of either a quotation mark (“) or an apostrophe (‘). While they don’t provide any functionality not available with single-quoted strings, they are useful for a number of reasons. They allow you to include unescaped single and double quotes within a string and they can span multiple lines without the use of the continuation character, making them especially useful when writing docstrings.

type

The type of a Python object determines what kind of object it is; every object has a type. An object’s type is accessible as its [`__class__`](https://docs.python.org/3/library/stdtypes.html#instance.__class__ "instance.__class__") attribute or can be retrieved with `type(obj)`.

type alias

A synonym for a type, created by assigning the type to an identifier.

Type aliases are useful for simplifying [type hints](https://docs.python.org/3/glossary.html#term-type-hint). For example:

def remove_gray_shades(
        colors: list[tuple[int, int, int]]) -> list[tuple[int, int, int]]:
    pass

could be made more readable like this:

Color = tuple[int, int, int]

def remove_gray_shades(colors: list[Color]) -> list[Color]:
    pass

See [`typing`](https://docs.python.org/3/library/typing.html#module-typing "typing: Support for type hints (see :pep:`484`).") and [**PEP 484**](https://www.python.org/dev/peps/pep-0484), which describe this functionality.

type hint

An [annotation](https://docs.python.org/3/glossary.html#term-annotation) that specifies the expected type for a variable, a class attribute, or a function parameter or return value.

Type hints are optional and are not enforced by Python but they are useful to static type analysis tools, and aid IDEs with code completion and refactoring.

Type hints of global variables, class attributes, and functions, but not local variables, can be accessed using [`typing.get_type_hints()`](https://docs.python.org/3/library/typing.html#typing.get_type_hints "typing.get_type_hints").

See [`typing`](https://docs.python.org/3/library/typing.html#module-typing "typing: Support for type hints (see :pep:`484`).") and [**PEP 484**](https://www.python.org/dev/peps/pep-0484), which describe this functionality.

universal newlines

A manner of interpreting text streams in which all of the following are recognized as ending a line: the Unix end-of-line convention `'\n'`, the Windows convention `'\r\n'`, and the old Macintosh convention `'\r'`. See [**PEP 278**](https://www.python.org/dev/peps/pep-0278) and [**PEP 3116**](https://www.python.org/dev/peps/pep-3116), as well as [`bytes.splitlines()`](https://docs.python.org/3/library/stdtypes.html#bytes.splitlines "bytes.splitlines") for an additional use.

variable annotation

An [annotation](https://docs.python.org/3/glossary.html#term-annotation) of a variable or a class attribute.

When annotating a variable or a class attribute, assignment is optional:

class C:
    field: 'annotation'

Variable annotations are usually used for [type hints](https://docs.python.org/3/glossary.html#term-type-hint): for example this variable is expected to take [`int`](https://docs.python.org/3/library/functions.html#int "int") values:

count: int = 0

Variable annotation syntax is explained in section [Annotated assignment statements](https://docs.python.org/3/reference/simple_stmts.html#annassign).

See [function annotation](https://docs.python.org/3/glossary.html#term-function-annotation), [**PEP 484**](https://www.python.org/dev/peps/pep-0484) and [**PEP 526**](https://www.python.org/dev/peps/pep-0526), which describe this functionality. Also see [Annotations Best Practices](https://docs.python.org/3/howto/annotations.html#annotations-howto) for best practices on working with annotations.

virtual environment

A cooperatively isolated runtime environment that allows Python users and applications to install and upgrade Python distribution packages without interfering with the behaviour of other Python applications running on the same system.

See also [`venv`](https://docs.python.org/3/library/venv.html#module-venv "venv: Creation of virtual environments.").

virtual machine

A computer defined entirely in software. Python’s virtual machine executes the [bytecode](https://docs.python.org/3/glossary.html#term-bytecode) emitted by the bytecode compiler.

Zen of Python

Listing of Python design principles and philosophies that are helpful in understanding and using the language. The listing can be found by typing “`import this`” at the interactive prompt.