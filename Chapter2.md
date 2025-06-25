# Chapter2

### プロジェクトのフォルダ構成

| フォルダ名             | 説明                                                                 |
|------------------------|----------------------------------------------------------------------|
| `.dart_tool`フォルダ   | Dart関連の自動生成ファイル類を保管するところ。                     |
| `.idea`フォルダ        | IntelliJ IDEA開発ツールの設定情報。                                 |
| `build`フォルダ        | ビルドして生成されたファイル類。                                     |
| `android`フォルダ      | Androidアプリ生成に必要なファイル類（プラットフォームにAndroidを選択した場合）。|
| `ios`フォルダ          | iOSアプリ生成に必要なファイル類（プラットフォームにiOSを選択した場合）。     |
| `linux`フォルダ        | Linuxアプリ生成に必要なファイル類（プラットフォームにLinuxを選択した場合）。 |
| `macos`フォルダ        | macOSアプリ生成に必要なファイル類（プラットフォームにmacOSを選択した場合）。|
| `windows`フォルダ      | Windowsアプリ生成に必要なファイル類（プラットフォームにWindowsを選択した場合）。|
| `web`フォルダ          | Webアプリ生成に必要なファイル類（プラットフォームにWebを選択した場合）。     |
| `lib`フォルダ          | Dartのスクリプトが保存される。                                     |
| `test`フォルダ         | ユニットテスト関連のファイル類。                                    |

---

### プロジェクトのファイル類

| ファイル名                 | 説明                                                       |
|----------------------------|------------------------------------------------------------|
| `.gitignore`               | Gitで利用するファイル。                                     |
| `.metadata`                | Flutterツールが利用するファイル。                          |
| `.packages`                | 利用しているパッケージ情報。                               |
| `analysis_options.yaml`    | Dartの分析に関するファイル。                               |
| `flutter_app.iml`          | モジュール定義ファイル。                                   |
| `pubspec.lock`             | Pub（Dartのパッケージマネージャ）が利用するファイル。       |
| `pubspec.yaml`             | Pubが利用するファイル。                                     |
| `README.md`             | リードミーファイル。                                     |

## アプリの構造
1. アプリケーションはmain関数として定義する。このmain関数では、runAppでウィジェットのインスタンスを実行する
2. runApp関数では、StatelessWidget継承クラスのインスタンスを引数に指定する。（これがアプリ本体のUIになる。）
3. StatelessWidgetr継承クラスにはbuildメソッドを用意する。ここでマテリアルデザインのアプリクラスであるMaterialAppインスタンスをreturnする。
4. MaterialAppの引数homeに、実際にアプリ内に表示するウィジェットを設定する。

## StatefulWidgetクラスの基本形
```dart
class ウィジェットクラス extends StatefulWidget {
  
  @override
  ステートクラス　createState() ⇒ ステートクラス();
}
```
## Stateクラスの基本形
```dart
class ウィジェットクラス extends State<ウィジェットクラス>{

  ---略---
  
  @override
  Widget build(BuildContext context){

  ---略---

  }
}
```