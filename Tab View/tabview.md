```dart

import 'package:flutter/material.dart';

class TabView extends StatefulWidget {
  const TabView({Key? key}) : super(key: key);

  @override
  State<TabView> createState() => _TabViewState();
}

class _TabViewState extends State<TabView> {
  /// [ currentIndex ] is the index of the current tab which controls the page transitions.
  int currentIndex = 0;

  /// [ body ] is the body of the tab view; ie, [ body ] determines which is the current interface.
  Widget? body;

  /// [ title ] is the title of the tab view shown in the [ AppBar ].
  String? title;

  /// [ initState] is called when the widget is created.
  @override
  void initState() {
    super.initState();

    /// [ changeView(0) ] is set by default as 0 inorderto set it at the initial page when the widgets are initialized.
    changeView(0);
  }

  /// [ onTap ] is the callback for when a tab is tapped used to [ change ] the view .
  void onTap(index) {
    changeView(index);
  }

  /// [ changeView ] is the function used to change the view.
  changeView(index) {
    setState(() {
      currentIndex = index;

      /// [ index ] will check and set the [ body ] to the correct view according to cases we have written.
      switch (index) {
        case 0:
          title = 'Home';
          body = Home();
          break;
        case 1:
          title = 'Profile';
          body = Profile();
          break;
        case 2:
          title = 'Settings';
          body = Settings();
          break;

        /// [ default ] is used to set the [ body ] to the default view; ie, it will redirect to home page.
        default:
          title = 'Home';
          body = Home();
          break;
      }
    });
  }

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Tab View',
      home: Scaffold(
        appBar: AppBar(
          title: Text(title!),
        ),
        body: body,
      ),
    );
  }
}

```