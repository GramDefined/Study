```
package com.example.nwar.study;

import android.graphics.Point;
import android.support.v7.app.ActionBar;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.Display;
import android.widget.Button;
import android.widget.RelativeLayout;

public class MainActivity extends AppCompatActivity {

    @Override 
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        ActionBar actionBar = getSupportActionBar();
        actionBar.hide(); // 액션 바 숨김
        Display display = getWindowManager().getDefaultDisplay();
        Point size = new Point();
        display.getSize(size);
        int width = size.x; // 단말기의 x축 크기
        int height = size.y - getStatusBarHeight(); // 단말기의 y축 크기(스테이터스바 제외)

        RelativeLayout layout = new RelativeLayout(this); //RelativeLayout 생성
        RelativeLayout.LayoutParams params = new RelativeLayout.LayoutParams(400, 600); // RelativeLayout 크기 설정
        layout.setLayoutParams(params); // 크기 적용
        layout.setBackgroundColor(0xFFFFFFFF); // 레이아웃의 배경 색 설정
        layout.setPivotX(0); // 레이아웃의 기준점 설정
        layout.setPivotY(0); // "
        layout.setScaleX((float)(width/(double)400));
        layout.setScaleY((float)(height/(double)600));

        Button button = new Button(this);
        RelativeLayout.LayoutParams params2 = new RelativeLayout.LayoutParams(200, 100);
        params2.leftMargin = 100;
        params2.topMargin = 200;
        button.setLayoutParams(params2);
        layout.addView(button, params2);
        setContentView(layout);
    }

    public int getStatusBarHeight(){
        int res = 0;
        int id = getResources().getIdentifier("status_bar_height","dimen","android");
        if(id > 0){
            res = getResources().getDimensionPixelSize(id);
        }
        return res;
    }
}
```

> ActionBar

.hide(); : 액션 바를 숨김

> Display

.getSize(Point p); : 디바이스의 해상도를 구함.

+ p.x; : 단말기의 x축 크기
+ p.y; : 단말기의 y축 크기

> RelativeLayout

생성자 : new RelativeLayout(context c);

.setLayoutParams(RelativeLayout.LayoutParams params); : params의 속성 적용

.setBackgroundColor(0x ...  ) : 레이아웃의 배경 색 설정

.setPivotX(Int x); : 레이아웃의 기준점(X축) 설정

.setPivotY(Int y); : 레이아웃의 기준점(Y축) 설정

.setScaleX(float fx); : x축의 비율 설정

.setScaleY(float fy); : y축의 비율 설정

.addView(ViewType, ParamsType) : ViewType에 ParamsType 적용시켜 View를 만듦. (ParamsType = RelativeLayout.LayoutParams)

> RelativeLayout.LayoutParams

생성자 : new RelativeLayout.LayoutParams(Int weight, Int Height);

.leftMargin = Int leftMargin; : 왼쪽 마진값 설정

.topMargin = Int topMargin; : 위쪽 마진값 설정

> Button

생성자: new Button(context c);

.setLayoutParams(ParamsType params); : params의 속성 값 적용(ParamsType = RelativeLayout.LayoutParams)

> 사용자 설정 메서드

getResources().getIdentifier(String name, String defType, String defPackage); : resourceId를 리턴함.

name: 파일이름 defType: 디렉토리이름 defPackage: 패키지 이름