---
marp: true
theme: gaia
paginate: true
backgroundColor: #fff
Date: 2023-1-25
MetaDescription: Install flutter on Windows, Mac OS and Linux

---

# Documentation Flutter 3.0 
![bg 90%](https://www.mycloudpa.com/assets/img/logo.png)

---
# 1. Introduction to widgets
### 1.1 What is a widget?

The first thing to understand about Flutter is that everything is a widget. Even layout is a widget. Even alignment is a widget. Even the application itself is a widget. A widget is an **immutable object** that describes a specific part of a UI. 

You might be familiar with the concept of widgets from other frameworks. For example, in **Android**, everything is a **View**. In **iOS**, everything is a **UIView**. In **Flutter**, everything is a **Widget**. 

---
Widgets form a hierarchy based on composition. Each widget nests inside, and **inherits** properties from its parent. 
There is no separate “application” object. Instead, the root widget serves this role. For example, this code creates a Material app:

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(
    const Center(
      child: Text(
        'Hello, world!',
        textDirection: TextDirection.ltr, // allow text to be read from left to right
      ),
    ),
  );
}
```

---
The code before creates a widget tree that displays Hello, world! in the center of the screen. 
The **runApp() function** takes the given widget and makes it the **root** of the widget tree. In this example, the root widget is a Center widget. If you look at the Center widget code, you’ll find the following line of code:

```dart
child: Text(
  'Hello, world!',
  textDirection: TextDirection.ltr,
),
```
Each widget have some special **properties**. For example, the Center widget has a child property. The child property is where you nest a 

---

child widget inside its parent. In this example, the Center widget nests a Text child widget. The widget tree for this UI consists of three widgets: 
- the Center root widget
- the Text child of the Center widget
- the Text child of the Text widget.
Each widget have a child property. The child property is where you nest a child widget inside its parent. In this example, the Center widget nests a Text child widget.

One more tips: You can see the properties of a widget in Visual Studio Code by hovering over the widget name. 

---

![bg 90%](gif/tips_flutter_vscode.gif)

---

You can see the widget catalog in the [Flutter documentation](https://flutter.dev/docs/development/ui/widgets).

### 1.2 Stateful and stateless widgets

There are two kinds of widgets: **stateful** and **stateless**.

A **stateless widget** is just what it sounds like: a widget with ***no state*** information. A stateless widget informs the user, or makes the UI look more attractive. A stateless widget doesn’t need to maintain any state.

A **stateful widget** is dynamic. A stateful widget can change its appearance over time based on **user interaction** or other factors, such as **updating the UI** in response to an animation. A stateful  

---

widget **maintains state** that might change during the lifetime of the widget. It uses the state to rebuild the user interface (UI) with updated information. 

For example, if you have a stateful widget that displays a counter, the value of the counter is the state. When the value of the counter changes, the state of the widget needs to be updated to reflect this change. 

A principal advantage of separating the widget state from its appearance is that you can change one without changing the other.
So you can use single widget to create complex widget.

---

### 2.1 How to create a stateful widget?

To create a stateful widget, you need to create two classes:

- A **StatefulWidget** class that creates an instance of

- A **State** class. The StatefulWidget class is, itself, immutable, but the State class persists over the lifetime of the widget.

Here’s an example of a stateful widget, which creates its State class. The StatefulWidget class is called Counter, and the State class is called CounterState.

---

```dart
class Counter extends StatefulWidget {
  @override
  _CounterState createState() => _CounterState();
}

class _CounterState extends State<Counter> {
  int _counter = 0;

