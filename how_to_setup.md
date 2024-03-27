[チュートリアル元](https://zenn.dev/kumassy/books/6e518fe09a86b2)

0. 下準備 [参考](https://tauri.app/v1/guides/getting-started/prerequisites)

- Windows  
  scoopを入れる (https://scoop.sh/)  
  ↓ 変更されてる可能性があるので公式ページを参照すること  
  また管理者権限のpowershellで実行するとエラーになるので注意 (https://shigeo-t.hatenablog.com/entry/2022/06/13/050000)
    ```
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
    Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression
    ```

- Mac  
  brewからrustupを入れる (https://zenn.dev/coco655/articles/rust_install)
  公式ではcurlで入れているが、brewにもあるみたいなのでそちらからインストール
    ```
    brew install rustup-init

    # インストールできたら初期化
    rustup-init
    ```

---

1.

Tauriに必要なものをインストール [参考](https://zenn.dev/suauiya/books/ef2d2c67c546361e4518/viewer/f25ab0480c5e6ec794e4)

```
choco install visualstudio2022buildtools
choco install visualstudio2022-workload-vctools

choco install nodejs
# 既にインストール済みの場合、バージョンが古いとエラーとなるため
# 念のため`choco update nodejs`しておく(https://github.com/vitejs/vite/issues/14299)
```

[参考](https://qiita.com/dozo/items/378452a0c3585f0756dc)

```
scoop install rustup

rustup self update
rustup update
rustup install stable
```

---

2. Tauriプロジェクトの作成 [参考](https://zenn.dev/kumassy/books/6e518fe09a86b2/viewer/521d6b)

```
cd "プロジェクトフォルダを作成したい階層まで移動しておく"

# Tauriプロジェクト作成 **初回のみ**
npm create tauri-app@latest

# 必要なnode moduleをプロジェクトフォルダにインストール **cloneしてきた際も必要**
npm install --save-dev @tauri-apps/cli

# 作成するアプリ情報を設定 **初回のみ**
npm run tauri init

# コマンドライン上で実行
npm run tauri dev
```

---

3. RustRoverの設定 [参考](https://tauri.app/v1/guides/debugging/rustrover/)

---

4. その他

- 実行時のアプリのブラウザデバッグ表示について [参考](https://tauri.app/v1/guides/debugging/application/)
    - アプリウィンドウを右クリック > Inspect Element より開く (mac: ⌘ + ⌥ + i, win: ctrl + shift + i)
    - デバッグメニュー左側アイコンにドッキングを解除するボタンがある