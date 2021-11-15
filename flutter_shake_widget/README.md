## Features

This widget is used to animate a widget with a shake animation. There are a lot of 
customisable fields : 
- The widget being animated
- The number of times it shakes
- The shake offset
- The animation duration

## Usage

There is a little example of the usage of this widget.

```dart
return ShakeWidget (
  key: _shakeWidget,
  child: ...,         // Required field
  shakeOffset = 6,    // Required field
  shakeCount = 3,
  shakeDuration = const Duration(milliseconds: 400),
)
```
You can use a `GlobalKey` to trigger easily one ShakeWidget if you have several ShakeWidget in the same file.

```dart
class Test extends StatefulWidget {
  const Test({Key? key}) : super(key: key);

  @override
  State<Test> createState() => _TestState();
}

class _TestState extends State<Test> {
  final _firstContainer = GlobalKey<ShakeWidgetState>();
  final _secondContainer = GlobalKey<ShakeWidgetState>();
  
  void onFirstPressed() {
    _firstContainer.currentState?.shake();
  }

  void onSecondPressed() {
    _secondContainer.currentState?.shake();
  }
  
  @override
  Widget build(BuildContext context) {
    return Center(
      child: Column(
        children: [
          ShakeWidget(
            key: _firstContainer,
            shakeCount: 3,
            shakeOffset: 6,
            shakeDuration: const Duration(milliseconds: 400),
            child: Container(
              width: 50,
              height: 50,
              color: Colors.red,
            )
          ),
          ShakeWidget(
              key: _secondContainer,
              shakeCount: 5,
              shakeOffset: 10,
              shakeDuration: const Duration(milliseconds: 1000),
              child: Container(
                width: 70,
                height: 70,
                color: Colors.blue,
              )
          ),
          ElevatedButton(onPressed: onFirstPressed, child: const Text("First")),
          ElevatedButton(onPressed: onSecondPressed, child: const Text("Second")),
        ],
      ),
    );
  }
}
```

