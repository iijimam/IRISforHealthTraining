# Interoperabilityのトレーニングで使うコンテナ環境作成用

コンテナ名違うのですが、以下の図のイメージの2個のコンテナを立ち上げます。
![](https://github.com/iijimam/NoPWS/blob/master/assets/IRIS-WG.png)

## 起動手順

- 1. [tempディレクトリ](/temp/)のPermissionを変更するためシェルを動かします。

    ホストの[tempディレクトリ](/temp/)をコンテナの/temp ディレクトリにボリュームマウントしています。

    ```
    ./setup.sh
    ```

- 2. キーを準備します。

    コンテナ用キーを　iris.key　としてcloneして作成されたディレクトリ直下においてください。
    
    ARM用はARM版コンテナ用キーを利用してください。

- 3. コンテナをビルドしながら開始します。

    Webサーバのポートはコンテナでは80ですが、8080に割り当てています。

    IRISのスーパーサーバーポート（JDBCの接続などに利用します）は、コンテナ内は1972です8082に割り当てています。

    修正される場合は、[docker-compose.yml](/docker-compose.yml)のportsの設定を変更してください。

    注意：ARM用コンテナを利用する場合は[Dockerfileの２行目](/Dockerfile#L2)のコメントを外してから実行してください。

    ```
    docker compose up -d --build
    ```

- 4. コンテナへのログイン

    IRISのコンテナ名は iris4hです。
    ```
    docker exec -it iris4h bash
    ```

- 5. コンテナを停止する場合

    ※コンテナを止めるだけなので作成した内容は消えません。

    ```
    docker compose stop
    ```

- 6. コンテナ破棄

    ※コンテナを削除するため作成した内容も全てなくなります。

    ```
    docker compose rm
    ```

