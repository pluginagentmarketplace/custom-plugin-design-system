---
name: mobile-development
description: Master mobile app development using native (Swift, Kotlin) and cross-platform frameworks (React Native, Flutter). Learn mobile UI design, app lifecycle, platform-specific optimization, and app store distribution.
---

# Mobile Development

## Quick Start

Mobile development creates applications for iOS, Android, and cross-platform platforms.

### Native iOS (Swift):

```swift
import SwiftUI

struct ContentView: View {
  @State private var count = 0

  var body: some View {
    VStack {
      Text("Count: \(count)")
        .font(.title)
      Button("Increment") {
        count += 1
      }
    }
  }
}
```

### Native Android (Kotlin):

```kotlin
@Composable
fun CounterApp() {
  var count by remember { mutableStateOf(0) }

  Column {
    Text("Count: $count", style = MaterialTheme.typography.headlineMedium)
    Button(onClick = { count++ }) {
      Text("Increment")
    }
  }
}
```

### Cross-Platform (React Native):

```javascript
import React, { useState } from 'react';
import { View, Text, TouchableOpacity } from 'react-native';

export default function Counter() {
  const [count, setCount] = useState(0);

  return (
    <View>
      <Text>Count: {count}</Text>
      <TouchableOpacity onPress={() => setCount(count + 1)}>
        <Text>Increment</Text>
      </TouchableOpacity>
    </View>
  );
}
```

### Cross-Platform (Flutter):

```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatefulWidget {
  @override
  State<MyApp> createState() => _MyAppState();
}

class _MyAppState extends State<MyApp> {
  int count = 0;

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: Center(
          child: Column(
            children: [
              Text('Count: $count'),
              ElevatedButton(
                onPressed: () => setState(() => count++),
                child: Text('Increment'),
              ),
            ],
          ),
        ),
      ),
    );
  }
}
```

## Core Concepts

### 1. iOS Development (Swift)

#### SwiftUI Framework
```swift
struct DetailView: View {
  @State private var isPresented = false
  @State private var selectedColor = Color.blue

  var body: some View {
    NavigationStack {
      VStack {
        ColorPicker("Select Color", selection: $selectedColor)
        NavigationLink("Go to Details") {
          DetailPage()
        }
      }
    }
  }
}
```

#### Key iOS Concepts
- View hierarchy and layouts
- State management (@State, @ObservedObject)
- Navigation (NavigationStack)
- Data persistence (UserDefaults, Core Data)
- Networking (URLSession)
- Async/await for async operations

### 2. Android Development (Kotlin)

#### Jetpack Compose
```kotlin
@Composable
fun UserProfile(userId: String) {
  val viewModel: UserViewModel = viewModel()
  val user by viewModel.getUser(userId).collectAsState(initial = null)

  user?.let {
    Column(modifier = Modifier.padding(16.dp)) {
      Text(it.name, style = MaterialTheme.typography.headlineSmall)
      Text(it.email)
    }
  }
}
```

#### Key Android Concepts
- Activity lifecycle
- Fragment management
- Navigation component
- Room database
- Retrofit for networking
- Coroutines for concurrency
- Dependency injection (Hilt)

### 3. Cross-Platform (React Native)

#### Navigation
```javascript
import { NavigationContainer } from '@react-navigation/native';
import { createNativeStackNavigator } from '@react-navigation/native-stack';

const Stack = createNativeStackNavigator();

export default function App() {
  return (
    <NavigationContainer>
      <Stack.Navigator>
        <Stack.Screen name="Home" component={HomeScreen} />
        <Stack.Screen name="Details" component={DetailsScreen} />
      </Stack.Navigator>
    </NavigationContainer>
  );
}
```

#### State Management
- Redux
- Context API
- Zustand
- MobX

### 4. Cross-Platform (Flutter)

#### State Management
```dart
class MyApp extends ChangeNotifier {
  List<Todo> _todos = [];

  List<Todo> get todos => _todos;

  void addTodo(Todo todo) {
    _todos.add(todo);
    notifyListeners();
  }
}

// Usage with Consumer
Consumer<MyApp>(
  builder: (context, myApp, child) {
    return ListView(
      children: myApp.todos.map((todo) => Text(todo.title)).toList(),
    );
  },
)
```

## Advanced Topics

### Performance Optimization
- Memory management
- Battery optimization
- Network efficiency
- UI rendering optimization
- App startup time

### Native Modules
- Accessing native APIs
- Custom platform channels
- C++ integration

### Testing
- Unit tests
- Widget tests (Flutter)
- Integration tests
- UI tests

### App Distribution

#### iOS
- App Store submission
- TestFlight beta testing
- Code signing certificates
- App Store Connect

#### Android
- Google Play Store
- Internal testing track
- Beta and alpha releases
- Signing APK/Bundle

## Real-World Projects

1. **Weather App** - API integration, real-time data
2. **Todo Application** - Local persistence, CRUD operations
3. **Social Media** - Real-time messaging, media uploads
4. **E-commerce App** - Shopping cart, payments
5. **Multiplayer Game** - Real-time sync, game mechanics

---

**Use this skill when:**
- Learning iOS or Android development
- Building cross-platform apps
- Optimizing mobile performance
- Publishing to app stores
- Implementing platform-specific features
