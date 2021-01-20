# Python環境構築（バックエンド編)
## Python 3.9.1 install

以下サイトに行って、3.9.1をダウンロード
https://www.python.org/downloads/  
ウィザードにてインストール

- Pathは通しておく（Path～にチェックを入れる）

インストールされたか確認

    C:\Users\hisano>python --version
    Python 3.9.1

## 仮想環境の構築

フォルダを作成し、仮想環境（Virtual environment）を作成

    mkdir reservesys
    cd reservesys
    python -m venv myvenv

仮想環境の起動

    myvenv\Scripts\activate

Scripts実行エラーが出た場合

    powershell -ExecutionPolicy Bypass myvenv\Scripts\activate 

*scriptの実行ポリシー*
| 実行ポリシー | 署名あり | 署名なし/ローカル | 署名なし/非ローカル | 説明 |
| :-- | :-: | :-: | :-: | :-- |
| Restricted | × | × | × | すべてのスクリプトの実行を制限
| AllSigned | 〇 | × | × | 署名のあるスクリプトのみ実行可能
| RemoteSigned | 〇 | 〇 | × | ローカル上のスクリプトと非ローカル上の署名のあるスクリプトのみ実行可能
| Unrestricted | 〇 | 〇 | △ | すべてのスクリプトが実行可能だが非ローカル上のスクリプトは実行時に許可が必要
| Bypass | 〇 | 〇 | 〇| すべてのスクリプトが実行可能


## Djangoのインストール

- pipのインストール

    cd myvenv
    python -m pip instgall --upgrade pip

- reqirementsファイルによってパッケージをインストールする

    cd ../
    new-item requirements.txt

- requrements.txtに以下のテキストを追加

    Django~=2.2.4

- myvenvでインストール実行

    cd myvenv
    pip install -r c:\reservesys\requirements.txt

## Gitのインストール
*インストールしていない場合のみ実施*  

以下サイトに行って Download → install と進むと自動でダウンロードされる  
https://git-scm.com/  

- インストーラーを実行  
- エディタは[nano]を選択  
- Path環境の調整では[Use Git aand optional Unix - tools from the windows Command Prompt]を選択  
- それ以外はデフォルト

## プロジェクトの作成

    cd reservesys
    django-admin.exe startproject mysite .

プロジェクトを作成すると、以下のフォルダ構成になる

    reservesys
    ├── manage.py
    ├── mysite
    │   ├── __init__.py
    │   ├── settings.py
    │   ├── urls.py
    │   └── wsgi.py
    ├── myvenv
    │   └── ...
    └── requirements.txt

- manage.py サイトの管理に役立つスクリプト  
- settings.py ウェブサイトの設定  
- urls.py urlresolverで使用されるパターンリスト

- setting.pyの変更 

設定値を以下に変更  

    TIME_ZONE = 'Asia/Tokyo'
    LANGUAGE_CODE = 'ja' 
    ALLOWED_HOSTS = ['localhost', '127.0.0.1', '[::1]'] ← 初期値を明示的にしただけ

最下行に設定値を追加（STATIC_URLの下）  

    STATIC_ROOT = os.path.join(BASE_DIR, 'static')

## データベースのセットアップ

Sqlite3を使用する。

    cd reservesys
    python manage.py migrate

## ウェブサーバーを起動してみる

    python manage.py runserver


エラーの場合は以下のコマンドにしてみる  

    python manage.py runserver

以下のサイトにアクセスしてみる  
http://127.0.0.1:8000/  

ロケットの画面が出たらOK  

