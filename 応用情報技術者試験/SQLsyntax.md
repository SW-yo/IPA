

以下に、1から13のSQL文法をマークダウン形式で列挙します。


---


### 1. 基本SQL文法 
 
- **SELECT文** 
データの選択や取得

```sql
SELECT column_name FROM table_name;
```
 
- **WHERE句** 
条件を指定してデータを絞り込む

```sql
SELECT column_name FROM table_name WHERE condition;
```
 
- **ORDER BY句** 
データの並び替え

```sql
SELECT column_name FROM table_name ORDER BY column_name [ASC|DESC];
```
 
- **GROUP BY句** 
集約関数と共にデータをグループ化

```sql
SELECT column_name, COUNT(*) FROM table_name GROUP BY column_name;
```
 
- **HAVING句** 
グループ化後のデータに条件を設定

```sql
SELECT column_name, COUNT(*) FROM table_name GROUP BY column_name HAVING condition;
```
 
- **JOIN句** 
テーブルの結合（内結合、外結合、自然結合など）

```sql
SELECT column_name FROM table1 INNER JOIN table2 ON table1.column_name = table2.column_name;
```


---


### 2. 高度なSQL文法 
 
- **サブクエリ** 
クエリの中にクエリを含める

```sql
SELECT column_name FROM table_name WHERE column_name IN (SELECT column_name FROM table_name2);
```
 
- **UNION** 
複数のSELECT結果を結合

```sql
SELECT column_name FROM table_name1 UNION SELECT column_name FROM table_name2;
```
 
- **INSERT文** 
データの挿入

```sql
INSERT INTO table_name (column1, column2) VALUES (value1, value2);
```
 
- **UPDATE文** 
データの更新

```sql
UPDATE table_name SET column_name = new_value WHERE condition;
```
 
- **DELETE文** 
データの削除

```sql
DELETE FROM table_name WHERE condition;
```


---


### 3. 集約関数 
 
- **COUNT()** 
行数のカウント

```sql
SELECT COUNT(*) FROM table_name;
```
 
- **SUM()** 
数値の合計

```sql
SELECT SUM(column_name) FROM table_name;
```
 
- **AVG()** 
平均値の取得

```sql
SELECT AVG(column_name) FROM table_name;
```
 
- **MAX()** 
最大値の取得

```sql
SELECT MAX(column_name) FROM table_name;
```
 
- **MIN()** 
最小値の取得

```sql
SELECT MIN(column_name) FROM table_name;
```


---


### 4. その他の文法 
 
- **DISTINCT** 
重複行の除去

```sql
SELECT DISTINCT column_name FROM table_name;
```
 
- **LIMIT句（またはFETCH句）** 
取得する行数を制限

```sql
SELECT column_name FROM table_name LIMIT 10;
```
 
- **CASE文** 
条件による値の切り替え

```sql
SELECT column_name, CASE WHEN condition1 THEN result1 WHEN condition2 THEN result2 ELSE result3 END FROM table_name;
```
 
- **EXISTS句** 
特定のサブクエリの結果が存在するかどうかを確認

```sql
SELECT column_name FROM table_name WHERE EXISTS (SELECT 1 FROM table_name2 WHERE condition);
```


---


### 5. テーブルの変更・制約に関するSQL文法 
 
- **ALTER TABLE文** 
既存のテーブル構造を変更**列の追加** :

```sql
ALTER TABLE table_name ADD column_name datatype;
```
**列の削除** :

```sql
ALTER TABLE table_name DROP COLUMN column_name;
```
**列のデータ型の変更** :

```sql
ALTER TABLE table_name MODIFY column_name new_datatype;
```
 
- **UNIQUE制約** 
列に重複する値が存在しないことを保証**UNIQUE制約の追加** :

```sql
ALTER TABLE table_name ADD CONSTRAINT constraint_name UNIQUE (column_name);
```
**テーブル作成時にUNIQUE制約を指定** :

```sql
CREATE TABLE table_name (
  column_name datatype UNIQUE
);
```
 
- **PRIMARY KEY制約** 
列が一意であり、NULLを許さない**PRIMARY KEYの追加** :

```sql
ALTER TABLE table_name ADD PRIMARY KEY (column_name);
```
 
- **FOREIGN KEY（外部キー制約）** 
他のテーブルのキーを参照**FOREIGN KEYの追加** :

