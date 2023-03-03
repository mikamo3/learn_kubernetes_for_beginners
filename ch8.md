ReplicaSet: 指定したテンプレートに従って正しい数のPodが常に動いている状態にするクラスタ全体のPodマネージャ

レプリカを管理する仕組みは調整ループ,システムの現在の状態が望ましいようにするアクションを起こす

ReplicaSetコントローラが作った各Podは完全に同じ

ReplicasetはPodのLabelを使ってクラスタの状態を監視する

```kubectl describe rs ```で状態を見る

podがどのReplicaSetで管理されているかは

```kubectl get pods Pod名 -o yaml```で出力されるmetadata.ownerReferencesを確認

labelセレクタで絞り込めばReplicaSetに管理されているPodの集合も確認できる

アプリケーションの何らかのメトリクスでスケールすることを水平Podオートスケーリングという

(Podに必要なリソースを増やすことを垂直スケールという)

```
kubectl autoscale rs kuard --min=2 --max=5 --cpu-percent=80
```
こんな感じで設定

```
 kubectl get hpa
```

こんな感じでオートスケーラーを確認できる

削除する時```--casccade=false```をつけることでPodを残して削除できる