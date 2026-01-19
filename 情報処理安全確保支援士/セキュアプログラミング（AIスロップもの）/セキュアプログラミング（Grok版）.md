2025-12-16作成

### Javaの重点対処項目

基本情報技術者試験（旧午後問題）の過去問を基に、Java関連の問題は主にオブジェクト指向プログラミングの理解と実装を問うものが多く、クラス設計やコレクションの活用が頻出しています。令和5年度以降の科目Bでは疑似言語中心にシフトしましたが、過去問ベースでJavaの基礎を固めることでアルゴリズム実装力が向上します。

#### 重点を置く学習内容
- **オブジェクト指向の基本概念**: クラス、インスタンス、継承、ポリモーフィズム、多態性。過去問ではあみだくじやキャッシュシステムのようなクラス階層設計が登場。
- **コレクションAPI**: List（ArrayList, LinkedList）、Map（HashMap）。内部クラスやリストベースのデータ管理が頻出。
- **例外処理とエラー管理**: IndexOutOfBoundsExceptionなどの投げ方とキャッチ。引数検証が重要。
- **文字列・配列処理**: 文字列の埋め込み、配列の探索・ソート。API（String, Arrays）の活用。
- **抽象クラス・インターフェース**: 抽象メソッドの実装とオーバーライド。キャッシュやリスト操作で多用。

#### 具体的な勉強方法
- **過去問演習**: fe-siken.comの過去問道場で平成25年春期・27年秋期などのJava問題を繰り返し解く。1問あたり30分以内で解答し、解説でAPI仕様を確認。
- **コード実装練習**: EclipseやIntelliJで過去問のプログラムを再実装。変数の変化をトレースし、デバッグツールでステップ実行。
- **参考書活用**: 「キタミ式イラストIT塾 Java入門」で文法を視覚的に学び、1日1章ペースで進める。週末に模擬試験として5問解く。
- **オンラインリソース**: Oracle公式ドキュメントでAPI（java.util.Listなど）を参照。YouTubeの過去問解説動画（例: 令和元年秋期問11）を視聴し、誤答パターンを分析。

#### 具体的な文法
| カテゴリ | 文法例 | 説明・過去問関連 |
|----------|--------|------------------|
| クラス定義・継承 | ```class
| 抽象クラス | ```abstract class Cache { public abstract Block getCachedBlockData(int index); } class Fifo extends Cache { ... }``` | 抽象メソッドのオーバーライド。キャッシュシステムでポリモーフィズムを実装。 |
| 例外処理 | ```try { if (y < 0.0 || y >= 1.0) throw new IllegalArgumentException(); } catch (IndexOutOfBoundsException e) { ... }``` | 引数範囲チェック。縦線追加時のエラー処理。 |
| コレクション操作 | ```lines.add(new HorizontalLine(x1, x2, y)); Collections.sort(lines);``` | List追加とソート。横線管理で頻出。 |
| 文字列処理 | ```String output = input.replace("!", "&amp;"); System.out.println(output);``` | HTMLタグ埋め込み時のエスケープ。英数字出力問題。 |

### ECMAScript（JavaScript）の重点対処項目

ECMAScript関連の問題は、応用情報技術者試験でも一部登場しますが、基本情報ではオブジェクト表現やデータ記述が中心。過去問ではJSON由来の仕様や配列操作が目立ち、軽量データ構造の理解が鍵です。

#### 重点を置く学習内容
- **オブジェクトと配列**: オブジェクトリテラル、連想配列。JSON形式のデータ表現が頻出。
- **関数とプロトタイプ**: 関数宣言、コールバック。値の順序付きリスト操作。
- **データ記述仕様**: JSONの名前-値ペアと配列構造。オブジェクトの多次元表現。
- **文字列・値操作**: スカラ値、真偽値の扱い。コンマ区切りやコロン連結。
- **例外・エラー管理**: 基本的なtry-catch（ES5以降）。データ検証。

#### 具体的な勉強方法
- **過去問演習**: IPA公開問題（平成31年春期問7）でJSON関連を重点的に。fe-siken.comで類似問題を検索・解く。
- **コード実装練習**: Node.jsやブラウザコンソールでオブジェクトを作成・操作。JSON.parse/stringifyをテスト。
- **参考書活用**: 「JavaScript本格入門」でES6文法を学び、1週間でオブジェクト章を完了。MDN Web Docsで公式仕様確認。
- **オンラインリソース**: Udemyの基本情報対策コースでECMAScriptモジュールを視聴。RFC8259（JSON規格）を軽く読み、クイズ形式で復習。

#### 具体的な文法
| カテゴリ | 文法例 | 説明・過去問関連 |
|----------|--------|------------------|
| オブジェクトリテラル | ```let obj = { name1: "value1", name2: [1, 2], name3: { sub: "value" } };``` | 名前-値ペアと配列のネスト。JSON由来のデータ記述。 |
| 配列操作 | ```let list = ["value1", "value2"]; list.push("value3"); console.log(list.join(","));``` | 順序付きリスト。値の追加・連結。 |
| 関数宣言 | ```function processData(data) { return data.name + ": " + data.value; }``` | コールバック使用。データ処理関数。 |
| JSON扱い | ```let jsonStr = '{"key": "value"}'; let parsed = JSON.parse(jsonStr);``` | パースとシリアライズ。オブジェクト表現の標準化。 |
| 例外処理 | ```try { if (!data) throw new Error("Invalid"); } catch (e) { console.log(e.message); }``` | データ検証エラー。値チェック。 |

### 令和8年春予想問題（科目B風・疑似言語ベースだがJava/ECMAScript対応）
令和8年春（2026年4月頃）の科目Bは疑似言語中心ですが、過去傾向からアルゴリズム実装をJava/ECMAScriptで想定。以下は予想問題例（問9相当）。実際の試験は20問中プログラミング関連が複数出題され、データ構造・アルゴリズムが融合。

#### 予想問題: タスクスケジューラの設計（Java版）
**プログラムの説明**: 複数のタスクを優先度に基づきスケジュールするプログラム。タスクはID、優先度（1-10）、実行時間を持つ。優先度が高い順に実行し、同優先度はFIFOで処理。Listを使って管理。

**プログラム（抜粋）**:
```java
import java.util.*;

