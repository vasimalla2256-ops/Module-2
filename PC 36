import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: HoverTextScreen(),
    );
  }
}

class HoverTextScreen extends StatefulWidget {
  @override
  State<HoverTextScreen> createState() => _HoverTextScreenState();
}

class _HoverTextScreenState extends State<HoverTextScreen> {
  bool isHovered = false;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: MouseRegion(
          onEnter: (_) => setState(() => isHovered = true),
          onExit: (_) => setState(() => isHovered = false),
          child: AnimatedDefaultTextStyle(
            duration: const Duration(milliseconds: 300),
            style: TextStyle(
              fontSize: isHovered ? 40 : 30,
              color: isHovered ? Colors.blue : Colors.black,
              fontWeight: isHovered ? FontWeight.bold : FontWeight.normal,
              shadows: isHovered
                  ? [
                      Shadow(
                        color: Colors.blueAccent,
                        blurRadius: 20,
                      ),
                    ]
                  : [],
            ),
            child: const Text("Hover Over Me"),
          ),
        ),
      ),
    );
  }
}
