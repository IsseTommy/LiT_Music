# 音楽アプリ
***
## １、押さえておくポイント、Swift言語特性
### ボタンの背景を画像にしたい時
1. 背景を画像に変えたいボタンを選択し、右側のタブの下矢印を選ぶ。  
1. Backgroundから背景にしたい画像を選択する。 　

---

### 音楽を流したい場合
1. まずViewController.swiftの一番上のimport UIKitの下に以下のコードを入力する。  
  このコードは音声を再生するためのライブラリ（補助ツールのようなもの）を取り込んでいる。
```
import AVFoundation
```
1. ViewDidLoad()の上に以下のコードを入力する。
  このコードはプレイヤーを準備している。
```
var audioPlayer : AVAudioPlayer!
```

1. プレイヤー準備をする為に以下のメゾットを作る
```
func setAudioPlayer(soundName: String, type: String) {
        let soundFilePath = Bundle.main.path(forResource: soundName, ofType: type)!
        let fileURL = URL(fileURLWithPath: soundFilePath)
        
        do {
            audioPlayer = try AVAudioPlayer(contentsOf: fileURL)
        } catch {
            print("音楽ファイルが読み取れませんでした")
        }
}
```
1. ボタンがタップされた時などに以下のようにオーディオプレイヤーを呼び出す
```
setAudioPlayer(soundName: "再生したいファイルの名前", type: "再生したいファイルの拡張子")
        audioPlayer.play()
```
___

## ２、エラー

### ビルドしようとするとファイルが見つからないと言われる
#### 原因

ファイルをインポートするときに「Create groups」ではなく「Create folder references」を選んでいた  
左端のタブのフォルダーが青色で表示されていたら間違えている証拠  

### 音楽が再生されない
#### 原因
ボタンの関連付け忘れ
