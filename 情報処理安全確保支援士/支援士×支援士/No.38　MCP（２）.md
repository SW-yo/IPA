2026/01/15

✓MCP
- Anthropicが提唱
- AIアプリケーションを外部システムに接続するためのオープンソース標準
- 外部サービスの呼び出しはツールを使う
- 攻撃者はツールを動かす指示が攻撃者に狙われやすい
- MCPの脆弱性はAPIの脆弱性
✓API
- APIはプログラム同士が会話するための形式がAPI
- 例としてOAuth2.0、OIDC（OpenID Connect）
- APIを呼び出すための手段がAPIキー（合鍵）
✓HTTPレスト
- アドレスでリソース指定
- HTTPのメソッドで操作を使い分ける
- ステートレス
✓MCPの仕事
- コンテキストの受け渡し（LLMに渡すデータの構造化）
- ツールの定義方法（HTTPレスト）
- ツール実行のライフサイクル
- データ形式と通信の前提（JSONベース）
- 「WEB API時代の設計思想をLLM向けに再整理」
✓MCPのスコープ外
- 認証・認可の方式
- セキュリティポリシーそのもの
- APIの中身の仕様
✓APIのアクセス制御の実装方法
- OAuth2.0：権限を安全に以上する仕組み、アクセストークンの形で提供
- OpenID Connect（OIDC）：OAuth＋主体の確認
✓AIのセキュリティ
- APIの権限指定はAIに限った話ではない
- AIのプロンプト自体の安全性も大事
https://gigazine.net/news/20260108-malicious-chrome-extensions-steal-chatgpt-conversations/