abstract class TaskScheduler {
    protected List<Task> tasks = new ArrayList<>();
    public abstract void addTask(int id, int priority, int time);
    public abstract void execute();
}

class PriorityScheduler extends TaskScheduler {
    @Override
    public void addTask(int id, int priority, int time) {
        tasks.add(new Task(id, priority, time));
        // ここにソート処理を記述（優先度降順）
    }
    
    @Override
    public void execute() {
        // タスクを実行し、合計時間を計算
        int total = 0;
        for (Task t : tasks) {
            total += t.time;
        }
        return total;
    }
}

class Task {
    int id, priority, time;
    Task(int id, int p, int t) { this.id = id; this.priority = p; this.time = t; }
}
```

**設問1**: addTaskメソッドでタスクを優先度降順にソートするコードを記述せよ。  
**解答例**: `Collections.sort(tasks, (a, b) -> b.priority - a.priority);`

**設問2**: executeで合計実行時間が10未満の場合にIllegalStateExceptionを投げる例外処理を追加せよ。  
**解答例**: `if (total < 10) throw new IllegalStateException("Time insufficient");`

#### 予想問題: JSONデータパーサー（ECMAScript版）
**プログラムの説明**: JSON形式のユーザー情報を解析し、配列から高スコアユーザーを抽出。オブジェクトのネスト構造を扱う。

**プログラム（抜粋）**:
```javascript
let users = [
    { id: 1, name: "Alice", scores: [85, 90] },
    { id: 2, name: "Bob", scores: [70, 75] }
];

function parseHighScores(data) {
    let highUsers = [];
    for (let user of data) {
        let avg = user.scores.reduce((a, b) => a + b) / user.scores.length;
        if (avg > 80) highUsers.push(user);
    }
    return JSON.stringify(highUsers);
}
```

**設問1**: parseHighScoresで平均計算がNaNになる場合のtry-catchを追加せよ。  
**解答例**: 
```javascript
try {
    let avg = user.scores.reduce((a, b) => a + b) / user.scores.length;
    if (isNaN(avg)) throw new Error("Invalid score");
} catch (e) {
    console.log(e.message);
}
```

**設問2**: highUsersをID昇順にソートするコードを記述せよ。  
**解答例**: `highUsers.sort((a, b) => a.id - b.id);`

これらの予想は過去問の傾向（オブジェクト管理、例外、ソート）を基に作成。科目B対策として、疑似言語をJava/ECMAScriptに翻訳する練習を推奨します。