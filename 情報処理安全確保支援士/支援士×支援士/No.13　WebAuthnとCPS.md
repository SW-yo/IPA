2025/12/22

✓WebAuthn
- Web Authnは認証情報が特定のオリジン（ドメイン）に紐付いている確認することで偽サイト（プロキシ）経由で不正ログインすることはできないようにしている
	https://www.lac.co.jp/lacwatch/service/20230316_003311.html
- 加えてユーザーは持っている認証器で秘密鍵による署名を作成して送りサーバーは公開鍵で確認する
- 攻撃者はログイン自体が成立しないため、盗むべきセッションCookieすら発行されない
- スミッシング：SMS（ショートメッセージ）によるフィッシング
- MFA：Multi-Factor Authentication、他要素認証
- TOTP：Time-based One-Time Password、時間ベースのワンタイムパスワード
- AiTM：Adversary in The Middle、多要素認証を通過した状態のデータ（セッションCookie）を盗み出すフィッシング攻撃
✓JSONの中のclientDataJason（W3C WebAutndeで定義、クライアントとIdP（RP）間のデータ形式はJSON）
- challenge
- origin（スキーム＋ホスト名＋ポート番号による、これでなりすましを防止）
- type
✓CPS（Certification Practice Statement）
- 公開鍵の運用等の規定
	https://jprs.jp/glossary/index.php?ID=0246
- CP/CPS：ポリシーの公開（例：JPRS）
	- CP（JPRSサーバー証明書認証局証明書ポリシー（Certificate Policy））：基準
	- CPS（JPRSサーバー証明書認証局運用規程（Certification Practice Statement））：運用規定
	https://jprs.jp/pubcert/info/repository/JPRS-CP.pdf
	https://jprs.jp/pubcert/info/repository/JPRS-CPCPS.pdf
- DigiNotarハッキング事件（オランダ、2011年）：認証局をハッキングして証明書を偽造して通信の盗聴
- MITM：Man-in-the-Middle Attack、中間者攻撃。通信する2者間の間に第三者が割り込み、通信内容を盗聴・改ざんするサイバー攻撃
	https://www.nri-secure.co.jp/glossary/mtm-attack