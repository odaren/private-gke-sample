# private-gke-sample


1. Artifact registryのリポジトリを作る
2. サンプルアプリのコードとDockerfileをインストールする
```
git clone https://github.com/GoogleCloudPlatform/kubernetes-engine-samples
cd kubernetes-engine-samples/hello-app
```
3. Dockerイメージをビルド
```
docker build -t REGION-docker.pkg.dev/${PROJECT_ID}/hello-repo/hello-app:v1 .
```
4. Dockerイメージを Artifact registryにpushする
```
gcloud auth configure-docker REGION-docker.pkg.dev
docker push REGION-docker.pkg.dev/${PROJECT_ID}/hello-repo/hello-app:v1
```
5. 限定公開のGKEクラスタを作成する
6. アプリケーションをデプロイする
```
kubectl apply -f deployment.yaml
```
7. アプリケーションを公開する
```
kubectl apply -f service.yaml
```
8. ポート転送して、アプリケーションが公開されたか確認する
9. Ingressを作成する
```
kubectl apply -f ingress.yaml
```
10. ブラウザから、ロードバランサの外部IPアドレスにアクセスする
