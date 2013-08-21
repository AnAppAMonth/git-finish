git-finish
==========

Finish a branch by archving it, coalescing and merging it, and finally deleting
it.


Install
=======

Place the `git-finish` file anywhere in PATH, and make sure it has the `execute`
permission.

This command relies on [git-coalesce](https://github.com/halfninety/git-coalesce).


Usage
=====

```
usage: git finish [options] <branch> [<base>]

    Before using this command, <branch> must first be rebased onto <base>.

    This command finishes a branch by carrying out the following tasks:

    1. Backup <branch> to `refs/archive/<branch>`.
    2. Coalesce the commits between <base> and <branch> by calling
       git-coalesce.
    3. Merge <branch> to <base>. By default fast-forwarding is used.
       If --no-ff is specified, the flag --no-commit is also used
       when doing the merge. You will have to commit manually.
    4. If fast-forwarding is used in step 3, also delete <branch>.
       Otherwise, step 3 will stop before committing, and you need
       to manually commit the merge and delete <branch>.

positional arguments:
  <branch>       the branch to finish
  [<base>]       the upstream branch to merge to. Defaults to `master` if
                 omitted

optional arguments:
  -h, --help     show this help message and exit
  --no-ff        forbid fast-forwarding when merging
  -v, --version  show program's version number and exit
```


License
=======

MIT
