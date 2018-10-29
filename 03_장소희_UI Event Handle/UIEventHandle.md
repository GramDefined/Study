# 화면 이벤트 처리 (UI Event Handle)  
## 화면 이벤트 핸들러 (UI Event Handler)  
* **"어떤 행위에 대한 요청을 처리하는 것"**
* ex) 행위(이벤트) : 버튼 누르기 → 요청 : 텍스트뷰 표시하기  
* **이벤트소스** : 이벤트가 발생하는 장소
* **핸들러** : 이벤트를 처리하는 클래스 

### 이벤트 실행 순서
1) 이벤트 발생
2) 액티비티가 이벤트 소스에 알림
3) 이벤트 소스에 등록된 핸들러 객체 생성 및 메서드 호출
4) 핸들러 메서드 실행

## 이벤트 처리 방법
### 1. 익명클래스 생성하여 이벤트 리스너로 사용
 ```java
 view.setOnClickListener(new View.onClickListener(){
  @Override
  public void onClick(View view){
    // Click Event
  }
})
 ```
 * 이벤트가 어디서 처리되는지 직관적으로 확인 가능
 * 코드의 간결성  
 → 가장 자주 사용되는 방법
 *  이벤트 소스 수가 증가하는 만큼 익명 클래스 객체를 생성
 

### 2. 익명클래스의 참조를 이벤트 리스너로 활용

생성된 익명 클래스 객체를 모든 이벤트 소스의 이벤트로 사용하는 것. 각 이벤트 소스들에 대한 이벤트 처리코드가 이벤트 리스너 별로 구분되는 것이 아닌 이벤트 리스너 안의 핸들러 함수에서 구분됨.
 ```java
 View.OnClickListener onClickListener = new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                switch (view.getId()) {
                    case R.id.Gram :
                        // Click Event
                        break ;
                    case R.id.Undefined :
                        // Click Event
                        break ;
                }
            }
        } ;
 view.setOnClickListener(onClickListener) ;
 ```

 * 매번 객체를 새로 만들지 않아도 됨
 * 이벤트가 어디서 처리되는지 직관적이지 않음

### 3. XML에서 View에 onClick 메서드 설정
 XML에 View를 추가할 때 onClick 속성을 사용해 이벤트 핸들러 함수 지정. 지정한 핸들러 함수와 같은 이름의 함수를 멤버함수로 추가.
``` xml
<Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/clickBtn"
        android:text="click"
        android:onClick="onButtonClick" />
```

```java
public void onButtonClick(View view) { 
     // Click Event
     }   
```

* 좀 더 간단하고 직관적인 방법
* 그러나 코드의 역할 이슈(UI 구성은 XML, 이벤트 처리는 JAVA) 때문에 별로 사용하지 않는 방법


# Touch-Click-LongClick의 관계

### 버튼 Click 시
Touch(down) → Touch(up) → Click 순으로 발생

### 버튼 LongClick 시
Touch(down) → LongClick → Touch(up) → Click 순으로 발생
