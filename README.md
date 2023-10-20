# lazygit-submodule-symlink-test
Test to minimally reproduce a bug that I might have found in lazygit

## To reproduce

1. Clone this repo and enter it
2. `git submodule update --init --recursive`
3. To confirm that the _true_ path of the submodule works fine with lazygit, enter `submodules/lsst-submodule` and open `lazygit`.
4. Then, go back to the root and `cd` into `symlink-to-lsst-submodule`. If you type `pwd` you get `/path/to/lazygit-submodule-symlink-test/symlink-to-lsst-submodule`, but if you type `pwd -P`, you get its "true" location on disk, `/path/to/lazygit-submodule-symlink-test/submodules/lsst-submodule`.
   - _(Side note: I totally didn't plan it, but `lazygit-submodule-symlink-test/symlink-to-lsst-submodule` and `lazygit-submodule-symlink-test/submodules/lsst-submodule` are the exact same length. Coincidences like that are fun._
5. Inside the symlink dir, attempt to open `lazygit`. Lazygit errors: `*errors.errorString repository does not exist`. But if you just use `git`, e.g. `git status` or `git log`, it works fine.
