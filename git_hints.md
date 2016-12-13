# Creating and Applying Patch Files
[Summarized from Ariejan](https://ariejan.net/2009/10/26/how-to-create-and-apply-a-patch-with-git/)

Make all the changes in a seperate branch. Then:

```bash
# Check out the branch you made changes in
$ git checkout branch_with_patch
# Make the patch over stdout and redirect to a file. This makes one file for an entire branch
$ git format-patch --stdout branch_base > file.patch
# Check what changes this patch has
$ git apply --stat file.patch
# Check for errors when applying it
$ git checkout branch_base
$ git apply --check file.patch
# Test on clean copy of the base branch
$ git checkout -b test_apply_patch
$ git am --signoff < file.patch
# Now run your tests. If they are good, send out the patch
