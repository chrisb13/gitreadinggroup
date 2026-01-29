# gitreadinggroup

## Motivation

We had some super messy history to clean up!

 - https://github.com/ACCESS-NRI/access-om3-configs/issues/1035
 - https://github.com/ACCESS-NRI/access-om3-configs/issues/880
 - https://github.com/ACCESS-NRI/access-om3-configs/pull/1078
 - https://github.com/ACCESS-NRI/access-om3-configs/pull/1077

## .. and ...
The following is from Julia Evans' great website
 - https://jvns.ca/blog/2023/11/01/confusing-git-terminology/#and

Here are two commands:

git log main..test
git log main...test
What’s the difference between .. and ...? I never use these so I had to look it up in man git-range-diff. It seems like the answer is that in this case:

A - B main
  \
    C - D test

main..test is commits C and D
test..main is commit B
main...test is commits B, C, and D
But it gets worse: apparently git diff also supports .. and ..., but they do something completely different than they do with git log? I think the summary is:

git log test..main shows changes on main that aren’t on test, whereas git log test...main shows changes on both sides.
git diff test..main shows test changes and main changes (it diffs B and D) whereas git diff test...main diffs A and D (it only shows you the diff on one side).


## DolphinDream's picture

Source: https://stackoverflow.com/a/46345364 or https://i.sstatic.net/4wMJI.png
![Alt text](https://i.sstatic.net/4wMJI.png)

## Matthew Brett's ideas
 - https://matthew-brett.github.io/pydagogue/pain_in_dots.html
 - https://matthew-brett.github.io/pydagogue/git_diff_dots.html#git-diff-dots

## Stackoverflow

On `git diff`
 - https://stackoverflow.com/questions/7251477/what-are-the-differences-between-double-dot-and-triple-dot-in-git-dif

On `git log`
 - https://stackoverflow.com/questions/462974/what-are-the-differences-between-double-dot-and-triple-dot-in-git-com

## Github
 - https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-comparing-branches-in-pull-requests#three-dot-and-two-dot-git-diff-comparisons
