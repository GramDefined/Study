### Delegate

#### Delegate 란?

- Delegate는 대리자 라는 뜻을 가진 단어   
- UITableViewDelegate를 구현한다 -> UITableView 에서 해야할 일을 대신 구현한다는 의미
- Delegate를 사용하는 방법은 무엇일까?

#### Delegate 패턴
 - Delegate 패턴은 객체 지향 프로그래밍에서 하나의 객체가 모든 일을 처리하지 않고  
 대리자에게 일을 위임하는 패턴
 1. Delegate 를 사용하려면 Delegate 프로토콜을 채택해야 함  

 ~~~swift
 // UITextFieldDelegate 프로토콜 채택한 예시
 class ViewController: UIViewController, UITextFieldDelegate {
     // something todo..
}
 ~~~
2.  Delegate의 위임자를 결정  

~~~swift
@IBOutlet weak var tf : UITextField!

override func viewDidLoad() {
        super.viewDidLoad()
        tf.delegate = self
    }
~~~

3. 필요한 동작 구현

#### 이쯤에서 알아보는 AppDelegate
- AppDelegate는 App이 해야할 일을 대신 구현한다는 의미 
- AppDelegate가 하는 일은 ?

#### AppDelegate의 역할
먼저 저번주에 동기가 설명해준 앱의 실행 순서
1. UIApplication 객체를 생성
2. @UIApplicationMain 어노테이션이 있는 클래스를 찾아 AppDelegate 객체 생성
3. Main Event Loop를 실행(touch, text input등 유저의 액션을 받는 루프) 및 기타 설정

- AppDelegate의 첫번째 역할 - AppDelegate 라는 class 정의

AppDelegate.swift 파일에 있는 AppDelegate class 를 찾아 app delegate 라는 인스턴스 생성,  
app delegate는 앱의 상태에 따라 콘텐츠가 그려지는 창(window)를 만듬

~~~swift
@UIApplicationMain
class AppDelegate: UIResponder, UIApplicationDelegate {
    // 앱의 보이는 화면을 참조함 (view를 담는 컨테이너 역할)
    var window: UIWindow?
}
~~~

- AppDelegate의 두번째 역할 - entry point와, 앱의 입력 이벤트를 전달하는 run loop를 생성

~~~swift
// UIApplicationMain 함수를 호출
@UIApplicationMain
class AppDelegate: UIResponder, UIApplicationDelegate {
    
}
~~~

실제로 앱은 UIApplication이라는 객체로 추상화 되어 Run Loop를 통해 프로그램 코드를 실행한다. 개발자는 AppDelegate를 통해 UIApplication의 역할의 일부를 위임받아 UI를 그리면서 앱을 만들어간다.

또한 AppDelegate는 UIApplicationDelegate 프로토콜을 채택하는데, 이 프로토콜은 앱의 세팅,  
이벤트를 처리하는 여러가지 방법 등을 정의한다.



