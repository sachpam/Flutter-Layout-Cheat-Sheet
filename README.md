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

## Methods

[build](https://api.flutter.dev/flutter/widgets/AnimatedBuilder/build.html)([BuildContext](https://api.flutter.dev/flutter/widgets/BuildContext-class.html)  context)  →  [Widget](https://api.flutter.dev/flutter/widgets/Widget-class.html)

Override this method to build widgets that depend on the state of the listenable (e.g., the current value of the animation).

override

[createElement](https://api.flutter.dev/flutter/widgets/StatefulWidget/createElement.html)()  →  [StatefulElement](https://api.flutter.dev/flutter/widgets/StatefulElement-class.html)

Creates a  [StatefulElement](https://api.flutter.dev/flutter/widgets/StatefulElement-class.html)  to manage this widget's location in the tree.  [[...]](https://api.flutter.dev/flutter/widgets/StatefulWidget/createElement.html)

inherited

[createState](https://api.flutter.dev/flutter/widgets/AnimatedWidget/createState.html)()  → _AnimatedState

Subclasses typically do not override this method.

inherited

[debugDescribeChildren](https://api.flutter.dev/flutter/foundation/DiagnosticableTree/debugDescribeChildren.html)()  →  [List](https://api.flutter.dev/flutter/dart-core/List-class.html)<[DiagnosticsNode](https://api.flutter.dev/flutter/foundation/DiagnosticsNode-class.html)>

Returns a list of  [DiagnosticsNode](https://api.flutter.dev/flutter/foundation/DiagnosticsNode-class.html)  objects describing this node's children.  [[...]](https://api.flutter.dev/flutter/foundation/DiagnosticableTree/debugDescribeChildren.html)

@protected, inherited

[debugFillProperties](https://api.flutter.dev/flutter/widgets/AnimatedWidget/debugFillProperties.html)([DiagnosticPropertiesBuilder](https://api.flutter.dev/flutter/foundation/DiagnosticPropertiesBuilder-class.html)  properties)  → void

Add additional properties associated with the node.  [[...]](https://api.flutter.dev/flutter/widgets/AnimatedWidget/debugFillProperties.html)

inherited

[noSuchMethod](https://api.flutter.dev/flutter/dart-core/Object/noSuchMethod.html)([Invocation](https://api.flutter.dev/flutter/dart-core/Invocation-class.html)  invocation)  → dynamic

Invoked when a non-existent method or property is accessed.  [[...]](https://api.flutter.dev/flutter/dart-core/Object/noSuchMethod.html)

inherited

[toDiagnosticsNode](https://api.flutter.dev/flutter/foundation/DiagnosticableTree/toDiagnosticsNode.html)({[String](https://api.flutter.dev/flutter/dart-core/String-class.html)  name, [DiagnosticsTreeStyle](https://api.flutter.dev/flutter/foundation/DiagnosticsTreeStyle-class.html)  style  })  →  [DiagnosticsNode](https://api.flutter.dev/flutter/foundation/DiagnosticsNode-class.html)

Returns a debug representation of the object that is used by debugging tools and by  [DiagnosticsNode.toStringDeep](https://api.flutter.dev/flutter/foundation/DiagnosticableTree/toStringDeep.html).  [[...]](https://api.flutter.dev/flutter/foundation/DiagnosticableTree/toDiagnosticsNode.html)

inherited

[toString](https://api.flutter.dev/flutter/foundation/DiagnosticableMixin/toString.html)({[DiagnosticLevel](https://api.flutter.dev/flutter/foundation/DiagnosticLevel-class.html)  minLevel:  DiagnosticLevel.debug  })  →  [String](https://api.flutter.dev/flutter/dart-core/String-class.html)

Returns a string representation of this object.

inherited

[toStringDeep](https://api.flutter.dev/flutter/foundation/DiagnosticableTree/toStringDeep.html)({[String](https://api.flutter.dev/flutter/dart-core/String-class.html)  prefixLineOne:  '', [String](https://api.flutter.dev/flutter/dart-core/String-class.html)  prefixOtherLines, [DiagnosticLevel](https://api.flutter.dev/flutter/foundation/DiagnosticLevel-class.html)  minLevel:  DiagnosticLevel.debug  })  →  [String](https://api.flutter.dev/flutter/dart-core/String-class.html)

Returns a string representation of this node and its descendants.  [[...]](https://api.flutter.dev/flutter/foundation/DiagnosticableTree/toStringDeep.html)

inherited

[toStringShallow](https://api.flutter.dev/flutter/foundation/DiagnosticableTree/toStringShallow.html)({[String](https://api.flutter.dev/flutter/dart-core/String-class.html)  joiner:  ', ', [DiagnosticLevel](https://api.flutter.dev/flutter/foundation/DiagnosticLevel-class.html)  minLevel:  DiagnosticLevel.debug  })  →  [String](https://api.flutter.dev/flutter/dart-core/String-class.html)

Returns a one-line detailed description of the object.  [[...]](https://api.flutter.dev/flutter/foundation/DiagnosticableTree/toStringShallow.html)

inherited

[toStringShort](https://api.flutter.dev/flutter/widgets/Widget/toStringShort.html)()  →  [String](https://api.flutter.dev/flutter/dart-core/String-class.html)

A short, textual description of this widget.

inherited

## Operators

[operator ==](https://api.flutter.dev/flutter/dart-core/Object/operator_equals.html)(dynamic  other)  →  [bool](https://api.flutter.dev/flutter/dart-core/bool-class.html)

The equality operator.  [[...]](https://api.flutter.dev/flutter/dart-core/Object/operator_equals.html)

inherited

1.  [CONSTRUCTORS](https://api.flutter.dev/flutter/widgets/AnimatedBuilder-class.html#constructors)
2.  [AnimatedBuilder](https://api.flutter.dev/flutter/widgets/AnimatedBuilder/AnimatedBuilder.html)
3.  [PROPERTIES](https://api.flutter.dev/flutter/widgets/AnimatedBuilder-class.html#instance-properties)
4.  [builder](https://api.flutter.dev/flutter/widgets/AnimatedBuilder/builder.html)
5.  [child](https://api.flutter.dev/flutter/widgets/AnimatedBuilder/child.html)
6.  [hashCode](https://api.flutter.dev/flutter/dart-core/Object/hashCode.html)
7.  [key](https://api.flutter.dev/flutter/widgets/Widget/key.html)
8.  [listenable](https://api.flutter.dev/flutter/widgets/AnimatedWidget/listenable.html)
9.  [runtimeType](https://api.flutter.dev/flutter/dart-core/Object/runtimeType.html)
10.  [METHODS](https://api.flutter.dev/flutter/widgets/AnimatedBuilder-class.html#instance-methods)
11.  [build](https://api.flutter.dev/flutter/widgets/AnimatedBuilder/build.html)
12.  [createElement](https://api.flutter.dev/flutter/widgets/StatefulWidget/createElement.html)
13.  [createState](https://api.flutter.dev/flutter/widgets/AnimatedWidget/createState.html)
14.  [debugDescribeChildren](https://api.flutter.dev/flutter/foundation/DiagnosticableTree/debugDescribeChildren.html)
15.  [debugFillProperties](https://api.flutter.dev/flutter/widgets/AnimatedWidget/debugFillProperties.html)
16.  [noSuchMethod](https://api.flutter.dev/flutter/dart-core/Object/noSuchMethod.html)
17.  [toDiagnosticsNode](https://api.flutter.dev/flutter/foundation/DiagnosticableTree/toDiagnosticsNode.html)
18.  [toString](https://api.flutter.dev/flutter/foundation/DiagnosticableMixin/toString.html)
19.  [toStringDeep](https://api.flutter.dev/flutter/foundation/DiagnosticableTree/toStringDeep.html)
20.  [toStringShallow](https://api.flutter.dev/flutter/foundation/DiagnosticableTree/toStringShallow.html)
21.  [toStringShort](https://api.flutter.dev/flutter/widgets/Widget/toStringShort.html)
22.  [OPERATORS](https://api.flutter.dev/flutter/widgets/AnimatedBuilder-class.html#operators)
23.  [operator ==](https://api.flutter.dev/flutter/dart-core/Object/operator_equals.html)

Flutter 1.9.1+hotfix.5 •
