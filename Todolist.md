# TODOリスト作成



```dart
import 'package:flutter/material.dart';

void main() => runApp(TodoApp());
```
- アプリの起動関数
- `TodoAPP`というウィジェットを起動
## TodoAppクラス（アプリの基本設定）

```dart
class TodoApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'TODO App',
      theme: ThemeData(primarySwatch: Colors.blue),
      home: TodoHomePage(),
    );
  }
}
```
- `MaterialApp`を使ってテーマの色、タイトル、最初に表示するページの定義
- 最初の画面は`TodoHomePage()`を指定

## TodoItemクラス
```dart
class TodoItem {
  String title;
  bool isDone;

  TodoItem({required this.title, this.isDone = false});
}
```
- タスクの１つを表現するクラス
- `title`：タスクの内容
- `isDone`:完了済みかどうか

## TodoHomePage(メイン画面のウィジェット)
```dart
class TodoHomePage extends StatefulWidget {
  @override
  _TodoHomePageState createState() => _TodoHomePageState();
}
```
## _TodoHomePageState（状態管理）
```dart
class _TodoHomePageState extends State<TodoHomePage> {
  final List<TodoItem> _todos = [];
  final TextEditingController _controller = TextEditingController();
```
- `_todos`:タスクのリストを格納
- `_controller`:テキスト入力用コントローラー

## タスクの追加関数
```dart
  void _addTask() {
    String text = _controller.text.trim();
    if (text.isNotEmpty) {
      setState(() {
        _todos.add(TodoItem(title: text));
        _controller.clear();
      });
    }
  }
  ```
  - テキストが空でなければ新しいタスクを追加
  - `setState()`によってUIを更新
  ## タスクの状態切り替え関数
  ```dart
  void _toggleTask(int index) {
    setState(() {
      _todos[index].isDone = !_todos[index].isDone;
    });
  }
```
- チェックボックスのON/OFFに応じて、`isDone`の値を切り替える
- `setState()`によりUIを反映させる

## UIの構築
```dart
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('TODO List')),
      body: Column(
        children: [
          Padding(
            padding: const EdgeInsets.all(12.0),
            child: Row(
              children: [
                Expanded(
                  child: TextField(
                    controller: _controller,
                    decoration: InputDecoration(labelText: '新しいタスクを追加'),
                  ),
                ),
                IconButton(icon: Icon(Icons.add), onPressed: _addTask),
              ],
            ),
          ),
          Expanded(
            child: ListView.builder(
              itemCount: _todos.length,
              itemBuilder: (context, index) {
                final todo = _todos[index];
                return ListTile(
                  leading: Checkbox(
                    value: todo.isDone,
                    onChanged: (_) => _toggleTask(index),
                  ),
                  title: Text(
                    todo.title,
                    style: TextStyle(
                      decoration:
                          todo.isDone ? TextDecoration.lineThrough : null,
                    ),
                  ),
                );
              },
            ),
          ),
        ],
      ),
    );
  }
}
```
| 要素                           | 説明                            |
| ---------------------------- | ----------------------------- |
| `Scaffold`                   | 画面全体のレイアウトを構成する基本部品           |
| `AppBar`                     | タイトルバー部分（TODO List）           |
| `TextField`                  | タスクを入力するテキストフォーム              |
| `IconButton`                 | ＋ボタン。押すと `_addTask()` が呼び出される |
| `ListView.builder`           | タスクをリスト表示するスクロール可能なリスト        |
| `Checkbox`                   | タスクが完了しているかを視覚的に表す            |
| `TextDecoration.lineThrough` | タスク完了時に文字に打ち消し線を表示する          |
