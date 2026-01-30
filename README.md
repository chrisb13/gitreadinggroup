# gitreadinggroup

## Motivation

We had some super messy history to clean up!

 - https://github.com/ACCESS-NRI/access-om3-configs/issues/1035
 - https://github.com/ACCESS-NRI/access-om3-configs/issues/880
 - https://github.com/ACCESS-NRI/access-om3-configs/pull/1078
 - https://github.com/ACCESS-NRI/access-om3-configs/pull/1077

## .. and ... introduction
This is a lesson by way of a sandbox repository. The following is inspired by Julia Evans' great website
 - https://jvns.ca/blog/2023/11/01/confusing-git-terminology/#and

Here are two commands:
```bash
git diff main..test
git diff main...test
```
What’s the difference between `..` and `...`? Note that without any dots git defaults to `..` and github Pull requests use `...`. 

Imagine we have the following
```markdown
A - B main
  \
    C - D test
```

Imagine the situation where commits `B`,`C`,`D` have _additions_ in them (no text is removed). Then:

 - `main..test` is removal of B, commits C and D
 - `test..main` is commit B, removal of C, D
 - `main...test` is commits B, C, and D

The situation is more complicated when we start removing text as well, let's look at an exmaple.

## Playing with the above example
We have a file at commit [A](https://github.com/chrisb13/double-triple-dot-git/commit/fd3c4fb8b020f192946de9c309422549ff554a39) that looks like:
```markdown
# double-triple-dot-git

This line will be used for commit B: I am adding some text for commit B

This line will be used for commit C: I am adding some text for commit C

This line will be used for commit D: I am adding some text for commit D
```

We will have 6 additional commits. Across the following branches:
```
A - B        main
  \
   C - D     test
```

```
A - B'        main_minus
  \
   C' - D'     test_minus
```

A commit with just a letter adds to the related line whereas a commit with a prime (`'`)  will remove the text on the related line. See the commits here (these show you the difference to the parent, so do look at the diagram above):
 - [B](https://github.com/chrisb13/double-triple-dot-git/commit/29adf5137fcfed8d9becb645f973a8f9c93764f1);
 - [C](https://github.com/chrisb13/double-triple-dot-git/commit/232caf4634fbf9aecc780b54abe5d2e8894d6d7d);
 - [D](https://github.com/chrisb13/double-triple-dot-git/commit/c41c8efb6e5133bf24f9afece6b9a235f20963c6);
 - [B'](https://github.com/chrisb13/double-triple-dot-git/commit/dd9c11e01f9a8d73589f566c04656d56ed0bc631);
 - [C'](https://github.com/chrisb13/double-triple-dot-git/commit/dd9c11e01f9a8d73589f566c04656d56ed0bc631);
 - [D'](https://github.com/chrisb13/double-triple-dot-git/commit/d3a03776f6d2288dd9f910eb7e163437f81276a7).

Here is our full repo history:
```markdown
* d3a0377   D' (origin/test_minus)
|
* 5dd0906   C'
|
| * c41c8ef D  (origin/test)
| |
| * 232caf4 C
|/
| * dd9c11e B' (origin/main_minus)
|/
| * 29adf51 B  (origin/main)
|/
* fd3c4fb   A
|
* bf39729   Initial commit - Christopher Bull
```

Suggested links:
 1. [main..test](https://github.com/chrisb13/double-triple-dot-git/compare/main..test);
 1. [main...test](https://github.com/chrisb13/double-triple-dot-git/compare/main...test);
 1. [main_minus..test_minus](https://github.com/chrisb13/double-triple-dot-git/compare/main_minus..test_minus);
 1. [main_minus...test_minus](https://github.com/chrisb13/double-triple-dot-git/compare/main_minus...test_minus).

Notes 
 - in the 4th example above there's a possible gotcha on an actual merge! (All lines will be deleted).

Feel free to add to the explanations above and fork [the repo'](https://github.com/chrisb13/double-triple-dot-git).

## Further reading
### DolphinDream's picture

Source: https://stackoverflow.com/a/46345364 or https://i.sstatic.net/4wMJI.png
![Alt text](https://i.sstatic.net/4wMJI.png)

### Matthew Brett's ideas
 - https://matthew-brett.github.io/pydagogue/pain_in_dots.html
 - https://matthew-brett.github.io/pydagogue/git_diff_dots.html#git-diff-dots

### Stackoverflow

On `git diff`
 - https://stackoverflow.com/questions/7251477/what-are-the-differences-between-double-dot-and-triple-dot-in-git-dif

On `git log`
 - https://stackoverflow.com/questions/462974/what-are-the-differences-between-double-dot-and-triple-dot-in-git-com

### Github
 - https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-comparing-branches-in-pull-requests#three-dot-and-two-dot-git-diff-comparisons
