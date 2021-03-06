# V6: 秘密と鍵

## 管理目標

本運用システムでは一般的にある種の秘密と暗号鍵を使用しています。これらは設定目的で使用でき、ユーザー名とパスワードを含めるか、暗号化手段による情報の保護を可能にします。このセクションではそのような機密情報をどのように扱うべきかを定義します。

検証対象のコンテナソリューションが以下の上位要件を満たすことを確認します。

* 機密情報を保護すること。
* 暗号マテリアルのセキュアな取り扱いを検証すること。
* 暗号鍵を定期的に入れ替えること。

## セキュリティ検証要件

| # | 説明 | L1 | L2 | L3 | 導入バージョン |
| --- | --- | --- | --- | -- | -- |
| **6.1** | アクセス制御を管理するために RBAC モデルが使用されていることを検証します。 |  | ✓ | ✓ | 1.0 |
| **6.2** | Docker Content Trust が有効であり適用されていることを検証します。 |  |  | ✓ | 1.0 |
| **6.3** | 機密情報が Dockerfile や Docker-Compose ファイルの一部としてあってはいけません。特に、API キーやパスワードなどの機密情報を扱うために Docker secrets などが使用されていることを検証します。 | ✓ | ✓ | ✓ | 1.0 |
| **6.4** | オーケストレーション結合鍵が一定の間隔で入れ替えられていることを検証します。 |  | ✓ | ✓ | 1.0 |
| **6.5** | auto-lock が有効である場合、auto-lock キーが定期的に入れ替えられていることを検証します。 |  | ✓ | ✓ | 1.0 |
| **6.6** | ノード証明書が定期的に入れ替えられていることを検証します。 |  | ✓ | ✓ | 1.0 |
| **6.7** | CA 証明書が定期的に入れ替えられていることを検証します。 |  | ✓ | ✓ | 1.0 |
| **6.8** | クラスタ間通信の相互 TLS 認証に使用される証明書の生成と検証に自前の CA が使用されていることを検証します。 |  | ✓ | ✓ | 1.0 |
| **6.9** | (UCP や DTR などに対して) 使用されている SSL/TLS 証明書が妥当性確認されていることを検証します。 | ✓ | ✓ | ✓ | 1.0 |
| **6.10** | 秘密 (暗号鍵やパスワードなど) が環境変数を使用してコンテナに公開されるなどではなく、秘密管理ソリューションでセキュアに使用されていることを検証します。 |  | ✓ | ✓ | 1.0 |
