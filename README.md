# Node-VOICEVOX-Engine

![GitHub](https://img.shields.io/github/license/y-chan/node-voicevox-engine)
![npm](https://img.shields.io/npm/v/node-voicevox-engine)

## 本ライブラリについて
本ライブラリは[ヒホ氏](https://github.com/Hiroshiba)によって制作・公開されている、
[VOICEVOX Engine](https://github.com/VOICEVOX/voicevox_engine)の**非公式**Node.js版、兼
[VOICEVOX Core](https://github.com/VOICEVOX/voicevox_core)のラッパーライブラリです。

## 使用にあたって
本ライブラリの使用にあたっては、利用者自身が[VOICEVOX Core公開のサイト](https://github.com/VOICEVOX/voicevox_core/releases/latest)より、
VOICEVOX Coreライブラリをダウンロードし、そのライブラリのパスを指定しなければなりません。
加えて[ONNX Runtime](https://github.com/microsoft/onnxruntime/releases/tag/v1.10.0)も必要です。
(Raspberry Pi等を用いる場合、[VOICEVOX公式が公開するarm64/armhf向けビルド](https://github.com/VOICEVOX/onnxruntime-builder/releases/tag/1.10.0.1)をご利用ください。)
本ライブラリのみで完結はしませんのでご注意ください。
なお、CPU版を利用する場合はCUDA/CUDNNは必要ありません。

なお、製品版VOICEVOXの`core.dll`/`libcore.so`/`libcore.dylib`を指定することで、複雑なインストール処理を省略することも可能です。
この場合、環境変数の`Path`(Windowsの場合)に製品版VOICEVOXのディレクトリを追加しておく必要があります。

## ドキュメント
準備中(現状はコード内に含まれるJSDocをご利用ください)

## 音声合成エンジンとしての利用
本ライブラリはVOICEVOXの音声合成エンジンとして利用可能です。
[`api.ts`内の`core.dll`となっている部分](https://github.com/y-chan/node-voicevox-engine/blob/main/api.ts#L30)をフルパスに変更し、以下のようなコマンドをご利用ください。
なお、音声ライブラリファイル群が`core.dll`/`libcore.so`/`libcore.dylib`と同じディレクトリ階層にある前提です。
```bash
# ビルドと依存関係・OpenJTalk辞書のダウンロード
# npm なら npm install
yarn install
# 実行する。npm なら npm start
# onnxruntimeの存在する場所によってパスを適切に変更してください
# Macの場合はDYDL_LIBRARY_PATH
LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/onnxruntime/lib/" yarn start
```


## ライブラリとしての使用例
[example](example/index.ts)をご覧ください。
なお、実行する際は[`example.ts`内の`core.dll`となっている部分](https://github.com/y-chan/node-voicevox-engine/blob/main/example/index.ts#L5)をフルパスに変更し、以下のようなコマンドをご利用ください。
なお、音声ライブラリファイル群が`core.dll`/`libcore.so`/`libcore.dylib`と同じディレクトリ階層にある前提です。
```bash
# ビルドと依存関係・OpenJTalk辞書のダウンロード
# npm なら npm install
yarn inatall
# 実行する。npm なら npm run example
# onnxruntimeの存在する場所によってパスを適切に変更してください
# Macの場合はDYDL_LIBRARY_PATH
LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/onnxruntime/lib/" yarn example
```

## ライセンス
本ライブラリは、[本家VOICEVOX Engine](https://github.com/VOICEVOX/voicevox_engine)のライセンスを継承し、
[LGPL-3.0](LICENSE)でライセンスされています。
