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
* **assertEqual(t, t')** passes if both **t** and **t'** are reduced to the same
normal form by means of equations.
* **assertDifferent(t, t')** passes if the normal forms of **t** and **t'** are
different.
* **assertTrue(t)** passes if the normal form of **t** is **true**.
* **assertFalse(t)** passes if the normal form of **t** is **false**.
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
* **loop(initial-state)**. This instruction starts the MUnit inner loop by rewriting
**initial-state**, which must have sort **System**.

* **command(comm)**. This instruction introduces the command **comm** into the first
element of the loop and rewrites the thus obtained term to evolve the system.