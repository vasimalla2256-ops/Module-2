import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

/// ===========================
///           VIEW
/// ===========================
class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: CounterView(),
    );
  }
}

class CounterView extends StatelessWidget {
  final CounterViewModel viewModel = CounterViewModel();

  CounterView({super.key});

  @override
  Widget build(BuildContext context) {
    return AnimatedBuilder(
      animation: viewModel, // listens to changes
      builder: (context, _) {
        return Scaffold(
          appBar: AppBar(title: const Text("MVVM Counter App")),
          body: Center(
            child: Text(
              "Count: ${viewModel.model.count}",
              style: const TextStyle(fontSize: 32),
            ),
          ),
          floatingActionButton: FloatingActionButton(
            onPressed: viewModel.increment,
            child: const Icon(Icons.add),
          ),
        );
      },
    );
  }
}

/// ===========================
///           MODEL
/// ===========================
class CounterModel {
  int count;
  CounterModel({this.count = 0});
}

/// ===========================
///         VIEW MODEL
/// ===========================
class CounterViewModel extends ChangeNotifier {
  final CounterModel model = CounterModel();

  void increment() {
    model.count++;
    notifyListeners(); // notify UI to update
  }
}
