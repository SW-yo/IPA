2025/12/21

✓SFA-512/256
	512に専用の初期化ベクトルによりハッシュ化→256に切り詰めて使用
✓MITRE ATT&CK（マイターアタック、MITRE Adversarial Tactics, Techniques, and Common Knowledge）
	サイバー攻撃者が実際に使う戦術（Tactics）と技術（Techniques）を体系的にまとめた、無料で公開されているナレッジベース（フレームワーク）
アメリカの非営利団体MITREが取りまとめ
https://www.intellilink.co.jp/column/security/2020/060200.aspx
https://attack.mitre.org/
✓STIX/TAXII（スティックスタクシー）
	サイバー脅威インテリジェンス（脅威情報）を標準的な形式で記述する言語（STIX：Structured Threat Information eXpression）と、それを自動で安全に交換するための通信プロトコル（TAXII：Trusted Automated eXchange of Indicator Information）を組み合わせた、サイバー脅威情報共有のための世界標準フレームワーク
https://www.ipa.go.jp/security/vuln/scap/stix.html
https://www.ipa.go.jp/security/vuln/scap/taxii.html
https://www.cloudflare.com/ja-jp/learning/security/what-is-stix-and-taxii/
✓サイバーキルチェーン
サイバー攻撃者が目的を達成するために実行する一連の行動プロセスをモデル化した概念
- 偵察(Reconnaissance)  
    標的となる個人、組織を調査する。例えば、インターネット、メール情報、組織への潜入等が挙げられる。
- 武器化(Weaponization)  
    攻撃のためのエクスプロイトキットやマルウェア等を作成する。
- デリバリー(Delivery)  
    マルウェアを添付したメールや悪意あるリンク付きメールを仕掛ける。また、直接対象組織のシステムへアクセスする。
- エクスプロイト(Exploitation)  
    標的にマルウェア等攻撃ファイルを実行させる。または、悪意あるリンクにアクセスさせ、エクスプロイトを実行させる。
- インストール(Installation)  
    エクスプロイトを成功させ、標的がマルウェアに感染する。これでマルウェア実行可能となる。
- C&C(Command & Control)  
    マルウェアとC&Cサーバーが通信可能となり、リモートから標的への操作が可能となる。
- 目的の実行(Actions on Objectives)  
    情報搾取や改ざん、データ破壊、サービス停止等、攻撃者の目的が実行される。
https://www.nec-solutioninnovators.co.jp/ss/insider/security-words/35.html