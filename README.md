import 'dart:math';

import 'package:flutter/material.dart';

void main() {
  runApp(const FunnyQuotesApp());
}

class FunnyQuotesApp extends StatelessWidget {
  const FunnyQuotesApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        colorScheme: ColorScheme.fromSeed(seedColor: Colors.deepPurple),
        useMaterial3: true,
      ),
      home: const HomePage(),
    );
  }
}

class HomePage extends StatefulWidget {
  const HomePage({super.key});

  @override
  State<HomePage> createState() => _HomePageState();
}

class _HomePageState extends State<HomePage> {
  static const List<String> quoteList = [
    'ไก่ที่หมดจาน ดีกว่าการที่เธอหมดใจ',
    'เหมาะกับการอยู่ในวงเหล้า มากกว่าการเข้าไปอยู่ในใจใคร',
    'ใบไม้ยังร่วง นับประสาอะไรกับคนง่วงอย่างเรา',
    'ไม่ถูกหวยไม่เป็นไร ขอเป็นคนที่ถูกใจเธอแทนแล้วกัน',
    'คงจะมีแต่แชมพูเท่านั้นแหละ ที่เป็นห่วงผม',
  ];
  static const List<Color> colorList = [
    Colors.blue,
    Colors.amberAccent,
    Colors.indigoAccent,
    Colors.yellowAccent,
    Colors.black87,
  ];
  var quote = quoteList[0]; //state variable
  var colors = colorList[0];
  void handldClickGo(){
    setState(() {
      var random = Random();
      var randomcolors = Random();
      var randomIndex = random.nextInt(quoteList.length);
      var randomColor = randomcolors.nextInt(colorList.length);
      quote = quoteList[randomIndex];
      colors = colorList[randomColor];
    });
  }

  @override
  Widget build(BuildContext context) {

    return Scaffold(
      appBar: AppBar(title: const Text('Funny Quotes')),
      floatingActionButton: FloatingActionButton(
        child: Text('Go'),
        onPressed: handldClickGo,
      ),
      body: Center(
        child: Padding(
          padding: const EdgeInsets.all(32.0),
          child: Text(
            quote,
            style: TextStyle(
              color: colors,
              fontSize: 30,
              fontStyle: FontStyle.italic,
              fontWeight: FontWeight.bold,
            ),
            textAlign: TextAlign.center,
          ),
        ),
      ),
    );
  }
}
