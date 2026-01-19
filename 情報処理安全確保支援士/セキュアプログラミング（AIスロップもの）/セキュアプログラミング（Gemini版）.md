2025-12-16作成

ご提示いただいた過去問（R7秋_午後.pdfの問1）の傾向と、情報処理安全確保支援士試験のシラバス（C++、Java、ECMAScriptの3言語が出題範囲）に基づき、JavaとECMAScript（JavaScript）で重点的に対処すべき項目を、より具体的な文法を含めてまとめます。

また、この傾向を踏まえた「令和8年春の予想問題」も作成します。

---

## 🔒 セキュアプログラミングの重点学習項目（過去問ベース）

|**言語**|**重点を置く学習内容**|**具体的な勉強方法**|**具体的な文法・API/設定**|
|---|---|---|---|
|**ECMAScript** **(JavaScript)**|1. クロスサイト・スクリプティング (XSS) 1111|**出力処理の徹底:** HTML要素の属性値やタグ間に、ユーザ入力をそのまま出力しない。|* **エスケープ:** ライブラリによる自動エスケープ処理の利用。手動で行う場合の**HTMLエンコーディング**関数。* **DOM操作:** `element.textContent = data` を使用し、`element.innerHTML = data` の使用を極力避ける。* **設定:** `Content-Security-Policy: ...` の適切なディレクティブ（例：`default-src 'self'`, `script-src 'self' 'nonce-...'`, **`unsafe-inline`の禁止**）2222。|
||2. クロスサイト・リクエスト・フォージェリ (CSRF) 3|**リクエストの検証:** 状態変更を伴うPOST/PUT/DELETEリクエストに対して、正規の送信元であることを検証する。|* **CSRFトークン:** HTTPリクエストのボディまたはヘッダーにトークンを含め、サーバー側で検証する処理ロジック 4444。* **Cookie設定:** **`SameSite=Strict`** または **`Lax`** 属性を付与する。* **メソッドの分離:** 状態を変更しない操作はGETメソッドに限定する。|
|**Java**|**1. SQLインジェクション**|**入力検証とデータベース連携:** ユーザ入力を含む文字列でSQLを組み立てない。|* **安全なAPI:** **`java.sql.PreparedStatement`** を使用し、プレースホルダ（`?`）で変数値をバインドする。* **危険なAPI:** `java.sql.Statement`や文字列連結によるSQL文生成は避ける。|
||**2. OSコマンドインジェクション**|**外部コマンド実行の制御:** ユーザ入力からOSコマンドを構築しない。|* **安全なAPI:** `java.lang.ProcessBuilder`を使用し、コマンドと引数を**リスト**で分離して渡す。* **危険なAPI:** `Runtime.getRuntime().exec(String command)` や、文字列連結によるコマンド生成は避ける。* **入力検証:** 外部コマンドの引数に利用するユーザ入力は、ホワイトリスト方式で厳格に検証する。|
||**3. 認証・アクセス制御**|**ロール/権限チェック:** サーバー側で、リクエストされた操作を実行する権限が利用者にあるかを常に確認する。|* **コード:** `if (user.hasPermission("ROLE_ADMIN")) { ... }` のような、**サーバーサイドでの権限検証ロジック**の実装。* **設定:** Webフレームワークやコンテナ設定（例：`web.xml`）での認証・認可設定。|

---

## 🎯 令和8年春 情報処理安全確保支援士試験 予想問題（午後I 問1）

### 設問1：XSS脆弱性の特定と対策（ECMAScript）

Webアプリケーション開発者Dさんが作成したECMAScript（JavaScript）のコードの一部を示す。このコードは、URLパラメータから値を取得し、それをページ内の要素に表示する。

**【脆弱なコード】**

JavaScript

```
// URL: https://example.com/page?name=John%3Cscript%3Ealert(1)%3C/script%3E
function displayUserName() {
    const urlParams = new URLSearchParams(window.location.search);
    const userName = urlParams.get('name');

    // (1) ユーザー名を直接HTMLに挿入
    document.getElementById('welcome-message').innerHTML = 'ようこそ、' + userName + 'さん';
}
```

(1) 脆弱なコード(1)が引き起こす脆弱性の名称を答えよ。

(2) この脆弱性を利用した攻撃が成功する仕組みを、HTML要素とECMAScriptの処理に言及して、具体的に述べよ。

(3) 脆弱なコード(1)を、セキュリティを確保したコードに修正せよ。

### 設問2：CSRF対策の検証（ECMAScript/HTTP）

ユーザーが退会処理を行う際のHTTPリクエストと、それに対するセキュリティ設定の一部を示す。退会処理はPOSTリクエストで行われる。

**【退会処理リクエスト】**

HTTP

```
POST /user/withdraw HTTP/1.1
Host: secure.app.com
Cookie: JSESSIONID=abc12345;
Content-Length: 0
```

**【サーバー設定】**

```
Set-Cookie: JSESSIONID=abc12345; Secure; HttpOnly; SameSite=Lax
```

(1) 上記のサーバー設定における SameSite=Lax のCookie属性が、攻撃者のWebサイトからのGETリクエストによるCSRF攻撃を防げるか否かを答えよ。また、その理由を述べよ。

(2) 退会処理リクエストにCSRF対策を追加する場合、最も一般的に採用される対策（トークンを用いる方法）において、ECMAScript側で行う必要がある処理（リクエスト送信前）と、サーバー側で行う必要がある処理（リクエスト受信時）をそれぞれ具体的に述べよ。

