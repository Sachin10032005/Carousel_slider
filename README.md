# Flutter Carousel Slider Demo

This project demonstrates a simple implementation of a Carousel Slider in Flutter, using the `carousel_slider` package.

## Getting Started

To run this project, you need to have Flutter installed. For instructions on how to install Flutter, visit the [official documentation](https://flutter.dev/docs/get-started/install).

### Packages Used
- `carousel_slider`: A Flutter Carousel widget package.

### Installation

1. Add the following dependency to your `pubspec.yaml` file:

    ```yaml
    dependencies:
      flutter:
        sdk: flutter
      carousel_slider: ^4.0.0  # Make sure to use the latest version
    ```

2. Run the following command to install the dependencies:

    ```bash
    flutter pub get
    ```

### Code Overview

The following Dart code demonstrates how to create a simple image carousel using the `CarouselSlider` widget in Flutter.

```dart
import 'package:flutter/material.dart';
import 'package:carousel_slider/carousel_slider.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: CarouselDemo(),
    );
  }
}

class CarouselDemo extends StatelessWidget {
  final List<String> imgList = [
    'https://images.pexels.com/photos/28375938/pexels-photo-28375938/free-photo-of-flower.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
    'https://images.pexels.com/photos/11998666/pexels-photo-11998666.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
    'https://images.pexels.com/photos/25811334/pexels-photo-25811334/free-photo-of-close-up-of-a-red-rose-growing-a-garden.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1',
  ];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Carousel Slider Demo')),
      body: CarouselSlider(
        options: CarouselOptions(
          height: 400.0,
          autoPlay: true,
          enlargeCenterPage: true,
          aspectRatio: 16 / 9,
          enableInfiniteScroll: true,
          autoPlayInterval: Duration(seconds: 3),
        ),
        items: imgList.map((item) => Container(
          margin: EdgeInsets.all(5.0),
          child: ClipRRect(
            borderRadius: BorderRadius.all(Radius.circular(10.0)),
            child: Stack(
              children: <Widget>[
                Image.network(item, fit: BoxFit.cover, width: 1000.0),
                Positioned(
                  bottom: 0.0,
                  left: 0.0,
                  right: 0.0,
                  child: Container(
                    decoration: BoxDecoration(
                      gradient: LinearGradient(
                        colors: [Color.fromARGB(200, 0, 0, 0), Color.fromARGB(0, 0, 0, 0)],
                        begin: Alignment.bottomCenter,
                        end: Alignment.topCenter,
                      ),
                    ),
                    padding: EdgeInsets.symmetric(vertical: 10.0, horizontal: 20.0),
                    child: Text(
                      'Image ${imgList.indexOf(item) + 1}',
                      style: TextStyle(
                        color: Colors.white,
                        fontSize: 20.0,
                        fontWeight: FontWeight.bold,
                      ),
                    ),
                  ),
                ),
              ],
            ),
          ),
        )).toList(),
      ),
    );
  }
}
