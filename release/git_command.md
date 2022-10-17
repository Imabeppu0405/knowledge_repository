# ブランチを切り戻すコマンドまとめ

## reset
文字通りリセットする方法。履歴が消去される。
- pull前までの戻し
```
git reflog
git reset --hard HEAD@{1} // 戻したいHEAD
```

- 特定のコミットまでの戻し
```
git log
git reset --hard コミットID
```

- 備考
    - --hard ：add、commit、ワーキングツリーの取り消し
    - --soft：commitのみ取り消し。
    - --mixed：commitとaddの取り消し。


## revert
変更を打ち消すコミットを作成する。こちらのほうがresetよりも安全(履歴を改ざんしないため)

- 特定のコミットの戻し
```
git log
git revert コミットID
```
- 直前のコミットの戻し
```
git revert HEAD 
```
- マージコミットの戻し
```
git revert -m 1 コミットiD
```
- 複数のコミットの戻し
```
git revert HEAD...HEAD~3
git rebase -i HEAD~3 // コミットをまとめる
```
