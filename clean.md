## git clean

Команда **git clean** используется для удаления мусора из рабочей директории. Это могут быть результаты сборки проекта или файлы конфликтов слияний.

*DESCRIPTION*
```hash = 
git clean [-d] [-f] [-i] [-n] [-q] [-e <pattern>] [-x | -X] [--] <path>…​

-d
Normally, when no <path> is specified, git clean will not recurse into untracked directories to avoid removing too much. Specify -d to have it recurse into such directories as well. If any paths are specified, -d is irrelevant; all untracked files matching the specified paths (with exceptions for nested git directories mentioned under --force) will be removed.

-f
--force
If the Git configuration variable clean.requireForce is not set to false, git clean will refuse to delete files or directories unless given -f or -i. Git will refuse to modify untracked nested git repositories (directories with a .git subdirectory) unless a second -f is given.

-i
--interactive
Show what would be done and clean files interactively. See “Interactive mode” for details.

-n
--dry-run
Don’t actually remove anything, just show what would be done.

-q
--quiet
Be quiet, only report errors, but not the files that are successfully removed.

-e <pattern>
--exclude=<pattern>
Use the given exclude pattern in addition to the standard ignore rules (see gitignore[5]).

-x
Don’t use the standard ignore rules (see gitignore[5]), but still use the ignore rules given with -e options from the command line. This allows removing all untracked files, including build products. This can be used (possibly in conjunction with git restore or git reset) to create a pristine working directory to test a clean build.

-X
Remove only files ignored by Git. This may be useful to rebuild everything from scratch, but keep manually created files.
```