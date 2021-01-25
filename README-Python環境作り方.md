# Python環境の作り方

## ソースファイルからのビルド

- ソースファイルの取得

	https://www.python.org/downloads/source/

- 圧縮ファイルを展開してビルド(Python-3.7.9.tgzの場合)

	7zipなどで展開後のフォルダがPython-3.7.9
	```
	cd Python-3.7.9\PCBuild
	build.bat -p x64
	```
	
- 環境変数設定バッチファイルの作成

	```bat:setenv.bat
	SET TMPDIR=%~dp0
	SET PYTHON_HOME=%TMPDIR:~0,-1%

	SET PYTHON_PATH=%PYTHON_HOME%\PCbuild\amd64
	SET PYTHON_BIN_PATH=%PYTHON_PATH%
	SET PYTHON_LIB_PATH=%PYTHON_PATH%
	SET PATH=%PYTHON_PATH%;%PYTHON_PATH%\Scripts;%PYTHON_HOME%\Scripts;%PATH%
	```

- アクティベートバッチファイル作成

	```bat:activate.bat
	@echo off
	set PWD=%CD%

	cd /D %~dp0
	call setenv.bat

	cd /D %PWD%
	cmd
	```

- pyconfig.hのコピー

	```copy Python-3.7.9\PC\pyconfig.h Python-3.7.9\include```

- pipのインストール

	https://bootstrap.pypa.io/get-pip.py から取得

	```python get-pip.py```


## モジュールをインストール

- 必要なものをインストール

	```python -m pip install numpy```

