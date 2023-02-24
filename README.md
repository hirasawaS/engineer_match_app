# プロジェクト説明(Engineer_match_app)

## 前提(conda環境を作る)
  - pipでいれたやつと,condaで入れたやつ
    ~~~ bash
      $ conda env create -n "$your_enviroment" -f origin_application_venv.yml
      $ pip install -r requirements.txt
    ~~~
  - venv環境dir直下に本リポジトリをクローン


## 1. 環境変数

- クレデンシャル等で必要になったものは.envに記載したうえでモジュール上で以下を実行してください

    ~~~ python
    env = environ.Env()
    env.read_env(".env")
    変数=env("$key")
    ~~~

    - 初期でDBとdjangoのクレデンシャルが格納されています。これによってセキュアな開発を行いましょう。


## 2. DBで行う設定

- その前にバージョン確認
  - postgres : 13.8
  - python : 3.8.16
  - Django==4.1.7
  - django-environ==0.9.0
  - psycopg2-binary==2.9.5
  - sqlparse==0.4.3
  - tzdata==2022.7
  - wincertstore==0.2

- 注意
  - 先にpostgresでDBを作成したのちに.envを作成し、保存しておくこと
  - 左のdebugボタンからpython-djangoというランタイム環境で起動ボタン押したらビルド/デプロイします。

## 3. 便利なコマンド集
1. アプリケーションを作成する
   1. 多重責務にならんように割と詳細にアプリケーションをわけるっぽい

         ~~~ bash
         $ python manage.py startapp $AppName
   　    ~~~
## 4. Djangoの基礎概念

 - 結構めんどいので後で追記
