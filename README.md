# Lua pairs iterator unexpected behavior with __pairs metamethod

This repository demonstrates a subtle bug in Lua's `pairs` iterator when interacting with tables having a custom `__pairs` metamethod. The bug manifests when the `__pairs` metamethod modifies the table structure during iteration, causing the iterator to miss elements or produce unexpected results.

The `bug.lua` file contains code that reproduces the issue. The `bugSolution.lua` file offers a solution to avoid this behavior.

## Reproducing the Bug

1. Clone this repository.
2. Run `bug.lua`. You might observe unexpected behavior in the output.

## Understanding the Issue

Lua's `pairs` iterator relies on the internal structure of the table. Modifying the table during iteration can disrupt its internal state, leading to inconsistencies. The `__pairs` metamethod provides a way to customize this iteration, but if not handled carefully, can lead to this bug.

## Solution

The `bugSolution.lua` file demonstrates a solution that avoids modifying the table during iteration. It creates a copy of the table before iterating, ensuring that the iteration process remains unaffected by changes to the original table.