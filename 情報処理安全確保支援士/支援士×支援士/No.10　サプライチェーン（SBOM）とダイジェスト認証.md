2025/12/22

✓サプライチェーン
- ビジネス上の繋がり
- ソフトウェアの繋がり
✓SBOM（Software Bill of Materials）
	アプリケーションがどんなコンポーネントからできているか、あるいは依存関係を管理
	https://www.meti.go.jp/press/2024/08/20240829001/20240829001.html
	![[【IPA】SBOM導入・運用の手引き  1.pdf]]
✓HTTP認証機能
- ダイジェスト認証はMD5、SHAはハッシュ化（一方向性）でありエンコードではない
	- nonce：Number used once
	- opaque：サーバーがクライアントに返す「ランダムな文字列」
	- nc：nonce count
	- algorithm：デフォルトが非推奨のMD5なので使われなくなってきた
	- cnonce：Client nonce
- ベーシック認証はBASE64でエンコード（可逆性）して送信
- 今はJWT（JSON Web Token）、OAuth（オーオース、「Google（X）でログイン」に使われる）