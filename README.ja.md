# senpai 🎓

[English](./README.md) | **日本語**

**コードはエージェントが書く。学びはあなたに残る。**

エージェントが書くコードは日々増えています。リリースは速くなったのに、自分の理解は浅くなった気がする。そんな感覚を持つエンジニアは少なくありません。

senpai は Claude Code と Codex 向けのskillで、エージェントを隣の席の先輩エンジニアに変えます。作業の速さはそのままです。変更のたびに、あなたのレベルの一歩先にある部分だけを手渡してくれます。

## 使うとこうなる

あなたはミドルレベルを目指しているとします。遅いページの高速化を頼むと、エージェントは変更を書きますが、小さな穴を1つだけ残します。

```python
def list_orders(db):
    orders = db.query("SELECT * FROM orders")
    # TODO(senpai): implement this — mid-level must-know
    # Load the customers for all orders in one query, not one per order.
    # Hint: look up "N+1 query problem".
    raise NotImplementedError
```

```
🎓 Senpai [mid-level must-know]
注文ごとに顧客を1件ずつ読むと、注文が100件なら101回クエリが走ります。
src/orders.py:4 を埋めたら教えてください。レビューします。
```

穴を埋めると、senpai がレビューします。`you do it` と言えば、senpai が自分で埋めて先に進みます。

## はしご

senpai は、変更に含まれる考え方ごとに、それを知っているべきキャリアのレベルを付けます。

| レベル | 知っておくべきことの例 |
| --- | --- |
| junior | off-by-one、null や空の入力の扱い、エラーメッセージの読み方 |
| mid | N+1 クエリ、インデックス、キャッシュ、テストで何をモックするか |
| senior | 競合状態、冪等性、リトライとタイムアウト、安全なマイグレーション |
| staff | API の後方互換性、一貫性と可用性のトレードオフ、保守にかかるコスト |

そのうえで、あなたのレベルとの関係で扱いを変えます。

| その考え方が | senpai の動き |
| --- | --- |
| あなたのレベルより下 | 黙って書く（もう知っているはず） |
| あなたのレベルちょうど | 1〜5行の穴を残して、あなたに書いてもらう |
| あなたのレベルより上 | 自分で書いて、3文で解説する |

穴への答えに直しがほとんど要らない状態が何回か続くと、senpai は次のレベルに上がることを提案します。勝手にレベルを変えることはありません。レベルは `~/.senpai/level` に保存されます。

## インストール

### Claude Code

```
/plugin marketplace add 6igtree/senpai
/plugin install senpai@senpai
```

### Codex

```sh
git clone https://github.com/6igtree/senpai.git /tmp/senpai
mkdir -p ~/.agents/skills && cp -r /tmp/senpai/skills/senpai ~/.agents/skills/
```

## 使い方

`senpai`（Claude Code では `/senpai` でも可）と言うと始まります。初回だけ、どのレベルを目指しているかを聞かれます。`senpai junior`、`senpai mid`、`senpai senior`、`senpai staff` でいつでも切り替えられ、`stop senpai` で止まります。

## しないこと

- 危ない場所には穴を空けない：認証や決済、削除、壊れるおそれのあるマイグレーションは、必ずエージェントが書きます。その代わり、解説で教えます。
- 穴は1回に1つまで：作業が止まらないようにするためです。
- 障害対応中は黙る：`just do it` と言えば、次の落ち着いた作業まで何も言いません。
- 作業は遅くしない：教えやすくするために、作業そのものの質を落とすことはしません。

## 関連

[nit](https://github.com/6igtree/nit)：エージェントが英語で話す同僚になります。コードを書きながら、仕事の英語を練習できます。

## ライセンス

MIT
