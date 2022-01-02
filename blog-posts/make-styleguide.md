---
published: false
title: 'makefile styleguide as task runner'
cover_image: ''
description: ''
tags: 'make'
series:
canonical_url: https://dev.to/hiroga/makefile-styleguide
---

Using make as task runner, this is style guide of `makefile` for me

## Style Rules

### Assignment to variables

Use `:=` as possible. The variables defined by `=` is referred recursively and it is little tricky.  
See [6\.5 Setting Variables](https://www.gnu.org/software/make/manual/make.html#Setting)

### Order or targets

Here is the preferable target order.

```md
1. all (any name you like)
2. .PHONY
3. (other tasks)
4. clean
```

`all` is optional and should contains default tasks, like `download`, `build`, `start`. If you do not allow running without specifying goal, just remove this target.

`.PHONY` target should contain all phony targets, which name is not build output. There are two reasons to use phony target. to make sure to run target if a file of the same name exists, and to skip checking a file timestamp of the same name.

see [Phony Targets \(GNU make\)](https://www.gnu.org/software/make/manual/html_node/Phony-Targets.html).

`clean` is used to be placed in the last, as I know.

## Formatting Rules

### Command substitution

Use `$$()` (double dollar) instead of `\`\`` (backquotes).  
Some articles say that backquotes has a little bit more compatibility to ancient make. However, escaping backquotes in nested command substitution is bother jobs.

#### TIPS: `$$(command)` vs `$(shell command)`

`$(shell command)` will be evaluated at the first time. `$$(command)` will be evaluated at the execution time.

### Semicolon vs new line and TAB

Use new line and TAB for command. To keep the format constant regardless of the number of lines in the command.

### Shell variables

Use `$${VAR}` instead of `$$VAR`. It help to distinguish shell variables from make variables.

## Meta Rules

### File name

Use `Makefile`, start with capital.  
The manual says [We recommend Makefile because it appears prominently near the beginning of a directory listing, right near other important files such as README\.](https://www.gnu.org/software/make/manual/make.html#Makefile-Names)

## References and Inspirations

- [GNU make](https://www.gnu.org/software/make/manual/make.html)
- [Home \| Makefile Advent Calendar 2020](https://voyagegroup.github.io/make-advent-calendar-2020/)
- [Makefile Best Practices — Cloud Posse Developer Hub](https://docs.cloudposse.com/reference/best-practices/make-best-practices/)
- [bash \- What is the difference between $\(command\) and \`command\` in shell programming? \- Stack Overflow](https://stackoverflow.com/questions/4708549/what-is-the-difference-between-command-and-command-in-shell-programming)
- [bash \- Command substitution: backticks or dollar sign / paren enclosed? \- Stack Overflow](https://stackoverflow.com/questions/9405478/command-substitution-backticks-or-dollar-sign-paren-enclosed)
- [coding style \- Should I name "makefile" or "Makefile"? \- Stack Overflow](https://stackoverflow.com/questions/12669367/should-i-name-makefile-or-makefile)
- [Style Guide の Style Guide を作る](https://zenn.dev/hiroga/articles/styleguide-of-styleguide)
