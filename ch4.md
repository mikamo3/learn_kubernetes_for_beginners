* namespace おぶじぇくとを構造化。要はフォルダ
* context namespaceを恒久的に変更したい時
* kubectlはAPIサーバからのレスポンスをhuman readable


ファイルに書かれたオブジェクトをk8sに作成する
```
kubectl apply -f obj.yml
```

ex: bar というpodにラベルをつける
```
kubectl label pods bar color=red
```

けす
```
kubectl label pods bar color-
```