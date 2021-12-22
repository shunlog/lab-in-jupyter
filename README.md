# Notebook

## Ignore cell output
The instructions from this [gist](https://gist.github.com/33eyes/431e3d432f73371509d176d0dfb95b6e) have to be applied in this repo to enable output stripping on git actions, and specifically:

``` bash
git config filter.strip-notebook-output.clean 'jupyter nbconvert --ClearOutputPreprocessor.enabled=True --to=notebook --stdin --stdout --log-level=ERROR'
git config filter.strip-notebook-output.smudge 'jupyter nbconvert --ClearOutputPreprocessor.enabled=True --to=notebook --stdin --stdout --log-level=ERROR'
```

Stripping the output of the executed cells makes using git with the notebooks much easier. For one, running `git status` and `git diff` only show the changes made in the source code, not in the output of the cells. Also it prevents the clutter of the repo with useless data.

## Dependencies

### nbdime (optional)

For making the output of `diff` much more intuitive (instead of a json blob)

``` python
pip install nbdime
nbdime config-git --enable --global 
```

### nbconvert

For converting all the notebooks into a single pdf (report), and also for stripping the output of the cells

``` bash
pip install nbconvert
```

## Usage

The `.ipynb` files go into the `./notebooks/` directory. Don't worry if the outputs have changed after you executed the cells again, git will ignore them. 

For the report, run `make_report` which will generate a pdf in the `./report` directory
