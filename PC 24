import 'package:flutter/material.dart';
import 'package:flutter_riverpod/flutter_riverpod.dart';
import 'package:audioplayers/audioplayers.dart';
import 'dart:math';

// --------------------- STATE PROVIDER ---------------------
class AppState {
  final Color color;
  final int noteIndex;
  AppState({required this.color, required this.noteIndex});

  AppState copyWith({Color? color, int? noteIndex}) {
    return AppState(
      color: color ?? this.color,
      noteIndex: noteIndex ?? this.noteIndex,
    );
  }
}

class AppNotifier extends StateNotifier<AppState> {
  AppNotifier()
      : super(AppState(
          color: Colors.blue,
          noteIndex: 1,
        ));

  final player = AudioPlayer();

  void changeState() {
    // generate random color and random note (1–10)
    final random = Random();
    final newColor = Color.fromARGB(
      255,
      random.nextInt(256),
      random.nextInt(256),
      random.nextInt(256),
    );
    final newNote = random.nextInt(10) + 1;

    state = state.copyWith(color: newColor, noteIndex: newNote);

    // play sound
    player.play(AssetSource("notes/note$newNote.wav"));
  }
}

final appProvider =
    StateNotifierProvider<AppNotifier, AppState>((ref) => AppNotifier());

// ------------------------- UI -------------------------
void main() {
  runApp(const ProviderScope(child: MyApp()));
}

class MyApp extends ConsumerWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context, WidgetRef ref) {
    final appState = ref.watch(appProvider);

    return MaterialApp(
      home: Scaffold(
        backgroundColor: appState.color,
        appBar: AppBar(
          title: const Text("Riverpod Music & Color App"),
          backgroundColor: appState.color,
        ),
        body: Center(
          child: ElevatedButton(
            onPressed: () {
              ref.read(appProvider.notifier).changeState();
            },
            child: const Text("Play Note & Change Color"),
          ),
        ),
      ),
    );
  }
}
