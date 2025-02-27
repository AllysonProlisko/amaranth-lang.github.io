Contributing
############

The Amaranth project is the collective work of many people collaborating over the years, and it would not be the same without everyone's unique perspectives and contributions. We're glad that you are considering joining us! This page will guide you through some of the ways to contribute to the project.


Filing problem reports
======================

We would like Amaranth to be a best-in-class design tool, and hearing about issues people encounter while using it is crucial for improving it. While we do care a lot about correctness of the results, we care about the experience of using the tool just as much. Amaranth is meant to be a tool that is comfortable to use: with fewer sharp edges (no matter how much technological appeal they might have) and more signs and guardrails.

Please `report <issues>`_ any problems you encounter using Amaranth. To go beyond that: **If, while you are using Amaranth, you see an error message that is hard to understand or is misleading, please report it as a bug. Even (especially!) if you think you did something wrong.**

.. _issues: https://github.com/amaranth-lang/amaranth

When filing problem reports, please include the following information:

* The exact version of Amaranth, which you can find by running ``python -c "import amaranth; print(amaranth.__version__)"``;
* A complete, self-contained, and minimal program that demonstrates the problem you are reporting (if minimizing it is not feasible, include the exact sequence of steps that reproduces the problem);
* What you expected to happen, and what actually happened (where possible, including a verbatim copy of the log file or the terminal output);
* For usability issues: your reason for filing the report (i.e. why did you expect a different behavior).

There is no expectation that a person who is filing a problem report should work on fixing it. Submitting an issue is a valuable contribution in its own right.


Fixing problems
===============

We appreciate that many in the open source community tend to see problems they encounter as opportunities to collaborate, and we enjoy seeing an issue being filed together with a pull request. However, unless you've contributed a few times before or the fix is truly trivial, **please discuss it with one of the maintainers first**. It doesn't take much time and it can sometimes save everyone a lot of unnecessary work and frustration.


Proposing new features
======================

Amaranth is a programming language and a toolchain, which is different from many other kinds of open source projects in that just about every part of it is, unavoidably, tightly coupled to every other one, the result being that seemingly obvious and apparently minor decisions can have dramatic consequences years later.

To make sure that new features undergo the scrutiny necessary for commitment to many years of support, and to make sure that everyone in the community who will be impacted by the changes has a chance to make their voice heard, **all substantial changes, including feature proposals, must go through a formal Request for Comments process**. The process, as well as the accepted proposals, are described `here <rfcs>`_. Typically, substantial changes are accepted after one to several rounds of community review achieve near-unanimous consensus.

.. _rfcs: https://amaranth-lang.org/rfcs/


Working with the codebase
=========================


Preparing the environment
-------------------------

The Amaranth codebase uses the PDM_ package and dependency manager to structure the development workflow. Please `install PDM`_ first and make sure you have downloaded the latest changes to the source files. Once you have done so, run:

.. _PDM: https://pdm.fming.dev/
.. _install PDM: https://pdm.fming.dev/latest/#recommended-installation-method

.. code-block:: console

   $ pdm install --dev

This command creates a :ref:`virtual environment <python:tut-venv>` located at ``./.venv/`` and installs the runtime dependencies of Amaranth as well as the necessary development tools in it.

Amaranth itself is installed in the *editable mode*, meaning that the changes to its source files are immediately reflected in running the tests and documentation. However, other changes (addition or removal of source files, or changes to dependencies) will not be picked up, and it is a good habit to run ``pdm install`` each time after updating the source tree.


Running the testsuite
---------------------

Some of the tests make use of `formal methods`_, and to run the complete testsuite, it is necessary to install the Yosys_ frontend and the yices2_ SMT solver. These are distributed as a part of the `OSS CAD Suite`_. Without the tools being installed, the tests that rely on formal verification will be skipped.

.. _formal methods: https://symbiyosys.readthedocs.io/en/latest/
.. _Yosys: https://github.com/YosysHQ/yosys
.. _yices2: https://github.com/SRI-CSL/yices2
.. _OSS CAD Suite: https://github.com/YosysHQ/oss-cad-suite-build

To run the testsuite, use:

.. code-block:: console

   $ pdm run test


Building the documentation
--------------------------

To build the documentation once, use:

.. code-block:: console

   $ pdm run document

The documentation index is located at ``./docs/_build/index.html``.

Working on documentation usually involves making many small, iterative changes, and it is laborous to rebuild it manually each time. To start a process that rebuilds documentation automatically on change, use:

.. code-block:: console

   $ pdm run document-live

While it is running you can browse the documentation at `https://127.0.0.1:8000 <https://127.0.0.1:8000>`_. The edits you make are reflected on the document open in the browser after a short delay. It is useful to keep an eye on the terminal where this process is running, as the information about syntactic errors, missing references, and other issues will be printed there.

Occasionally, the documentation builder will persist in rendering an incorrect or outdated version of the contents of a Python source file. To fix this, run:

.. code-block:: console

   $ pdm run document-live -a


Contributing your changes
=========================

.. todo::

   This section is unfinished

At the moment there is no formal style guide for source code. We ask that you do your best effort to keep the code that you add or modify similar in style as well as in spirit to the code surrounding it, and we may ask you to change it during review. When in doubt, submit your code as-is.


Weekly meetings
===============

Every Monday at 17:00 UTC on our IRC channel `#amaranth-lang at libera.chat <irc>`_ or Matrix channel `#amaranth-lang@matrix.org <matrix>`_ (the channels are bridged together: the same messages appear on both), Amaranth maintainers meet with users and contributors to discuss newly submitted Requests for Comments and any other issues that warrant broad attention. These public meetings are the primary avenue of decision making.

.. _irc: https://web.libera.chat/#amaranth-lang
.. _matrix: https://matrix.to/#/#amaranth-lang:matrix.org

If you want to contribute, have interest in language evolution, or simply want to voice your view on proposed features, feel free to join these meetings; there is no formal attendance. If you are not able to make the time, the meetings are publicly recorded and the summaries are posted in the relevant GitHub thread after the meeting.
