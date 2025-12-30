2025/12/28

✓脆弱性診断内製化ガイド：IPA
	- RISK=重要度×被害発生可能性（脅威と脆弱性）
	- リスクアセスメント
	- コントロールしやすいのは脅威よりも脆弱性
	- 対策する時に闇雲に行うのではなくどこにどんな対策をすると効率的か考える
	- セキュリティ・バイ・デフォルト/デザイン：ソフトウェアやハードウェアにおけるセキュリティ機能や設定を最初から（デフォルト/企画・設計段階）組み込んだ状態にすべきというプラクティス
	- シフトレフト・アプローチ：ソフトウェア開発ライフサイクルの左側（初期段階）にテストやセキュリティ対策を前倒しで組み込み、問題の早期発見と修正を行うことで品質向上、コスト削減、開発期間短縮を目指す手法
	- DevSecOps：開発（Development）、セキュリティ（Security）、運用（Operations）を統合し、システム開発ライフサイクル全体にセキュリティを組み込むアプローチ
	- CWE/CVE/CVSS
	- フルディスクロージャー：「真にセキュアなシステムとは、プロトコル、ソースコードなどすべての視点でオープンレビューに耐えうること」 「脆弱性に関する詳細情報はすべてのユーザが利用できること」
	- 協調的公開 (Coordinated Vulnerability Disclosure: CVD)/ 責任ある公開 (Responsible Disclosure)：「発見された脆弱性に関する情報をベンダ (開発者) などの関係者と調整し、修正プログラムなどの解決策が用意できてから一般公開する」 「攻撃リスクを抑えつつ利用者保護を優先する」という実務的な方法、EU発祥
	https://www.ipa.go.jp/jinzai/ics/core_human_resource/final_project/2025/Vulnerability-assessment.html
	-情報セキュリティ早期警戒パートナーシップガイドライン（IPA）：ISO/IEC 29147:2014（脆弱性の公開）、30111（脆弱性取り扱いプロセス）
	https://www.ipa.go.jp/security/guide/vuln/partnership_guide.html
	https://www.pwc.com/jp/ja/knowledge/column/awareness-cyber-security/psirt-commentary/vol7.html
	- 失敗例＝WannaCry
	https://www.proofpoint.com/jp/threat-reference/wannacry