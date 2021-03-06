# V5: イメージ配布

## 管理目標

コンテナを稼働させるためには、まずイメージをビルドする必要があります。イメージはコンテナ内で実行されるものやたとえば使用されるソフトウェアパッケージのバージョンを定義します。膨大な量のコンテナのベースとなる可能性があるため、環境の安全な運用を確保するためには各イメージのセキュリティが不可欠です。

検証対象のコンテナソリューションが以下の上位要件を満たすことを確認します。

* イメージが堅牢化されていること。
* イメージ内に機密データが保存されていないこと。
* イメージに脆弱性のあるコンポーネントがないかチェックされていること。

## セキュリティ検証要件

| # | 説明 | L1 | L2 | L3 | 導入バージョン |
| --- | --- | --- | --- | -- | -- |
| **5.1** | 三つ以上の奇数のイメージレジストリ (DTR など) が使用されていることを検証します。 |  |  | ✓ | 1.0 |
| **5.2** | イメージレジストリでガベージコレクションが有効であり、定期的に実行されていることを検証します。 | ✓ | ✓ | ✓ | 1.0 |
| **5.3** | すべてのイメージが定期的に自動セキュリティスキャンを受けていることを検証します。 |  | ✓ | ✓ | 1.0 |
| **5.4** | ローカルキャッシュではなく対応する常に最新のイメージに基づいてコンテナが作成されていることを検証します。 | ✓ | ✓ | ✓ | 1.0 |
| **5.5** | すべてのイメージがタグを使用しており、production/master のみがデフォルトの _latest_ タグの使用が許可されていることを検証します。 |  | ✓ | ✓ | 1.0 |
