# jupyter-notebook-sample

## ryeで管理

```
rye init
rye add jupyter
rye sync
```

## jupyter notebook起動

```
rye run jupyter notebook
```

## nbstripoutの設定

### install
```
rye add nbstripout
rye sync
```

### commit hook
```
rye run nbstripout --install
```

そうすると gitのconfigに下記が設定される
```
[filter "nbstripout"]
	clean = \"/Users/springmt/jupyter_notebook_sample/.venv/bin/python\" -m nbstripout
	smudge = cat
[diff "ipynb"]
	textconv = \"/Users/springmt/jupyter_notebook_sample/.venv/bin/python\" -m nbstripout -t
```

この状態でcommitする