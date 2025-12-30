2025/12/23

✓CT
- RFC9162
	https://datatracker.ietf.org/doc/html/rfc9162
- CT：Certificate Transparency、サーバー証明書の発行状況を監視・監査するための仕組み、CP/CPSに基づいた証明書発行ログ、CTログサーバーを利用、ログを登録した時にSCTが発行される、CTログサーバーは複数のLog Operatorが管理している
	https://jprs.jp/pubcert/about/CT/
	https://crt.sh/
- HPKP：HTTP公開鍵ピンニング、 HTTP Public Key Pinning、偽造された証明書によるMITM攻撃のリスクを減らすために、特定の暗号化公開鍵を特定のウェブサーバーに関連付けるようにウェブクライアントに指示するセキュリティ機能
- HSTS：HTTP Strict Transport Security、HSTSが有効なサイトへはhttp://が指定されていても自動的にhttps://に置き換えて通信が行われる
	https://e-words.jp/w/HSTS.html
- RA：Registration Authority、登録局、デジタル証明書の認証局（CA）の役割のうち、利用者からの発行者申請の受付や本人確認などの業務を行う機関
	https://e-words.jp/w/%E7%99%BB%E9%8C%B2%E5%B1%80.html
	※認証局の役割は発行局（IA：Issuing Authority）、登録局（RA：Registration Authority）、検証局（VA：Validation Authority）の3つに分かれており、大規模なPKI（公開鍵基盤）などではそれぞれが個別に設置・運用され役割分担していることがある
✓Passkey
- クライアント証明書認証：ユーザーのPCやスマホなどの端末にインストールされた電子証明書（クライアント証明書）を使って、その端末が正規のものであるかを確認する認証方式
- リスクベース認証：ユーザーのアクセス環境（場所、時間、デバイスなど）を分析し、普段と異なる「リスクが高い」と判断した場合のみ追加の本人確認（追加認証）を求める仕組み
- EV SSL/TLS：SSL/TLS暗号化通信方式における個人情報やクレジット情報、機密文書（ファイル）といった、第三者に対し守秘すべきデータの受け手が、「なりすまし」されていないか（守秘情報の盗み見・詐取を企む偽者ではないか）どうかを、SSL認証局（中立公平な信頼できる認証機関であることの厳格な認証を毎年KPMG, Deloitte等による外部監査機関から取得することが要件）が業界団体（CA Browser Forum）で統一規格化された手順に基づき身元確認していることを、守秘すべきデータの送り手たるサイト利用者に対し証明するためのサービス
- Passkey：秘密鍵はこれまでTPM (Trusted Platform Module)と呼ばれるコンピュータのセキュリティを強化する専用のセキュリティチップに保存されていたが、Passkeyはプラットフォームベンダーがクラウド（iCloud Keychain、Windows Hello、Google Password Manager）でバックアップしてくれる、鍵ペアはデバイスの認証器で作る
	https://www.jcert.co.jp/about_ssl/evssl/
- FIDO：公開鍵とデジタル署名（レスポンスやオリジンを含めて秘密鍵で作成）