# Flutter를 알아볼까요?

## Flutter란?

* Flutter는 Google에서 새로 공개한 UI프레임워크로 Android와 IOS 어플리케이션을 동시에 개발할 수 있습니다.

* 또한 Kotlin과 Swift 언어도 동시지원해 개발용이성을 높였습니다.

## Flutter 이전에는 어떤 프레임워크가 지원했나요?

### Xamarin

* 기존에는 Xamarin이란 프레임워크가 C#을 이용하여 Android, IOS, Window 프로그래밍을 지원했습니다.

* 하지만 Xamarin은 용량과 개발 지원 부족으로 사용하지 않게 되었습니다.

## Flutter를 직접 설치해볼까요?

### SDK설치

#### [Flutter 공식 페이지](https://flutter.io/docs/development/tools/sdk/archive#windows)

* Flutter 공식페이지에서 Flutter 1.0.0 버전 SDK를 다운받은 후 압축을 해제합니다.

### Android Studio Plugin에서 Flutter, Dart 설치

* Android Studio에서 제공하는 Flutter와 Dart를 설치 후 Android Studio를 재시작 해줍니다.

### Flutter 프로젝트 생성

* 그 후 시작화면에서 Flutter 프로젝트를 생성해줍니다.

### Flutter 기초 체험해보기

```dart
void main() => runApp(MyApp());
```

* runApp()은 view를 보여주는 용도로 사용되며 inflate와 비슷한 기능을 한다.

```dart
class MyHomePage extends StatefulWidget {
  
  MyHomePage({Key key, this.title}) : super(key: key);
  final String title;

  @override
  _MyHomePageState createState() => _MyHomePageState();
}
```

#### 여기서 잠깐 Stateful과 Stateless의 차이점은?

* state는 상태라는 뜻을 가진 단어로 View의 변화에 같이 반응하느냐 하지않느냐로 알고 진행하면 된다.

* 방금전 위에 있던 StatefulWidget은 View의 변화에 함께 반응하기에 StatefulWidget을 사용하고 기능 구현을 따로 진행한다.

```dart
class _MyHomePageState extends State<MyHomePage> {
  var _position=0.0;
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(widget.title),
      ),
      body: Center(
        child:Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            Slider(
              value: _position,
              onChanged: (var position){
                setState(() {
                  _position=position;
                });
              },
            ),
            new Transform.rotate(angle: _position*2*3.14,child: new Icon(Icons.android),),
            new Transform.rotate(angle: _position*2*3.14,child: new Icon(Icons.android),),
```

* 우선 _MyHomePageState 클래스는 MyHomePage 클래스의 기능을 구현하기에 제네릭 타입을 사용하여 기능구현을 진행한다.
* Flutter는 기능들을 추가할 때 마다 자동적으로 View가 쌓이게되면서 늘어나는 형태를 가지고 있다.

* 또한 onChange나 onPress를 이용하여 기능들을 추가할 수 있다.

### 다 만들었으면 실행을 시켜볼까?

![inked _li](https://user-images.githubusercontent.com/26649912/50669480-c9a00100-1008-11e9-8d88-25a757fca6b0.jpg)

* AVD에 들어가서 에뮬레이터가 존재하지 않을시 에뮬레이터를 생성 후 켜주고 애뮬레이터가 존재시 애뮬레이터를 킨 후 어플리케이션을 생성해준다.

### 최종완성 디자인
![dsdfsdfsdfsad](https://user-images.githubusercontent.com/26649912/50669551-1e437c00-1009-11e9-8598-5abb50e97097.PNG)