  void _increment() {
    setState(() {
      _counter++;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Row(
      children: <Widget>[
        RaisedButton(
          onPressed: _increment,
          child: Text('Increment'),
        ),
        Text('Count: $_counter'),
      ],
    );
  }
}
```

---

Tips: The name of the State class must begin with an underscore (_). This convention indicates that the class is private.

### 2.2 Row and Column

##### 2.2.1 Row 

If you want to create a layout that contains multiple children in a horizontal or vertical array, you can use the Row or Column widget. These widgets are referred to as **“flex”** widgets because they **flex** their children to fill the available space in the main axis (either horizontally or vertically).
So to display some components in a row, you can use the Row widget. For example, this code creates five stars icons in a row:

---

![bg 90%](gif/row_widget.gif)

---

This is the code of the Row widget above:

```dart
Row(
  children: <Widget>[
    Icon(Icons.star, color: Colors.green[500]),
    Icon(Icons.star, color: Colors.green[500]),
    Icon(Icons.star, color: Colors.green[500]),
    Icon(Icons.star, color: Colors.black),
    Icon(Icons.star, color: Colors.black),
  ],
)
```

As you can see, the Row widget takes a list of widgets as its children property. You can center the Row widget by wrapping it in a Center widget.

---

##### 2.2.2 Column

The Column widget works in a similar way to the Row widget, except that it displays its children in a vertical array. For example, this code creates five stars icons in a column:

```dart
Column(
  children: <Widget>[
    Icon(Icons.star, color: Colors.green[500]),
    Icon(Icons.star, color: Colors.green[500]),
    Icon(Icons.star, color: Colors.green[500]),
    Icon(Icons.star, color: Colors.black),
    Icon(Icons.star, color: Colors.black),
  ],
)
```

---

##### 2.2.3 Combine Row and Column

You can combine Row and Column widgets to create more complex layouts. Even if existing widgets don’t provide the exact layout you need, you can combine simple widgets to create custom layouts. 

In this case you can use a GridView widget to create a grid layout but to understand how you can create a custom layout, you need to know how to combine Row and Column widgets.

This code creates two rows and two columns for the first row and four column for the second row and each column contains an icon:

---

```dart
Row(
  children: <Widget>[
    Column(
      children: <Widget>[
        Icon(Icons.star, color: Colors.green[500]),
        Icon(Icons.star, color: Colors.green[500]),
        Icon(Icons.star, color: Colors.green[500]),
        Icon(Icons.star, color: Colors.black),
        Icon(Icons.star, color: Colors.black),
      ],
    ),
    Column(
      children: <Widget>[
        Icon(Icons.star, color: Colors.green[500]),
        Icon(Icons.star, color: Colors.green[500]),
        Icon(Icons.star, color: Colors.black),
        Icon(Icons.star, color: Colors.black),
        Icon(Icons.star, color: Colors.black),
      ],
    ),
  ],
)
```

---

### 2.3 Responsive layout VS Adaptive layout

##### 2.3.1 Responsive layout

To create a responsive layout, you need to use the MediaQuery widget. The MediaQuery widget allows you to access the size of the screen and the orientation of the device. 

For example, this code creates a responsive layout that displays a title and a button in a column if the device is in portrait mode and in a row if the device is in landscape mode:

---

```dart
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      home: Scaffold(
        appBar: AppBar(
          title: Text('Flutter layout demo'),
        ),
        body: Center(
          child: MediaQuery.of(context).orientation == Orientation.portrait
              ? Column(
                  children: <Widget>[
                    Text('Portrait mode'),
                    RaisedButton(
                      onPressed: () {},
                      child: Text('Button'),
                    ),
                  ],
                )
              : Row(
                  children: <Widget>[
                    Text('Landscape mode'),
                    RaisedButton(
                      onPressed: () {},
                      child: Text('Button'),
                    ),
                  ],
                ),
        ),
      ),
    );
  }
}
```

---

![bg 90%](gif/responsive.gif)

---

There are other widgets that allow you to create a responsive layout, I will  not mention some of them here but you can find them in the official documentation:
- **LayoutBuilder** class: A widget that builds itself based on the parent's size.
- **AspectRatio** widget: This widget allows you to specify the aspect ratio of the child widget. 
- **CustomSingleChildLayout** widget: A widget that defers the layout of its single child to a delegate.
- **OrientationBuilder** widget: A widget that builds itself differently depending on the orientation of the parent.

---

##### 2.3.2 Adaptive layout

Maybe your question is: What is the difference between responsive layout and adaptive layout?

The difference is that the responsive layout changes the layout based on the size of the screen, but the adaptive layout changes the layout based on the device.

I will not explain how to create an adaptive layout because it is not the main topic of this tutorial, but you can find more information about it in the official documentation by clicking [Adaptive Apps](https://docs.flutter.dev/development/ui/layout/building-adaptive-apps).

---

You have here some key points about the layout in Flutter to improve your skills in Flutter development.

- **TargetPlatform** class: An enumeration of the platforms that Flutter runs on.
- **DefaultTargetPlatform** class: The default target platform for the current application.
- **ThemeData** class: The colors and typographic choices of a material design application.
- **Theme** widget: A widget that controls the colors and typography of its child widgets.
