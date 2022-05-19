## git commit

Команда **git commit** берёт все данные, добавленные в индекс с помощью **git add**, и сохраняет их слепок во внутренней базе данных, а затем сдвигает указатель текущей ветки на этот слепок.

*DESCRIPTION*
```hash = 
git commit [-a | --interactive | --patch] [-s] [-v] [-u<mode>] [--amend]
	   [--dry-run] [(-c | -C | --squash) <commit> | --fixup [(amend|reword):]<commit>)]
	   [-F <file> | -m <msg>] [--reset-author] [--allow-empty]
	   [--allow-empty-message] [--no-verify] [-e] [--author=<author>]
	   [--date=<date>] [--cleanup=<mode>] [--[no-]status]
	   [-i | -o] [--pathspec-from-file=<file> [--pathspec-file-nul]]
	   [(--trailer <token>[(=|:)<value>])…​] [-S[<keyid>]]
	   [--] [<pathspec>…​]


-a
--all
Tell the command to automatically stage files that have been modified and deleted, but new files you have not told Git about are not affected.

-p
--patch
Use the interactive patch selection interface to choose which changes to commit. See git-add[1] for details.

-C <commit>
--reuse-message=<commit>
Take an existing commit object, and reuse the log message and the authorship information (including the timestamp) when creating the commit.

-c <commit>
--reedit-message=<commit>
Like -C, but with -c the editor is invoked, so that the user can further edit the commit message.

--fixup=[(amend|reword):]<commit>

--squash=<commit>
Construct a commit message for use with rebase --autosquash. The commit message subject line is taken from the specified commit with a prefix of "squash! ". Can be used with additional commit message options (-m/-c/-C/-F). See git-rebase[1] for details.

--reset-author
When used with -C/-c/--amend options, or when committing after a conflicting cherry-pick, declare that the authorship of the resulting commit now belongs to the committer. This also renews the author timestamp.

--short
When doing a dry-run, give the output in the short-format. See git-status[1] for details. Implies --dry-run.

--branch
Show the branch and tracking info even in short-format.

--porcelain
When doing a dry-run, give the output in a porcelain-ready format. See git-status[1] for details. Implies --dry-run.

--long
When doing a dry-run, give the output in the long-format. Implies --dry-run.

-z
--null
When showing short or porcelain status output, print the filename verbatim and terminate the entries with NUL, instead of LF. If no format is given, implies the --porcelain output format. Without the -z option, filenames with "unusual" characters are quoted as explained for the configuration variable core.quotePath (see git-config[1]).

-F <file>
--file=<file>
Take the commit message from the given file. Use - to read the message from the standard input.

--author=<author>
Override the commit author. Specify an explicit author using the standard A U Thor <author@example.com> format. Otherwise <author> is assumed to be a pattern and is used to search for an existing commit by that author (i.e. rev-list --all -i --author=<author>); the commit author is then copied from the first such commit found.

--date=<date>
Override the author date used in the commit.

-m <msg>
--message=<msg>
Use the given <msg> as the commit message. If multiple -m options are given, their values are concatenated as separate paragraphs.

The -m option is mutually exclusive with -c, -C, and -F.

-t <file>
--template=<file>
When editing the commit message, start the editor with the contents in the given file. The commit.template configuration variable is often used to give this option implicitly to the command. This mechanism can be used by projects that want to guide participants with some hints on what to write in the message in what order. If the user exits the editor without editing the message, the commit is aborted. This has no effect when a message is given by other means, e.g. with the -m or -F options.

-s
--signoff
--no-signoff
Add a Signed-off-by trailer by the committer at the end of the commit log message. The meaning of a signoff depends on the project to which you’re committing. For example, it may certify that the committer has the rights to submit the work under the project’s license or agrees to some contributor representation, such as a Developer Certificate of Origin. (See http://developercertificate.org for the one used by the Linux kernel and Git projects.) Consult the documentation or leadership of the project to which you’re contributing to understand how the signoffs are used in that project.

The --no-signoff option can be used to countermand an earlier --signoff option on the command line.

--trailer <token>[(=|:)<value>]
Specify a (<token>, <value>) pair that should be applied as a trailer. (e.g. git commit --trailer "Signed-off-by:C O Mitter \ <committer@example.com>" --trailer "Helped-by:C O Mitter \ <committer@example.com>" will add the "Signed-off-by" trailer and the "Helped-by" trailer to the commit message.) The trailer.* configuration variables (git-interpret-trailers[1]) can be used to define if a duplicated trailer is omitted, where in the run of trailers each trailer would appear, and other details.

-n
--[no-]verify
By default, the pre-commit and commit-msg hooks are run. When any of --no-verify or -n is given, these are bypassed. See also githooks[5].

--allow-empty
Usually recording a commit that has the exact same tree as its sole parent commit is a mistake, and the command prevents you from making such a commit. This option bypasses the safety, and is primarily for use by foreign SCM interface scripts.

--allow-empty-message
Like --allow-empty this command is primarily for use by foreign SCM interface scripts. It allows you to create a commit with an empty commit message without using plumbing commands like git-commit-tree[1].

--cleanup=<mode>
This option determines how the supplied commit message should be cleaned up before committing. The <mode> can be strip, whitespace, verbatim, scissors or default.

strip
Strip leading and trailing empty lines, trailing whitespace, commentary and collapse consecutive empty lines.

whitespace
Same as strip except #commentary is not removed.

verbatim
Do not change the message at all.

scissors
Same as whitespace except that everything from (and including) the line found below is truncated, if the message is to be edited. "#" can be customized with core.commentChar.

# ------------------------ >8 ------------------------
default
Same as strip if the message is to be edited. Otherwise whitespace.

The default can be changed by the commit.cleanup configuration variable (see git-config[1]).

-e
--edit
The message taken from file with -F, command line with -m, and from commit object with -C are usually used as the commit log message unmodified. This option lets you further edit the message taken from these sources.

--no-edit
Use the selected commit message without launching an editor. For example, git commit --amend --no-edit amends a commit without changing its commit message.

--amend
Replace the tip of the current branch by creating a new commit. The recorded tree is prepared as usual (including the effect of the -i and -o options and explicit pathspec), and the message from the original commit is used as the starting point, instead of an empty message, when no other message is specified from the command line via options such as -m, -F, -c, etc. The new commit has the same parents and author as the current one (the --reset-author option can countermand this).

It is a rough equivalent for:

	$ git reset --soft HEAD^
	$ ... do something else to come up with the right tree ...
	$ git commit -c ORIG_HEAD
but can be used to amend a merge commit.

You should understand the implications of rewriting history if you amend a commit that has already been published. (See the "RECOVERING FROM UPSTREAM REBASE" section in git-rebase[1].)

--no-post-rewrite
Bypass the post-rewrite hook.

-i
--include
Before making a commit out of staged contents so far, stage the contents of paths given on the command line as well. This is usually not what you want unless you are concluding a conflicted merge.

-o
--only
Make a commit by taking the updated working tree contents of the paths specified on the command line, disregarding any contents that have been staged for other paths. This is the default mode of operation of git commit if any paths are given on the command line, in which case this option can be omitted. If this option is specified together with --amend, then no paths need to be specified, which can be used to amend the last commit without committing changes that have already been staged. If used together with --allow-empty paths are also not required, and an empty commit will be created.

--pathspec-from-file=<file>
Pathspec is passed in <file> instead of commandline args. If <file> is exactly - then standard input is used. Pathspec elements are separated by LF or CR/LF. Pathspec elements can be quoted as explained for the configuration variable core.quotePath (see git-config[1]). See also --pathspec-file-nul and global --literal-pathspecs.

--pathspec-file-nul
Only meaningful with --pathspec-from-file. Pathspec elements are separated with NUL character and all other characters are taken literally (including newlines and quotes).

-u[<mode>]
--untracked-files[=<mode>]
Show untracked files.

The mode parameter is optional (defaults to all), and is used to specify the handling of untracked files; when -u is not used, the default is normal, i.e. show untracked files and directories.

The possible options are:

no - Show no untracked files

normal - Shows untracked files and directories

all - Also shows individual files in untracked directories.

The default can be changed using the status.showUntrackedFiles configuration variable documented in git-config[1].

-v
--verbose
Show unified diff between the HEAD commit and what would be committed at the bottom of the commit message template to help the user describe the commit by reminding what changes the commit has. Note that this diff output doesn’t have its lines prefixed with #. This diff will not be a part of the commit message. See the commit.verbose configuration variable in git-config[1].

If specified twice, show in addition the unified diff between what would be committed and the worktree files, i.e. the unstaged changes to tracked files.

-q
--quiet
Suppress commit summary message.

--dry-run
Do not create a commit, but show a list of paths that are to be committed, paths with local changes that will be left uncommitted and paths that are untracked.

--status
Include the output of git-status[1] in the commit message template when using an editor to prepare the commit message. Defaults to on, but can be used to override configuration variable commit.status.

--no-status
Do not include the output of git-status[1] in the commit message template when using an editor to prepare the default commit message.

-S[<keyid>]
--gpg-sign[=<keyid>]
--no-gpg-sign
GPG-sign commits. The keyid argument is optional and defaults to the committer identity; if specified, it must be stuck to the option without a space. --no-gpg-sign is useful to countermand both commit.gpgSign configuration variable, and earlier --gpg-sign.

--
Do not interpret any more arguments as options.

<pathspec>…​
When pathspec is given on the command line, commit the contents of the files that match the pathspec without recording the changes already added to the index. The contents of these files are also staged for the next commit on top of what have been staged before.

```