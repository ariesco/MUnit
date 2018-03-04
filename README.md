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

Available commands:
-------------------
* **assertEqual(t, t')** indicates that both **t** and **t'** must be reduced to the same
normal form by means of equations.
* **assertDifferent(t, t')** indicates that the normal forms of **t** and **t'** must
be different.
* **assertTrue(t)** indicates that the normal form of **t** must be **true**.
* **assertFalse(t)** indicates that the normal form of **t** must be **false**.
* **assertReachable(t, t')** Indicates that **t'** is reachable from **t** within an
unbounded number of steps.
* **assertReachableBnd(t, t', bnd)**