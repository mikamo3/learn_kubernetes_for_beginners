# label annotation

label Pod,Replicasetといったオブジェクトに付与できるkey,valueのペア

annotation ツールやライブラリを便利に使用するために必要なオブジェクトを特定しない情報


label利用例

```
$ kubectl run alpaca-prod \
  --image=gcr.io/kuar-demo/kuard-amd64:1 \
  --replicas=2 \
  --labels="ver=1,app=alpaca,env=prod"
$ kubectl run bandicoot-prod \
  --image=gcr.io/kuar-demo/kuard-amd64:2 \
  --replicas=2 \
  --labels="ver=2,app=bandicoot,env=prod"
$ kubectl run bandicoot-staging \
  --image=gcr.io/kuar-demo/kuard-amd64:2 \
  --replicas=1 \
  --labels="ver=2,app=bandicoot,env=staging"

$ kubectl get deployments --show-labels

NAME               ... LABELS
alpaca-prod        ... app=alpaca,env=prod,ver=1
alpaca-test        ... app=alpaca,env=test,ver=2
bandicoot-prod     ... app=bandicoot,env=prod,ver=2
bandicoot-staging  ... app=bandicoot,env=staging,ver=2
```

```
kubectl get pods --selector="ver=2"
```
みたいに絞り込みができる

annotationは

* オブジェクトの変更理由の記録
* スケジューリングポリシーの伝達
* UIの見た目（base64で画像など仕込める）
etc

特定のリソースに強く関連付けられた小さなデータを入れるのに使うのが良さそう

```
metadata:
  annotations:
    example.com/icon-url: "https://example.com/icon.png"
```