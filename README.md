 プロジェクト説明(Engineer_match_app)

## 1. 環境構築方法
- バージョン(各々新規にツール入れるときはメンバに共有すること)
  - postgres : 13.8
  - python : 3.8.16
  - Django==4.1.7
  - django-environ==0.9.0
  - psycopg2-binary==2.9.5
  - sqlparse==0.4.3
  - tzdata==2022.7
  - wincertstore==0.2
- やっといてほしいこと
  - このリポジトリをクローンしてください

### 1.1 データベースおよび環境変数の設定

- postgreSQLを使用します。DB接続ツール(javaでいうJDBCドライバ)はpycopg2を使用します。本来であればAWSとかでDBを立ててやるのがいいですが、金がかかるのでそれは本番運用に置いておいてまったく同じ環境をlocalhostに作成してソースコードをgithubで管理します。
- クレデンシャルの管理について
  - .envというファイルをenginneer_match_app直下に作成して環境変数を記載します。(プログラムから読み取るときは以下の手順)

     ~~~ python
      env = environ.Env()
      env.read_env(".env")
      変数=env("$key")
      ~~~
    - .envの作り方
    ``` yaml
      secret_key="私に聞いてください"
      db_user="$your_user_name"
      db_password="$your_password_name"
    ```
## 1.2 anacondaの仮想環境
- 環境構築について説明します。当リポジトリのvenv_create配下にある以下のファイルを使用します。
  - origin_application_venv.yml
  - requirements.txt
1. conda仮想環境を作成します。同一環境が作られるので環境名は何でもいいですがvenv_matchapp とかでいいでしょう。
    - 【注意】
      - 作成したいディレクトリの上で行うこと
      - cmdでやると不都合が起こることがあるらしいのでAnaconda Promptで以下のコマンドを実行
      - いったんこのディレクトリから上記二つのファイルを置き、そのファイルが存在する場所でコマンドを打つこと
        ```bash
        $ conda env create -n "$your_enviroment_name" -f origin_application_venv.yml
        $ pip install -r requirements.txt
        ```
      - 正常に環境が作られたか確認(下にさっき作った環境が出てくる)
        ```bash
        $ conda info -e 
        ```

