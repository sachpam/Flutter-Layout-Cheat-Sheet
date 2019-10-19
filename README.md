# Flutter-Layout-Cheat-Sheet
This repo includes identified Flutter Layouts which anyone can refer as their layout cheat sheet.

# AnimatedBuilder  class

A general-purpose widget for building animations.

## Performance optimizations

If your  [builder](https://api.flutter.dev/flutter/widgets/AnimatedBuilder/builder.html)  function contains a subtree that does not depend on the animation, it's more efficient to build that subtree once instead of rebuilding it on every animation tick.

If you pass the pre-built subtree as the  [child](https://api.flutter.dev/flutter/widgets/AnimatedBuilder/child.html)  parameter, the AnimatedBuilder will pass it back to your builder function so that you can incorporate it into your build.

Using this pre-built child is entirely optional, but can improve performance significantly in some cases and is therefore a good practice.

[_link_](https://api.flutter.dev/flutter/# "Copy link to clipboard")

Sample

This code defines a widget called  `Spinner`  that spins a green square continually. It is built with an  [AnimatedBuilder](https://api.flutter.dev/flutter/widgets/AnimatedBuilder-class.html)  and makes use of the  [child](https://api.flutter.dev/flutter/widgets/AnimatedBuilder/child.html)  feature to avoid having to rebuild the  [Container](https://api.flutter.dev/flutter/widgets/Container-class.html)  each time.

_assignment_

```dart
class Spinner extends StatefulWidget {
  @override
  _SpinnerState createState() => _SpinnerState();
}

class _SpinnerState extends State<Spinner> with SingleTickerProviderStateMixin {
  AnimationController _controller;

  @override
  void initState() {
    super.initState();
    _controller = AnimationController(
      duration: const Duration(seconds: 10),
      vsync: this,
    )..repeat();
  }

  @override
  void dispose() {
    _controller.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return AnimatedBuilder(
      animation: _controller,
      child: Container(width: 200.0, height: 200.0, color: Colors.green),
      builder: (BuildContext context, Widget child) {
        return Transform.rotate(
          angle: _controller.value * 2.0 * math.pi,
          child: child,
        );
      },
    );
  }
}
```

Inheritance

-   [Object](https://api.flutter.dev/flutter/dart-core/Object-class.html)
-   [Diagnosticable](https://api.flutter.dev/flutter/foundation/Diagnosticable-class.html)
-   [DiagnosticableTree](https://api.flutter.dev/flutter/foundation/DiagnosticableTree-class.html)
-   [Widget](https://api.flutter.dev/flutter/widgets/Widget-class.html)
-   [StatefulWidget](https://api.flutter.dev/flutter/widgets/StatefulWidget-class.html)
-   [AnimatedWidget](https://api.flutter.dev/flutter/widgets/AnimatedWidget-class.html)
-   AnimatedBuilder

## Constructors

[AnimatedBuilder](https://api.flutter.dev/flutter/widgets/AnimatedBuilder/AnimatedBuilder.html)({[Key](https://api.flutter.dev/flutter/foundation/Key-class.html)  key, @required  [Listenable](https://api.flutter.dev/flutter/foundation/Listenable-class.html)  animation, @required  [TransitionBuilder](https://api.flutter.dev/flutter/widgets/TransitionBuilder.html)  builder, [Widget](https://api.flutter.dev/flutter/widgets/Widget-class.html)  child  })

Creates an animated builder.  [[...]](https://api.flutter.dev/flutter/widgets/AnimatedBuilder/AnimatedBuilder.html)

const

## Properties

[builder](https://api.flutter.dev/flutter/widgets/AnimatedBuilder/builder.html)  →  [TransitionBuilder](https://api.flutter.dev/flutter/widgets/TransitionBuilder.html)

Called every time the animation changes value.

final

[child](https://api.flutter.dev/flutter/widgets/AnimatedBuilder/child.html)  →  [Widget](https://api.flutter.dev/flutter/widgets/Widget-class.html)

The child widget to pass to the  [builder](https://api.flutter.dev/flutter/widgets/AnimatedBuilder/builder.html).  [[...]](https://api.flutter.dev/flutter/widgets/AnimatedBuilder/child.html)

final

[hashCode](https://api.flutter.dev/flutter/dart-core/Object/hashCode.html)  →  [int](https://api.flutter.dev/flutter/dart-core/int-class.html)

The hash code for this object.  [[...]](https://api.flutter.dev/flutter/dart-core/Object/hashCode.html)

read-only, inherited

[key](https://api.flutter.dev/flutter/widgets/Widget/key.html)  →  [Key](https://api.flutter.dev/flutter/foundation/Key-class.html)

Controls how one widget replaces another widget in the tree.  [[...]](https://api.flutter.dev/flutter/widgets/Widget/key.html)

final, inherited

[listenable](https://api.flutter.dev/flutter/widgets/AnimatedWidget/listenable.html)  →  [Listenable](https://api.flutter.dev/flutter/foundation/Listenable-class.html)

The  [Listenable](https://api.flutter.dev/flutter/foundation/Listenable-class.html)  to which this widget is listening.  [[...]](https://api.flutter.dev/flutter/widgets/AnimatedWidget/listenable.html)

final, inherited

[runtimeType](https://api.flutter.dev/flutter/dart-core/Object/runtimeType.html)  →  [Type](https://api.flutter.dev/flutter/dart-core/Type-class.html)

A representation of the runtime type of the object.

read-only, inherited

