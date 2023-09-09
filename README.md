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
commit hookの設定は各自で実施しなければならない。
下記コマンドを実行する。

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

この状態でcommitする。

この状態でcommitすると差分はこんな感じ

https://github.com/SpringMT/jupyter_notebook_sample/compare/73778a45a5a74f5e1f9c4437c629ba7b3e449fd6...46f2614d1c563522a55be7c32c9e8ee4c784ddb8