### 設問3：SQLインジェクション脆弱性の対策（Java）

Javaアプリケーションのコードの一部を示す。このコードは、ユーザIDを基にデータベースからユーザー情報を検索する。

**【脆弱なコード】**

Java

```
// String userIdはユーザーからの入力値
String sql = "SELECT name, email FROM users WHERE id = '" + userId + "'";

// (2) 実行
try (Statement stmt = connection.createStatement()) {
    // (3)
    ResultSet rs = stmt.executeQuery(sql); 
    // ... 
} catch (SQLException e) {
    // ...
}
```

(1) 脆弱なコード(2)と(3)が引き起こす脆弱性の名称を答えよ。

(2) 攻撃者が userId に a' OR '1'='1 を入力した場合、意図しない結果を招く理由を、実行されるSQL文を示して説明せよ。

(3) 脆弱なコード(2)と(3)を、セキュリティを確保したコードに修正し、データベース連携に用いるJavaのAPI名を明記せよ。



お任せください。先に作成した「令和8年春 情報処理安全確保支援士試験 予想問題（午後I 問1）」に対する模範解答を作成します。

---

## 🎯 令和8年春 情報処理安全確保支援士試験 予想問題 模範解答（午後I 問1）

### 設問1：XSS脆弱性の特定と対策（ECMAScript）

(1) 脆弱なコード(1)が引き起こす脆弱性の名称を答えよ。

解答: クロスサイト・スクリプティング (XSS)

(2) この脆弱性を利用した攻撃が成功する仕組みを、HTML要素とECMAScriptの処理に言及して、具体的に述べよ。

解答:

1. URLパラメータに含まれる <script>alert(1)</script> という文字列が、ECMAScriptの処理によって取得される。

2. 脆弱なコード(1)では、この文字列が document.getElementById('welcome-message').**innerHTML** プロパティを通じてHTML要素（welcome-message）に挿入される。

3. ブラウザは挿入された文字列をHTMLタグとして解釈し、悪意のある <script> タグを実行してしまう。

4. 結果として、攻撃者が意図したスクリプト（例：alert(1)）が実行される。

(3) 脆弱なコード(1)を、セキュリティを確保したコードに修正せよ。

解答:

javascript // ユーザー名をそのままHTMLタグとして解釈させないように、textContentを使用する document.getElementById('welcome-message').textContent = 'ようこそ、' + userName + 'さん';

### 設問2：CSRF対策の検証（ECMAScript/HTTP）

(1) 上記のサーバー設定における SameSite=Lax のCookie属性が、攻撃者のWebサイトからのGETリクエストによるCSRF攻撃を防げるか否かを答えよ。また、その理由を述べよ。

解答:

* 防げない。

* 理由: SameSite=Lax は、クロスサイトでのトップレベルナビゲーション（例：攻撃サイトからのリンククリックやGETフォーム送信）によるGETリクエストの場合、Cookieの送信を許可するため。この場合、POSTリクエストではなくGETリクエストによる退会処理が設計されていると、攻撃が成功する可能性がある。

(2) 退会処理リクエストにCSRF対策を追加する場合、最も一般的に採用される対策（トークンを用いる方法）において、ECMAScript側で行う必要がある処理（リクエスト送信前）と、サーバー側で行う必要がある処理（リクエスト受信時）をそれぞれ具体的に述べよ。

解答:

* ECMAScript側（リクエスト送信前）: フォーム送信や非同期通信（Ajax/Fetch）を行う際に、HTML上の隠しフィールドやHTTPヘッダーからCSRFトークンの値を取得し、その値をリクエスト（例：POSTリクエストのボディ）に含めて送信する。

* サーバー側（リクエスト受信時）: リクエストに含まれるCSRFトークンの値が、サーバー側でセッションまたはCookieなどに格納されている正規のトークンの値と一致するか検証する。一致しない場合は、リクエストを拒否する。

### 設問3：SQLインジェクション脆弱性の対策（Java）

(1) 脆弱なコード(2)と(3)が引き起こす脆弱性の名称を答えよ。

解答: SQLインジェクション

(2) 攻撃者が userId に a' OR '1'='1 を入力した場合、意図しない結果を招く理由を、実行されるSQL文を示して説明せよ。

解答:

* 実行されるSQL文: SELECT name, email FROM users WHERE id = 'a' OR '1'='1'

* 理由: SQL文の末尾にある WHERE 句が、常に真となる条件式 OR '1'='1' によって上書きされるため、データベースは条件に関係なく全てのユーザーの情報（または意図しない情報）を返してしまう。

(3) 脆弱なコード(2)と(3)を、セキュリティを確保したコードに修正し、データベース連携に用いるJavaのAPI名を明記せよ。

解答:

* API名: java.sql.PreparedStatement

* 修正コード例:

```java

// 安全なAPI (PreparedStatement) を使用

String sql = "SELECT name, email FROM users WHERE id = ?";

```
    try (PreparedStatement pstmt = connection.prepareStatement(sql)) {
        // プレースホルダに変数値を設定
        pstmt.setString(1, userId); 
        
        // 実行（SQL文は安全に構築される）
        ResultSet rs = pstmt.executeQuery(); 
        // ...
    } catch (SQLException e) {
        // ...
    }
    ```
```