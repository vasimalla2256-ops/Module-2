import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

// --------------------------- APP ROOT ---------------------------
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      initialRoute: AppRoutes.home,
      onGenerateRoute: AppRoutes.generateRoute,
    );
  }
}

// --------------------------- ROUTING CLASS ---------------------------
class AppRoutes {
  static const String home = '/';
  static const String about = '/about';

  static Route<dynamic> generateRoute(RouteSettings settings) {
    switch (settings.name) {
      case home:
        return MaterialPageRoute(builder: (_) => HomeScreen());

      case about:
        final Color bgColor = settings.arguments as Color;
        return MaterialPageRoute(
          builder: (_) => AboutScreen(backgroundColor: bgColor),
        );

      default:
        return MaterialPageRoute(
          builder: (_) => Scaffold(
            body: Center(child: Text("Route not found")),
          ),
        );
    }
  }
}

// --------------------------- HOME SCREEN ---------------------------
class HomeScreen extends StatefulWidget {
  @override
  State<HomeScreen> createState() => _HomeScreenState();
}

class _HomeScreenState extends State<HomeScreen> {
  Color selectedColor = Colors.blue;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text("Home Screen"),
        backgroundColor: selectedColor,
      ),
      body: Column(
        mainAxisAlignment: MainAxisAlignment.center,
        children: [
          Text(
            "Choose a color for About Screen:",
            style: TextStyle(fontSize: 18),
          ),
          SizedBox(height: 20),

          // Color selection row
          Row(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              colorBox(Colors.blue),
              colorBox(Colors.green),
              colorBox(Colors.red),
              colorBox(Colors.orange),
            ],
          ),

          SizedBox(height: 40),

          ElevatedButton(
            onPressed: () {
              Navigator.pushNamed(
                context,
                AppRoutes.about,
                arguments: selectedColor, // pass color
              );
            },
            child: Text("Go to About Screen"),
          )
        ],
      ),
    );
  }

  // Small color circle widget
  Widget colorBox(Color color) {
    return GestureDetector(
      onTap: () {
        setState(() {
          selectedColor = color;
        });
      },
      child: Container(
        margin: EdgeInsets.symmetric(horizontal: 8),
        width: 40,
        height: 40,
        decoration: BoxDecoration(
          color: color,
          shape: BoxShape.circle,
          border: Border.all(width: 2, color: Colors.black),
        ),
      ),
    );
  }
}

// --------------------------- ABOUT SCREEN ---------------------------
class AboutScreen extends StatelessWidget {
  final Color backgroundColor;

  const AboutScreen({required this.backgroundColor});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: backgroundColor,
      appBar: AppBar(
        title: Text("About Screen"),
        backgroundColor: backgroundColor,
      ),
      body: Center(
        child: Text(
          "This is the About Screen",
          style: TextStyle(fontSize: 22, color: Colors.white),
        ),
      ),
    );
  }
}
