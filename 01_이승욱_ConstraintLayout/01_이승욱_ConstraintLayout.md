# ConstraintLayout
## ConstraintLayout 장점
- 단순한 계층 구조로 만들어낼 수 있다
- 새로운 버전 나와도 여러분에 코드에는 영향을 미치지 않는다.
- 새 버전을 내더라도 개발자들의 코드가 에러를 낼까봐 걱정하지 않아도 됩니다.
- 매우  재미있는 레이아웃입니다.
## ConstraintLayout vs RelativeLayout
- onstraintLayout은 RelativeLayout과 유사하며, 안드로이드 스튜디오 레이아웃 편집기에서 ConstraintLayout의 모든 기능을 사용할 수 있습니다.
##  side Constraint
- side constraint를 사용하면 RelativeLayout과 유사하게 한쪽 끝을 기준으로 위젯이 목표물을 향하도록 움직일 수 있습니다. 정렬을 위해 사용하는 기준선도 있습니다. 기준선은 텍스트의 바닥이므로 다른 크기의 두 버튼을 정렬시키되, 텍스트는 수직으로 만들 수도 있습니다. XML에서 이런 모습을 간단히 만들 수 있는데요. constraint를 시작하는 위치에서부터 ConstraintLayout을 시작하고 대상 constraint를 설정하면 됩니다
- end 와 start 를 사용하는 이유는 다른 나라들은 글을 오른쪽부터 쓰는 나라도 있기때문에 통일하기 위해서만들었습니다. 
## Center Constraint
### center
- 한 위젯의 왼쪽과 오른쪽에 두 개의 constraint를 설정하기위해 사용된다.
- bias라는 개념이 있어서 기본 값은 50%이고 위젯의 중앙이 됩니다. 이 값을 변경해서 위치를 조정할 수 있고 UI를 좀 더 유연하게 만들 수 있습니다.
### Match Constraint
- Wrap Content나 고정 크기를 사용하는 대신 linear layout처럼 zero DP를 넣고 사용합니다. 이 경우 constraint에 맞게 위젯의 크기가 정해집니다. 위젯이 Match Constraint를 사용해서 Wrap Content가 되면 크기가 늘어납니다. 마진을 지정해서 크기가 마진만큼 작아지게 할 수도 있습니다.
###  Ratio
- Wrap Content나 고정 크기를 사용하는 대신 linear layout처럼 zero DP를 넣고 사용합니다. 이 경우 constraint에 맞게 위젯의 크기가 정해집니다. 위젯이 Match Constraint를 사용해서 Wrap Content가 되면 크기가 늘어납니다. 마진을 지정해서 크기가 마진만큼 작아지게 할 수도 있습니다.
## chain
- Chain 제약은 여러개의 뷰를 묶어 어떻게 공간에 배치할지를 정하는 조건이다.
-  -  speard : 기본적인 배치이다. `layout_constraintVertical_weight` / `layout_constraintHorizontal_weight` 을 이용하면 LinearLayout의 layout_weight효과를 낼 수 있다.
  -   spread_inside : 공간의 가장자리에 첫번째 부와 마지막 뷰가 배치되고, 남은 사이공간에 나머지 뷰들이 배치된다.
  -   packed : 묶인 모든 뷰들이 공간의 가운데에 배치된다. bias 속성과 함꼐 사용하면 위치를 조절할 수 있다
## Guideline
- UI를 만드는데 도움이 되기 위해 Guideline을 만들었습니다.
- Guideline의 경우 마지막 패스에서 완전히 사라지고 레이아웃도 되지 않습니다.
- - 1.  “Begin/Start” 가이드라인 - 화면 시작으로부터 오프셋으로 지정합니다.
  - 2.  “Matching/End” 가이드라인 - 화면 끝으로부터 오프셋으로 지정합니다.
  - 3.  “Percent” 가이드라인 - 화면의의 일정 비율로 가이드라인의 위치를 지정합니다.
##참조자료
- [ConstraintLayou](https://github.com/GramDefined/Study/blob/master/01_%EC%9D%B4%EC%8A%B9%EC%9A%B1_ConstraintLayout/ConstraintLayout_%EC%9D%B4%EC%8A%B9%EC%9A%B1.pptx)
