# k8sを使った開発

## 参考

[ここ](https://github.com/coreos/coreos-kubernetes/tree/master/multi-node/vagrant)からパクってきました。

## 依存

- openssl
- vagrant 2.0.2

<!-- https://coreos.com/tectonic/docs/latest/tutorials/kubernetes/getting-started.html 
https://github.com/coreos/coreos-kubernetes/tree/master/multi-node/vagrant
-->

## 開発用コマンド

### k8s のコマンドの例

[原文](https://kubernetes.io/docs/concepts/overview/object-management-kubectl/overview/)

#### 命令的管理

Kubernetesオブジェクトは、kubectlコマンドラインツールとYAMLまたはJSONで記述されたオブジェクト構成ファイルを使用して、作成、更新、および削除できます。

[原文](https://kubernetes.io/docs/concepts/overview/object-management-kubectl/imperative-config/)

##### 構成ファイルから作成する

```bash
kubectl create -f nginx.yaml
```

##### 2つまとめて削除する

```bash
kubectl delete -f nginx.yaml -f redis.yaml
```

##### 構成を上書きしてオブジェクトを更新する

```bash
kubectl replace -f nginx.yaml
```

#### 宣言的管理

Kubernetesオブジェクトは、複数のオブジェクト構成ファイルをディレクトリに格納し、`kubectl apply` を使用して必要に応じてそれらのオブジェクトを再帰的に作成および更新することで、作成、更新、および削除できます。この方法は、変更をオブジェクト構成ファイルにマージすることなく、ライブオブジェクトに書き込まれたデータを保持します。

[原文](https://kubernetes.io/docs/concepts/overview/object-management-kubectl/declarative-config/)

##### configsディレクトリ内のすべてのオブジェクト設定ファイルを処理し、ライブオブジェクトを作成またはパッチする

```bash
kubectl apply -f configs/
```

##### 再帰的にディレクトリを処理する

```bash
kubectl apply -R -f configs/
```
