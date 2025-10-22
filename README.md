MUnit: A Unit testing framework for Maude
=========================================

Getting the tool
----------------

The code of 'MUnit' is contained in a GIT repository on GitHub, whose URL is
https://github.com/ariesco/MUnit. To get a copy of the repository you only
have to write in your Linux/MacOS console:

    $ git clone https://github.com/ariesco/MUnit

This will create a MUnit folder containing the source code of the tool as well as
several examples.

Syntax and use
--------------
Unit tests are defined in modules with syntax **munit MODULE is ASSERTIONS endu**,
where **MODULE** is the name of the module that will be tested and **ASSERTIONS**
is a list of assertions following the syntax described below.

Take into account the following instructions when using the tool:
- Maude must be started with the **-allow-files** option, so external files
can be used.
- Modules under test must be loaded before the **munit.maude** file, which starts
the I/O loop.

Example
-------

We show how to test the **add_even.maude** module, available in the **examples**
folder. The tool is first started as:

```
$> maude examples/add_even.maude -allow-files munit.maude
```

The unit tests are defined in the file **add_even_test.maude**, which is loaded with
the following command:

```
MUnit> open examples/add_even_test.maude
```

This file contains 8 test cases, where 6 of them are correct and 2 of them are
prepared to fail. The tool presents the following information:

```
8 test cases were executed.

2 failures.

assertEqual (3, 4) failed.
First term reduced to 3
Second term reduced to 4

assertEqual (3, add(1, 2)) passed.

assertEqual(add(2, 1), 2 + 1) passed.

assertEqual(3, 3) passed.

assertTrue(even(7)) failed.
Term reduced to false

assertTrue(even(8)) passed.

hasSolution(1, 0, *, unbounded, true = true /\ 8 > 4 = true) passed.

hasSolution(2, 0, *, 7, true = true /\ 9 > 4 = true) passed.
```



Available commands:
-------------------
* **open path**, which loads the file stored in **path**.
* **q** or **quit**, which finish the current session.

Available assertions:
---------------------
* **assertEqual(t, t')** passes if both **t** and **t'** are reduced to the same
normal form by means of equations.
* **assertDifferent(t, t')** passes if the normal forms of **t** and **t'** are
different.
* **assertTrue(t)** passes if the normal form of **t** is **true**.
* **assertFalse(t)** passes if the normal form of **t** is **false**.
* **asertSort(t, s)** passes if the normal form of **t** has exactly sort **s**.
* **assertLeqSort(t, s)** passes if the normal form of **t** has sort **s'**, with **s' <= s**.
* **assertReachable(t, t')** passes if **t'** is reachable from **t** within an
unbounded number of steps.
* **assertReachableBnd(t, t', bnd)** passes if **t'** is reachable from **t** within
**bnd** steps.
* **hasSolution(t, pat, mode, bound, cond)}** passes when there exists at least one
reachable term that, starting from **t**, matches the pattern **pat** and fulfills the
condition **cond** in at most **bound** (either **unbounded** or a natural
number) steps. The **mode** can be either *, for 0 or more steps; +, for 1
or more steps; and !, for final states.
* **noSolution(t, pat, mode, bound, cond)** passes when no reachable solution was expected
from **t**, matching the pattern **pat** and fulfilling the
condition **cond** in at most **bound**.
