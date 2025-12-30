2025-12-16作成

# 基本情報技術者試験対策：JavaとECMAScript重点項目

IPAの過去問題を分析し、令和8年春試験に向けたJavaとECMAScriptの重点対策をまとめました。基本情報技術者試験の午後問題で頻出するテーマを中心に構成しています。

## 重点を置く学習内容

### Javaの重点項目
1. **オブジェクト指向プログラミングの基礎**
   - カプセル化、継承、ポリモーフィズムの実装
   - インターフェースと抽象クラスの使い分け
   - 例外処理（checked/unchecked exceptionの理解）

2. **コレクションフレームワーク**
   - List、Set、Mapの特徴と使い分け
   - Iteratorパターンの理解
   - ストリームAPI（filter, map, collectなど）

3. **ファイル入出力とデータ処理**
   - FileクラスとIO/NIO API
   - CSV/JSONデータの読み書き
   - 文字コードの取り扱い

### ECMAScriptの重点項目
1. **非同期処理**
   - Promise、async/awaitの理解
   - イベントループの仕組み
   - Fetch APIを使った非同期通信

2. **関数とオブジェクト**
   - 関数宣言と関数式の違い
   - thisの挙動とbind/call/apply
   - オブジェクトのプロトタイプ継承

3. **DOM操作とイベントハンドリング**
   - 要素の選択・操作・スタイル適用
   - イベントの伝搬（バブリング・キャプチャリング）
   - フォームバリデーションの実装

## 具体的な勉強方法

### Java
1. **過去問題の実装演習**
   - IPAの過去問題（特に令和5年度以降）のアルゴリズム問題をJavaで実装
   - 1つのアルゴリズムを複数の実装方法で解く練習
   - 時間を計って解答を完成させる訓練

2. **コードリーディングの強化**
   - 誤ったコードのデバッグ演習
   - コメントのないコードの意味理解
   - 設計パターンが適用されたコードの読み解き

3. **実践的なプロジェクト演習**
   - CSVデータを読み込んで集計・分析するプログラム
   - 複数クラスを用いた簡易在庫管理システム
   - 単体テストを含む小さなアプリケーションの作成

### ECMAScript
1. **ブラウザ環境での実践演習**
   - フォームバリデーション機能の実装
   - 非同期通信を使った簡易APIクライアント
   - レスポンシブデザイン対応のUIコンポーネント作成

2. **コード変換演習**
   - コールバック地獄をPromise/asyncでリファクタリング
   - 従来の関数スタイルからアロー関数への変換
   - varからlet/constへの変換とスコープの理解

3. **アルゴリズム実装演習**
   - 配列操作系アルゴリズム（ソート、検索など）
   - 文字列操作アルゴリズム
   - 再帰アルゴリズムの理解と実装

## 具体的な文法

### Javaの必須文法
```java
// オブジェクト指向
public interface DataAccess {
    void save(Data data);
    Data load(String id);
}

public abstract class BaseRepository {
    protected Connection getConnection() { /* */ }
}

// 例外処理
try {
    // ファイル操作
} catch (IOException e) {
    throw new RuntimeException("ファイル処理に失敗", e);
} finally {
    // リソース解放
}

// ストリームAPI
List<String> filteredList = dataList.stream()
    .filter(data -> data.isActive())
    .map(Data::getName)
    .collect(Collectors.toList());
```

### ECMAScriptの必須文法
```javascript
// 非同期処理
async function fetchData(url) {
    try {
        const response = await fetch(url);
        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }
        return await response.json();
    } catch (error) {
        console.error('データ取得エラー:', error);
        throw error;
    }
}

// オブジェクトと配列の操作
const { name, age, ...rest } = userInfo;
const combinedArray = [...array1, ...array2];

// 関数とthisの操作
const obj = {
    value: 42,
    getArrowFunc: () => console.log(this.value), // thisは親スコープ
    getNormalFunc() { console.log(this.value); } // thisは呼び出し元
};
```

## 令和8年春 予想問題

### Java 予想問題
**テーマ：在庫管理システムの実装**

与えられた商品データ（CSV形式）を読み込み、以下の機能を実装するプログラムを作成せよ：
1. 商品カテゴリ別の在庫集計
2. 在庫数が一定数未満の商品を警告リストとして抽出
3. 指定された商品IDの在庫数更新機能

条件：
- クラス設計に適切なカプセル化を適用すること
- 例外処理を適切に実装すること
- Stream APIを活用してデータ処理を実装すること

```java
// 考えられる解答の骨子
public class InventorySystem {
    private Map<String, Product> products = new HashMap<>();
    
    public void loadFromCsv(String filePath) throws IOException {
        // CSV読み込み処理（例外処理含む）
    }
    
    public Map<String, Integer> getStockByCategory() {
        return products.values().stream()
            .collect(Collectors.groupingBy(
                Product::getCategory,
                Collectors.summingInt(Product::getStock)
            ));
    }
    
    public List<Product> getLowStockProducts(int threshold) {
        return products.values().stream()
            .filter(p -> p.getStock() < threshold)
            .collect(Collectors.toList());
    }
}
```

### ECMAScript 予想問題
**テーマ：非同期データ処理とUI更新**

ECMAScriptを用いて、以下の要件を満たすWebアプリケーションの一部を実装せよ：
1. REST APIから商品データを非同期で取得
2. 取得したデータをテーブル形式で表示
3. 検索ボックスによる絞り込み機能
4. エラーハンドリングとローディング状態の表示

条件：
- async/awaitを活用した非同期処理を実装すること
- DOM操作とイベントハンドリングを適切に実装すること
- エラーやローディング状態のUXを考慮した実装にすること

```javascript
// 考えられる解答の骨子
class ProductApp {
    constructor() {
        this.products = [];
        this.isLoading = false;
        this.bindEvents();
    }
    
    bindEvents() {
        document.getElementById('searchInput').addEventListener('input', 
            debounce(this.filterProducts.bind(this), 300));
    }
    
    async loadProducts() {
        this.setLoading(true);
        try {
            const data = await fetchData('/api/products');
            this.products = data;
            this.renderProducts(data);
        } catch (error) {
            this.showError('商品データの取得に失敗しました');
        } finally {
            this.setLoading(false);
        }
    }
    
    renderProducts(products) {
        // DOM操作によるテーブルレンダリング
    }
}
```

## 学習スケジュールの提案

1. **基礎固め（2ヶ月）**
   - Java/ECMAScriptの基本文法の復習
   - 過去問題のコード読解演習

2. **実践演習（1.5ヶ月）**
   - 想定された出題形式での実装演習
   - 制限時間内でのプログラム作成訓練

3. **総合演習（0.5ヶ月）**
   - 過去問題の総復習
   - 予想問題の模擬解答作成

基本情報技術者試験は実践的な知識が問われるため、単なる文法の暗記ではなく、実際の問題を解く経験を積むことが重要です。IPAの公式過去問題を十分に活用し、特に令和5年度以降の問題を中心に分析・演習を行うことをお勧めします。