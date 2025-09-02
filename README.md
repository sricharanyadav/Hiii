import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(home: ResponsiveHome());
  }
}

class ResponsiveHome extends StatelessWidget {
  const ResponsiveHome({super.key});

  @override
  Widget build(BuildContext context) {
    // Get screen dimensions
    double screenWidth = MediaQuery.of(context).size.width;
    return Scaffold(
      appBar: AppBar(title: Text('Responsive UI Example')),
      body: Center(
        child: Container(
          padding: EdgeInsets.all(16.0),
          child: Column(
            children: [
              // Responsive Text
              Text(
                'Hello, Flutter!',
                style: TextStyle(
                  fontSize: screenWidth * 0.1,
                ), // Responsive font size
              ),
              SizedBox(height: 20),
              // Responsive Row
              Row(
                mainAxisAlignment: MainAxisAlignment.spaceEvenly,
                children: [
                  Flexible(
                    flex: 2,
                    child: Container(
                      color: Colors.blue,
                      height: 100,
                      child: Center(child: Text('Box 1')),
                    ),
                  ),
                  SizedBox(width: 10),
                  Flexible(
                    flex: 3,
                    child: Container(
                      color: Colors.green,
                      height: 100,
                      child: Center(child: Text('Box 2')),
                    ),
                  ),
                ],
              ),
              SizedBox(height: 20),
              // Responsive Grid
              Expanded(
                child: GridView.count(
                  crossAxisCount: screenWidth > 600
                      ? 4
                      : 2, // Adjust grid columns based on screen width
                  children: List.generate(6, (index) {
                    return Container(
                      margin: EdgeInsets.all(6.0),
                      color: Colors.red,
                      child: Center(child: Text('Item ${index + 1}')),
                    );
                  }),
                ),
              ),
            ],
          ),
        ),
      ),
    );
  }
}
