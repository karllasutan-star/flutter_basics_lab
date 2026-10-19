# Flutter Architecture, Widgets and Basic UI
## Laboratory Answers

Name: Karl Justin Lasutan  
Section: BSIT-3A

## GitHub Repository

https://github.com/karllasutan-star/flutter_basics_lab

---

## Activity 2 Debug Console

Last three `build()` lines:

```text
build() called: 4 glasses
build() called: 5 glasses
build() called: 6 glasses

Activity 2 Observation
When I moved _glasses++ outside setState(), the value could change internally, but the displayed number did not immediately update. This happened because Flutter was not notified that the state had changed, so the widget was not rebuilt.

Activity 3 Observation
When I removed Expanded from one StatBox, that box no longer shared the available width equally with the others. Its width depended more on its content, while the remaining Expanded widgets divided the leftover space.

Activity 5 Observation
I changed the ElevatedButton border radius from 8 to 20 inside buildTheme(). The Elevated button became more rounded because the theme applied the new shape to the ElevatedButton.


Review Questions
1. What is the difference between a StatelessWidget and a StatefulWidget? Give one example of each from this lab. A StatelessWidget is used when the widget does not need to change its data while the app is running. A StatefulWidget is used when the widget has data that can change and the screen needs to update.

An example of a StatelessWidget is the ProfileCard in Activity 1. An example of a StatefulWidget is the WaterTrackerPage in Activity 2 because the number of glasses changes when the buttons are pressed.

2. Why is a StatefulWidget written as two classes? What does each class do?
A StatefulWidget uses two classes because the widget itself describes the configuration, while the State class stores the data that can change.

For example, WaterTrackerPage creates the state object, while _WaterTrackerPageState stores _glasses and contains the methods and build() function used to update the screen.

3. In Activity 2, what happened when you changed _glasses outside setState()? Why?
When I changed _glasses without using setState(), the number displayed on the screen did not immediately update. The variable changed, but Flutter was not told to rebuild the widget.

setState() is important because it tells Flutter that the state has changed and that build() should run again.

4. Looking at the Debug Console in Activity 2, when is build() called?
build() is called when the widget is first displayed and again after setState() changes the state. In Activity 2, a new build() called message appeared when the number of glasses was updated.

5. Explain the main axis and the cross axis of a Row and of a Column.
For a Row, the main axis is horizontal because its children are arranged from left to right. Its cross axis is vertical.

For a Column, the main axis is vertical because its children are arranged from top to bottom. Its cross axis is horizontal.

6. In Activity 3, what happened when you removed Expanded from a StatBox? What does Expanded do?
When I removed Expanded from one StatBox, it no longer had the same width as the other boxes. Its width depended more on its content, while the other Expanded widgets divided the remaining available space.

Expanded makes a child use the available space along the main axis. When several widgets are wrapped with Expanded, they can share the available space equally.

7. Why do we use GridView.builder for the menu instead of a Column with many children?
GridView.builder is useful because it arranges the menu items in a grid and creates items as they are needed. This is more suitable for a menu with many items than placing all of them manually inside a Column.

It also allows the menu to scroll and makes the code easier to manage.

8. How do Stack and Positioned create the Best seller badge in Activity 4?
Stack allows widgets to be placed on top of each other. The main menu information is displayed inside the card, while the Best seller badge is placed over it.

Positioned controls the exact location of the badge inside the Stack. In Activity 4, it places the badge near the top-left corner of the menu card.

9. What is the difference between customizing with ThemeData and with a style on one widget? Give one example of each from Activity 5.
ThemeData is used to apply a consistent design to multiple widgets or to the whole application. A style placed directly on one widget only affects that specific widget.

An example of ThemeData in Activity 5 is elevatedButtonTheme, which changes the appearance of ElevatedButtons. An example of styling one widget directly is using a TextStyle on a specific Text widget.

10. When you flip the dark-mode switch in Activity 5, which widget holds the state, and how does the change reach MaterialApp?
The dark-mode state is stored in _ThemeDemoAppState using the _isDark variable.

When the switch changes, SettingsPage calls the onDarkChanged callback. This calls _setDark(), which changes _isDark inside setState(). Flutter rebuilds ThemeDemoApp, and MaterialApp uses _isDark to choose between ThemeMode.dark and ThemeMode.light.
