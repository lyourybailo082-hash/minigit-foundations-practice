# Exercise 1

## My predictions
a: It creates a folder
b: /Head
c: Notes.txt
d: The parent folder
e: 1
f: Notes.txt

## Actual results
a: repo/.minigit/HEAD
b: /HEAD
c: notes.txt
d: docs
e: 1
f: .txt

## What I learned
Joining paths does not create folders.
Capitalization stays exactly as written.
parent_path() returns the parent path.
extension() returns only the extension, including the dot.