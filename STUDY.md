## minikube on Macで起動したserviceのLocal URLを調べる
- kubernatesでserviceをapplyする
- `minikube` コマンドでURLを特定

  ```
  > minikube service web-svc --url
  🏃  Starting tunnel for service web-svc.
  |-----------|---------|-------------|------------------------|
  | NAMESPACE |  NAME   | TARGET PORT |          URL           |
  |-----------|---------|-------------|------------------------|
  | default   | web-svc |             | http://127.0.0.1:64359 |
  |-----------|---------|-------------|------------------------|
  http://127.0.0.1:64359
  ```

## secretに記載するencorded文字列を取得する方法

```
> echo -n "YOUR_SECRET_KEY" | base64
WU9VUl9TRUNSRVRfS0VZ
```