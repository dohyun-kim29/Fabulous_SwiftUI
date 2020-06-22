# SwiftUI 기초

1. SwiftUI에 대하여

   - **"Less code, Better code. Everyone"**

     

   - Swift 기반의 **UI 프레임워크**

     

   - 기존의 명령형 대신 **선언형**으로 프로그래밍한다.

     

   - **Preview**를 통해 작업중인 코드의 결과물을 볼 수 있다.

     

   - 모든 애플 플랫폼 지원

     

2. SwiftUI의 4가지 원칙

   - **선언형**

     명령형 방식에서는 **각 과정을 어떻게 수행해야 할지** 에 초점을 맞추는 반면, 

     선언형 방식에서는 **정확히 무엇을 하고 싶은지** 를 정의한다.

     ```SwiftUI
     Button(action: {
     	print("Hello!")
     }) {
     Text("ByeBye!")
     .font(.title)
     .foregroundColor(.black)
     }
     ```

     코드가 기존의 방식에 비해 간결하다.

     

   - **자동화**

     가능한 많은 기능이 **자동으로 수행** 될수있게 제공

     매번 작성해야 했던 상용구 생략

     

   - **조합**

     뷰의 **조합과 분리를 간단히** 할 수 있게 제공

     복잡한 뷰 설계, 수정 / 특정뷰 **재사용 용이**

     뷰 프로토콜에 **다양한 공용 수식어** 사용 가능

     

   - **일관성**

     UI는 항상 **데이터에 동기화되어 일관성있게** 보여야 한다.

     SwiftUI에서는 **데이터가 변경되는 즉시 UI도 자동으로 갱신**된다.

     

   

3. 프로젝트 생성

   - 기존 Storyboard 가 아닌 **SwiftUI** 선택

     

   - ViewController.Swift 대신 **ContentView.Swift**파일이 생긴다.

     

   - 당연하게도, Main.storyboard 는 삭제되었다.

     

   - Preview만을 위한 에셋인 **Preview Assets.xcassets** 가 추가되었다.

     

   - Preview 단축키는 Option + Command + P 이다.

