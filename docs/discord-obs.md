# [Discord StreamKit Overlay](discord-obs.md)

- [OBSでDiscordのアイコンを四角や横並びにするジェネレーター](https://blog.alfebelow.com/entry/2022/03/20/obs-discord-icon)
- [Discord StreamKit Overlay](https://streamkit.discord.com/overlay)
- [OBSのDiscordアイコン外観変更ジェネレーター](https://obs-discord-icon.alfebelow.com/)

## Parameters

### [Discord StreamKit Overlay](https://streamkit.discord.com/overlay)

- Show Speaking Users Only: false
- Small Avatars: true
- Hide Names: true
- Show My Avatar First: false
- Text Color:
    - Text Color: #ffffff
    - Text Size: 14px
    - Text Outline Color: #000000
    - Text Outline Size: 0px
    - Shadow Color: #000000
    - Shadow Size: 0px
- BACKGROUND SETTINGS:
    - Background Color: #1e2124
    - Opacity: 95%
    - Shadow Color: #000000
    - Shadow Size: 0px

### [OBSのDiscordアイコン外観変更ジェネレーター](https://obs-discord-icon.alfebelow.com/)

- アイコンの並び: 横並び
- アイコンの間隔（上下）: 0
- アイコンの間隔（左右）: 0
- アイコンの形: 丸
- アイコンの大きさ: 標準
- 話すときの動き: 
    - 縁取り: true
    - 点滅: false
    - ぴょこぴょこ: true
- 動きの速さ: 80
- 色: #ffffff
- 名前: false
- 特定のユーザを隠す:

### Discord

- ローカルファイル: false
- 幅: 900
- 高さ: 200
- OBSで音声を制御する: false
- カスタムフレームレートを使用する: false
- 表示されていないときにソースをシャットダウンする: true
- シーンがアクティブになったときにブラウザの表示を更新する: true
- ページ権限: OBSのステータス情報へのアクセス

----------

## 導入方法

1. OBSのソースにブラウザを追加
OBSを起動、OBSのシーンを選択後、「ソース」欄で右クリックしてブラウザを追加

2. Discord を起動

3. [Discord StreamKit Overlay](https://streamkit.discord.com/overlay) にアクセス
[Discord StreamKit Overlay](https://streamkit.discord.com/overlay)

4. ボイスウィジェットのURLを取得
`Install for OBS` をクリックし、 `VOICE WIDGET` のタブを選択
`Server` と `Voice Channel`からボイスチャンネルを選択
右下に表示されるURLをコピー

5. OBSにURLを入力
OBSに戻り、中央にあるURLの入力欄に `4.` でコピーしたURLを貼り付け

6. カスタムCSSを作成
[OBSのDiscordアイコン外観変更ジェネレーター](https://obs-discord-icon.alfebelow.com/) で好みの見た目を決めたあと、下に表示されるCSSをコピー

7. OBSにカスタムCSSを入力
OBSに戻り、URLの少し下にあるカスタムCSSの入力欄に `6.` でコピーしたカスタムCSSを貼り付け

8. 作成完了
ダイアログをOKで閉じて完了。OBSに話している人が表示されます。

----------

## サンプル

<details>

<summary>Tips for collapsed sections</summary>

```css
[class*="Voice_voiceStates__"] {
  display: flex;
  flex-wrap: wrap;
  margin: 32px;
} 
[class*="Voice_voiceState__"] {
  height: auto;
  margin-bottom: 0;
  display: flex;
  flex-direction: column;
} 
[class*="Voice_avatar__"] {
  filter: brightness(70%);
  margin-right: 0;
} 
[class*="Voice_avatarSpeaking__"] {
  position: relative;
  filter: brightness(100%);
  border-color: #FFFFFF;
  animation: 750ms infinite alternate ease-in-out speak-jump;
  z-index: 1;
  animation-duration: 351ms;
} 
[class*="Voice_name__"] {
  left: 0px;
  position: relative;
  max-width: 56px;
  box-sizing: border-box;
  text-overflow: clip;
  white-space: nowrap;
  overflow: hidden;
  display: block;
  text-align: center;
  z-index: 2;
} 
[class*="Voice_user__"] {
  padding-top: 0px;
}
[src*="avatars/533698325203910668/"], [src*="avatars/533698325203910668/"] + [class*="Voice_user_"]  {
  /* shovel blue */
  display: none;
}
[src*="avatars/600611976024162304/"], [src*="avatars/600611976024162304/"] + [class*="Voice_user_"]  {
  /* shovel green */
  display: none;
}
[src*="avatars/600611680711606284/"], [src*="avatars/600611680711606284/"] + [class*="Voice_user_"]  {
  /* shovel red */
  display: none;
}

@keyframes speak-jump {
  0% {
    bottom: 0px;
  }
  50% {
    bottom: 10px;
  }
  100% {
    bottom: 0px;
  }
}
@keyframes speak-border {
  0% {
    filter: drop-shadow(2px 2px 0px #FFFFFF) drop-shadow(-2px -2px 0px #FFFFFF) drop-shadow(-2px 2px 0px #FFFFFF) drop-shadow(2px -2px 0px #FFFFFF);
  }
  50% {
    filter: drop-shadow(2px 2px 0px #FFFFFF) drop-shadow(-2px -2px 0px #FFFFFF) drop-shadow(-2px 2px 0px #FFFFFF) drop-shadow(2px -2px 0px #FFFFFF);
  }
  100% {
    filter: drop-shadow(2px 2px 0px #FFFFFF) drop-shadow(-2px -2px 0px #FFFFFF) drop-shadow(-2px 2px 0px #FFFFFF) drop-shadow(2px -2px 0px #FFFFFF);
  }
}
```

</details>
