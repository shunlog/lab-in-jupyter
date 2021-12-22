# Notebook

## Dependencies

### nbdime

For `diff`ing only the source code in the cells while ignoring the outputs and details (e.g. execution_count)

#### Installation

``` python
pip install nbdime
nbdime config-git --enable --global 
```

Edit git config so that the output and details are ignored:

``` bash
git config -e --global
```

Change
``` git-config
[diff "jupyternotebook"]
	command = git-nbdiffdriver diff
```
To

``` git-config
[diff "jupyternotebook"]
	command = git-nbdiffdriver diff --ignore-outputs --ignore-details
```

### nbconvert

Needed for converting all the notebooks into a single pdf (report)

``` bash
pip install nbconvert
```

