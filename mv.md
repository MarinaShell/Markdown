## git mv

Команда **git mv** — это удобный способ переместить файл, а затем выполнить **git add** для нового файла и **git rm** для старого.

*DESCRIPTION*
```hash = 
git mv [-v] [-f] [-n] [-k] <source> <destination>
git mv [-v] [-f] [-n] [-k] <source> ... <destination directory>
-f
Force renaming or moving of a file even if the target exists

-k
Skip move or rename actions which would lead to an error condition. An error happens when a source is neither existing nor controlled by Git, or when it would overwrite an existing file unless -f is given.

-n
Do nothing; only show what would happen

-v
Report the names of files as they are moved.
```