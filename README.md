# p4u
p4 utility to fill up the gap of p4 itself.

It is based on bash script thus working with bunch of shell commands.
It works on top of `p4` binary as released officially but filled the gap for features and things that
could be better.

> For someone coming from `git` to use `p4`, I bet you know what was missing in the latter.

# Features

*WIP*, some implemented as below.

## `p4u describe`

Original `p4 describe` has limitation as follows

* It doesn't show (additional) diff of newly added files on the shelved changelist.
* It outputs in non-unified (non-git compatible) format, it needs a particular flags to make it output just that
* It outputs excessed header text although it's good, but sometimes we want to directly pipe it to ` ... | view -` (`vim`) to see as diff format immediatley without manual removal of such header lines.

Usages as implemented

* `p4u describe -S=123456`
* `p4u describe -S=123456 --no-header`

# License
MIT, Wasin Thonkaew
