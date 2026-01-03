2026/01/03

✓TLS1.3の暗号スイート：AEAD（Authenticated Encryption with Associated Data、例：AES128-GCM）とハッシュアルゴリズム（例：SHA256）の組み合わせ、鍵交換と署名を外して暗号化とハッシュ関数だけの構成に変更、認証付き暗号
https://www.ibm.com/docs/ja/odm/8.12.0?topic=configurations-configuring-tls-protocols-cipher-suites
https://study-sec.com/aead/
✓暗号スイート：Cipher suite、鍵交換アルゴリズム・認証方式・サイファー（暗号そのものや暗号化・復号のアルゴリズム）・メッセージ認証符号の組み合わせ
- ECDHE：Elliptic Curve Diffie-Hellman Ephemeral、議交換アルゴリズム
- RSA：暗号を鍵認証方式に使用
- AES-128：サイファーとして使用し暗号利用モードはGCM（Galois/Counter MODE）を使用
- SHA-256：メッセージ認証符号（HMAC：Hash-based Message Authentic Code）として使用
- MAC：Message Authentication Code、相手から届いたメセージが途中で改ざんやすり替えに遭っていないか検証するための短い符号（HMACアルゴリズムsha256などを使用）
- 認証タグ：MACの代わりに使用、AES-GCM（Advanced Encryption Standard - Galois/Counter Mode、AEADモードのAES)
- ノンス ：nonce、暗号技術やブロックチェーンなどで使われる「number used once（一度だけ使われる数値）」の略、リプレイ攻撃を防いだり暗号化処理をランダム化したりマイニングの難易度調整に使われたりする使い捨てのランダムな値
https://www.ipa.go.jp/security/crypto/guideline/ssl_crypt_config.html
![[IPA_TLS 暗号設定 ガイドライン.pdf]]