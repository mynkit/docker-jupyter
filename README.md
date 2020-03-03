# docker-jupyter-sample

## dockerでjupyter立ち上げでアクセスする方法

* dockerでjupyterを立ち上げ．(http://localhost:9999 にアクセスすればjupyterみれる )

```sh
docker run -d --name notebook -v $PWD:/home/jovyan -p 9999:8888 jupyter/datascience-notebook
```

* tokenを取得(http://localhost:9999 にアクセスしたときに聞かれる)

```sh
docker logs notebook 2>&1 | grep 'http://127.0.0.1:8888/?token=' 2>&1 | sed -e "s/^.*token=\(.*\).*$/\1/" 2>&1 | sed -n -e \$p
```

* dockerを閉じたいとき

```sh
docker stop notebook && docker rm notebook
```

* dockerで使ってないコンテナやイメージを全整理(削除)する

```sh
docker system prune
```
