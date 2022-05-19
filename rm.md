## git rm

Команда **git rm** используется в Git для удаления файлов из индекса и рабочей директории. Она похожа на [**git add**](./add.md) с тем лишь исключением, что она удаляет, а не добавляет файлы для следующего коммита.

*DESCRIPTION*
```hash = 
git rm [-f] [-n] [-r] [--cached] [--ignore-unmatch]
	  [--quiet] [--pathspec-from-file=<file> [--pathspec-file-nul]]
	  [--] [<pathspec>…​]

-f
--force
Override the up-to-date check.

-n
Don’t actually remove any file(s). Instead, just show if they exist in the index and would otherwise be removed by the command.

-r
Allow recursive removal when a leading directory name is given.

--
This option can be used to separate command-line options from the list of files, (useful when filenames might be mistaken for command-line options).

--cached
Use this option to unstage and remove paths only from the index. Working tree files, whether modified or not, will be left alone.

--ignore-unmatch
Exit with a zero status even if no files matched.

--sparse
Allow updating index entries outside of the sparse-checkout cone. Normally, git rm refuses to update index entries whose paths do not fit within the sparse-checkout cone. See git-sparse-checkout[1] for more.

-q
--quiet
git rm normally outputs one line (in the form of an rm command) for each file removed. This option suppresses that output.

--pathspec-from-file=<file>
Pathspec is passed in <file> instead of commandline args. If <file> is exactly - then standard input is used. Pathspec elements are separated by LF or CR/LF. Pathspec elements can be quoted as explained for the configuration variable core.quotePath (see git-config[1]). See also --pathspec-file-nul and global --literal-pathspecs.

--pathspec-file-nul
Only meaningful with --pathspec-from-file. Pathspec elements are separated with NUL character and all other characters are taken literally (including newlines and quotes).
```