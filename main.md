name: inverse
layout: true
class: center, middle, inverse

---
# Kubernetes Logging
# Introduction

---
layout: false
## whoami

.left-small[
    ![image](https://pbs.twimg.com/profile_images/994762110792953856/EheEvqBY_400x400.jpg)
]

.right-large[
- Kyohei Mizumoto(@kyohmizu)

- C# Software Engineer

- Interests
    - Docker/Kubernetes
    - Go
    - Security
]

---
### Required

- Kubernetesの概要程度の知識

### Targets

- Kubernetes Logging未経験者

---
### Contents

1. Logging Overview

1. Fluentd

1. Get Started with GKE

1. Demo

1. Other Services

---
class: center, middle, inverse
# Logging Overview

---
<center><img src=twelve-factor-app-logs.png width=85%></center>

---
### Logging

- 標準出力と標準エラー出力にログを出力

- "kubectl logs"コマンドで表示

- 安定保存のため、ログを集約して外部に転送

---
### kubectl logs

.zoom2[
```console
$ kubectl logs kube-dns-[num] -c kubedns -n kube-system
```
]

<center><img src=kubectl-logs.png width=100%></center>

---
class: header-margin
### Landscape

<center><img src=landscape.png width=100%></center>

---
class: center, middle, inverse
# Fluentd

---
class: header-margin
### Fluentd

.right-small[
<center><img src="https://docs.fluentd.org/logo/Fluentd_square.png" width=90%></center>
]

.left-large[
- CNCFがホストするプロジェクト

- DaemonSetを利用

- 標準出力ログを読み出して転送
]

---
class: header-margin
### Before Fluentd

<center><img src="https://www.fluentd.org/images/fluentd-before.png" width=80%></center>

---
class: header-margin
### After Fluentd

<center><img src="https://docs.fluentd.org/images/fluentd-architecture.png" width=85%></center>

---
### Architecture

- Unified Logging with JSON  
  プロセス(収集、フィルタリング、出力)の統一

- Pluggable Architecture  
  フレキシブルな入出力プラグイン

- Minimum Resources Required

- Built-in Reliability  
  バッファ、フェイルオーバーによるHA構成

---
### Forward To

- CloudWatch
- Elasticsearch
- Google Cloud Storage(GCS)
- Graylog
- Kafka
- Kinesis
- Amazon S3
- Stackdriver
- Syslog

etc...

---
### Get Started

[公式イメージ](https://github.com/fluent/fluentd-kubernetes-daemonset/tree/master/docker-image/v1.3)

<center><img src="fluentd-daemonset.png" width=85%></center>

---
class: center, middle, inverse
## Get Started with GKE

---
### Get Started with GKE

GKEではリソース作成済み

```console
$ kubectl get po -n kube-system | grep fluentd
// 結果は一部省略
fluentd-gcp-scaler-8b674f786-jc4wk  1/1  Running
fluentd-gcp-v3.2.0-4hqm6            2/2  Running
fluentd-gcp-v3.2.0-m5p49            2/2  Running
fluentd-gcp-v3.2.0-x6rlq            2/2  Running

```

---
### Stackdriver

Real-time Log Management and Analysis

- Seamlessly Resolve Issues

- Scalable and Fully Managed

- All Your Cloud Logs In One Place

- Real Time Insights

---
class: header-margin
### Stackdriver Monitoring

<center><img src="stackdriver.png" width=100%></center>

---
class: header-margin
### Stackdriver Logs Viewer

<center><img src="stackdriver-logs-viewer.png" width=100%></center>

---
class: center, middle, blue
# Demo

---
class: center, middle, inverse
# Other Services

---
class: header-margin
### Datadog

.right-small[
<center><img src="https://datadog-prod.imgix.net/img/presskit/DDlogo.jpg" width=100%></center>
]

.left-large[
- SaaS型の監視＆解析ツール

- 課金制

- 様々なサービスのメトリクスをシームレスに集約
]

---
class: header-margin
### Log Explorer

<center><img src="https://datadog-docs.imgix.net/images/logs/log_explorer_view-978012a0.png" width=100%></center>

---
### Log Management

- Datadog Agent がログを収集

    - DaemonSet for Kubernetes

    - 暗号化通信を使用してデータを送信

- ログのFiltering、Monitoring、Alert機能

- Custom Logs

---
class: header-margin
### Fluent Bit

<center><img src="https://fluentbit.io/assets/img/logo1-default.png" width=90%></center>

- シンプルかつ軽量なFluentd

- 既存のプラグインは使用不可

---
### Books

<center><img src="https://images-na.ssl-images-amazon.com/images/I/91VNghpL1EL.jpg" width=45%></center>

---
### Links

.zoom1[
The Twelve-Factor App  
[https://12factor.net/](https://12factor.net/)

Fluentd  
[https://www.fluentd.org/](https://www.fluentd.org/)

Fluent Bit  
[https://fluentbit.io/](https://fluentbit.io/)

Stackdriver Logging  
[https://cloud.google.com/logging/](https://cloud.google.com/logging/)

Datadog  
[https://www.datadoghq.com/](https://www.datadoghq.com/)
]

---
### Others

fluentd-gcp-scaler のコードについて調べたので、  
Qiita記事を投稿しました。

.zoom2[
<https://qiita.com/kyohmizu/items/cbf9cca76a826d8eb130>
]

---
class: center, middle, blue
# Thank you!
