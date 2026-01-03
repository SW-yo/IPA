2026/01/04

✓TLS：Transport Layer Security、インターネット通信を暗号化し、盗聴・改ざん・なりすましを防ぐためのセキュリティプロトコル、Layer4、ポート番号＝TCP443
✓DTLS：Datagram Transport Layer Security、UDPのようなデータグラムベースの通信を安全にするためのプロトコル、TLS（Transport Layer Security）を基にUDPの特性に合わせて拡張、Layer4、ポート番号＝UDP443（QUICで使用されている）
https://powerdmarc.com/ja/what-is-dtls/
✓QUIK：Quick UDP Internet Connections、Googleによって開発された新しい通信プロトコル、DTLSではなくTLS（通常は1.3）を使用、Layer4～7、「これからの標準はQUIC」ですが、「センサーや小型機器ならDTLS」
✓UDP：User Datagram Protocol、データグラム（datagram）とはネットワーク通信におけるデータの小さなまとまりで宛先アドレスなどの制御情報（ヘッダ）が付加されたもので、IP（インターネットプロトコル）などのコネクションレス型通信で使われる基本単位
✓IPsec：Internet Protocol Security、IPパケットの暗号化、Layer3
✓CHAP：Challenge-Handshake Authentication Protocol、PPPでチャレンジレスポンス認証機能をイーサネット上で提供、PPPoEにチャレンジレスポンスを、PAP（Password Authentication Protocol）よりも高いセキュリティを実現
✓TLS1.3：TCPのペイロードデータの暗号強度をTLSを強化
✓DTLS：UDPのペイロードデータの暗号化
✓QUICやWebRTCとの比較：「『これからの標準はQUIC』だけど『センサーや小型機器ならDTLS』」がGeminiの意見。 QUICはTLS 1.3を暗号機能として組み込みつつ自身でパケットの再送や順序を管理する仕組みを持っているのに対して、DTLSは基本的にそれらの管理は元のUDP通りで暗号機能を提供するセキュリティプロトコルだからレガシーでも使えるケースが多い。ちなみに、この書き方だとChatGPTは「厳密には間違ってる」と文句を言ってくる（レイヤーによって「再送」をするしないが異なるらしい）。WebRTCはDTLSを使ってリアルタイム通信のセキュリティを確保している。