```sql
ALTER TABLE table_name ADD CONSTRAINT constraint_name FOREIGN KEY (column_name) REFERENCES other_table(other_column);
```
 
- **CHECK制約** 
値が指定した条件を満たしていることを保証

```sql
ALTER TABLE table_name ADD CONSTRAINT constraint_name CHECK (condition);
```


---


### 6. その他の制約に関するSQL文法 
 
- **DEFAULT制約** 
列にデフォルトの値を設定

```sql
ALTER TABLE table_name ALTER COLUMN column_name SET DEFAULT default_value;
```
 
- **NOT NULL制約** 
NULLを許可しない制約

```sql
ALTER TABLE table_name MODIFY column_name datatype NOT NULL;
```


---


### 7. ビューに関するSQL文法 
 
- **ビューの作成** 
仮想テーブル（ビュー）の作成

```sql
CREATE VIEW view_name AS SELECT column_name FROM table_name WHERE condition;
```
 
- **ビューの削除** 
既存のビューを削除

```sql
DROP VIEW view_name;
```


---


### 8. インデックスに関するSQL文法 
 
- **インデックスの作成** 
インデックスを作成し、検索パフォーマンスを向上

```sql
CREATE INDEX index_name ON table_name (column_name);
```
 
- **ユニークインデックスの作成** 
一意性を持つインデックスを作成

```sql
CREATE UNIQUE INDEX index_name ON table_name (column_name);
```
 
- **インデックスの削除** 
インデックスを削除

```sql
DROP INDEX index_name;
```


---


### 9. トランザクション制御に関するSQL文法 
 
- **BEGIN TRANSACTION** 
トランザクションの開始

```sql
BEGIN TRANSACTION;
```
 
- **COMMIT** 
トランザクションで行った変更を確定

```sql
COMMIT;
```
 
- **ROLLBACK** 
トランザクションを取り消す

```sql
ROLLBACK;
```
 
- **SAVEPOINT** 
セーブポイントを作成し、部分的なロールバックが可能

```sql
SAVEPOINT savepoint_name;
```
 
- **SET TRANSACTION** 
トランザクションの分離レベルを設定

```sql
SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;
```


---


### 10. 高度なクエリ・制約 
 
- **FULL OUTER JOIN** 
両方のテーブルから一致しない行を含む結合

```sql
SELECT column_name FROM table1 FULL OUTER JOIN table2 ON table1.column_name = table2.column_name;
```
 
- **SELF JOIN** 
同じテーブルを自分自身と結合

```sql
SELECT a.column_name, b.column_name FROM table_name a, table_name b WHERE a.some_column = b.some_column;
```
 
- **COALESCE** 
NULLでない最初の値を返す

```sql
SELECT COALESCE(column_name, default_value) FROM table_name;
```
 
- **NULLIF** 
2つの値が等しい場合にNULLを返す

```sql
SELECT NULLIF(column1, column2) FROM table_name;
```


---


### 11. カーソルに関する文法 
 
- **DECLARE CURSOR** 
カーソルを宣言し、データを一行ずつ処理

```sql
DECLARE cursor_name CURSOR FOR SELECT column_name FROM table_name;
```
 
- **FETCH** 
カーソルから次の行を取得

```sql
FETCH NEXT FROM cursor_name;
```
 
- **CLOSE** 
カーソルを閉じる

```sql
CLOSE cursor_name;
```
 
- **DEALLOCATE** 
カーソルのリソースを解放

```sql
DEALLOCATE cursor_name;
```


---


### 12. ストアドプロシージャやトリガーに関する文法 
 
- **ストアドプロシージャの作成** 
複数のSQL文をまとめて実行

```sql
CREATE PROCEDURE procedure_name AS BEGIN SQL_statements END;
```
 
- **ストアドプロシージャの実行** 
ストアドプロシージャを実行

```sql
EXEC procedure_name;
```
 
- **トリガーの作成** 
特定のイベント時に自動実行されるトリガーを定義

```sql
CREATE TRIGGER trigger_name BEFORE INSERT ON table_name FOR EACH ROW BEGIN SQL_statements END;
```


---


### 13. WITH句（共通表式: CTE） 
 
- **WITH句** 
複雑なクエリを簡潔にし、再利用可能な仮想的なサブクエリを定義

```sql
WITH cte_name AS (SELECT column_name FROM table_name WHERE condition) SELECT * FROM cte_name;
```


---


以上が、1から13までのSQL文法のマークダウン形式です。