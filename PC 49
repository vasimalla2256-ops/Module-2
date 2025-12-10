import 'package:flutter/material.dart';
import 'package:shared_preferences/shared_preferences.dart';

void main() {
  runApp(const MaterialApp(
    debugShowCheckedModeBanner: false,
    home: LocalStorageTextField(),
  ));
}

class LocalStorageTextField extends StatefulWidget {
  const LocalStorageTextField({super.key});

  @override
  State<LocalStorageTextField> createState() => _LocalStorageTextFieldState();
}

class _LocalStorageTextFieldState extends State<LocalStorageTextField> {
  final TextEditingController _controller = TextEditingController();
  String savedKey = "saved_text";

  @override
  void initState() {
    super.initState();
    loadSavedText();
  }

  /// Load previously saved text from SharedPreferences
  Future<void> loadSavedText() async {
    final prefs = await SharedPreferences.getInstance();
    String? storedText = prefs.getString(savedKey);

    if (storedText != null) {
      _controller.text = storedText;
    }
  }

  /// Save the text whenever user types
  Future<void> saveText(String value) async {
    final prefs = await SharedPreferences.getInstance();
    prefs.setString(savedKey, value);
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text("Persistent TextFormField")),
      body: Padding(
        padding: const EdgeInsets.all(20.0),
        child: TextFormField(
          controller: _controller,
          decoration: const InputDecoration(
            labelText: "Enter something...",
            border: OutlineInputBorder(),
          ),
          onChanged: (value) {
            saveText(value); // Save on every change
          },
        ),
      ),
    );
  }
}
