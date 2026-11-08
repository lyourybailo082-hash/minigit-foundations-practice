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
## Exercise 2 — Lost newlines

The bug happens because std::getline() removes each newline.
Joining the lines produces "ab" instead of "a\nb\n".

The fix reads the whole file without removing newlines:

cpp
std::string readAll(const std::filesystem::path& file) {
    std::ifstream input(file, std::ios::binary);
    std::ostringstream contents;
    contents << input.rdbuf();
    return contents.str();
}


This version requires #include <sstream>.

## Exercise 3 — Two path mistakes

The first mistake is joining strings instead of filesystem paths.
Use root / ".minigit" for portable path joining.

The second mistake is the leading slash in "/HEAD".
Use "HEAD" so it stays inside the metadata directory.

Corrected code:

cpp
std::filesystem::path metadataDirectory(
    const std::filesystem::path& root) {
    return root / ".minigit";
}

std::filesystem::path headFile(
    const std::filesystem::path& root) {
    return metadataDirectory(root) / "HEAD";
}