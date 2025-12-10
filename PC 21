import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: ColorChangeExample(),
    );
  }
}

class ColorChangeExample extends StatefulWidget {
  @override
  _ColorChangeExampleState createState() => _ColorChangeExampleState();
}

class _ColorChangeExampleState extends State<ColorChangeExample> {
  bool isColored = false; // Tracks current color state

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text("Change Text Color")),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Text(
              "First Name",
              style: TextStyle(
                fontSize: 24,
                color: isColored ? Colors.red : Colors.black,
              ),
            ),
            SizedBox(height: 20),
            Text(
              "Last Name",
              style: TextStyle(
                fontSize: 24,
                color: isColored ? Colors.red : Colors.black,
              ),
            ),
            SizedBox(height: 40),
            ElevatedButton(
              onPressed: () {
                setState(() {
                  isColored = !isColored; // Toggle color
                });
              },
              child: Text("Change Text Color"),
            )
          ],
        ),
      ),
    );
  }
}
