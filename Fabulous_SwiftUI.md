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

     

   

4. Content View 살펴보기

   - ContentView.Swift에 있는 **ContentView_Previews** 구조체는 프리뷰를 위한 용도이다.

     

   - ContentView의 기본 코드

   - ```SwiftUI
     struct ContentView: View {
     	var body: some View {
     		Text("Hello World")
     	}
     }
     ```

     

   - View 타입은 **프로토콜**로 선언되어았다

   - View 프로토콜

   - ````SwiftUI
     protocol View {
     	associatedtype Body: View
     	var body: Self.Body { get }
     }
     ````

   - 재귀호출이 일어나지 않게 컨테이너 뷰에는 **Never** 타입이 사용된다.

     

     

5. 텍스트 수정

   - ```SwiftUI
     var body: some View {
     	Text("원하는 텍스트를 입력해주세요")
     }
     ```

   - Preview에 실시간으로 반영된다.

     

   - 여러 **수식어**를 사용하여 다양한 효과를 적용시킬 수 있다

   - ```SwiftUI
     Text("Hello SwiftUI")
     .font(.largeTiTle)
     .foregrounColor(.red)
     ```

     

   - SwiftUI의 모든 수식어는 자신의타입이나 뷰 프로토콜을 반환하도록 설계되어 **연쇄적인 메소드 호출(메소드 체이닝)**이 가능하다.

     

   - 이러한 작업을 코드 입력이 아닌 **라이브러리** 를 사용하여 수정할 수 있다. (Xcode툴바에 위치)

   - +Attributes inspector 탭에서도 가능.

     

   - 텍스트 위에 커서를 올리고 Commend키를 누르면 다양한 액션 메뉴를 확인할 수 있다.

# 뷰 구성하기

 1. 텍스트

    - 단어 그대로 화면에 **원하는 문자열**을 표현하는 뷰

      

    - SwiftUI에서는 **버튼**, **피커**, **토글** 등 다양한 뷰에서 텍스트를 사용하는 경우가 많아, **UILabel보다 사용 범위가 넓다**.

      

    - **수식어를 적용시킬 때 순서가 중요하다**

    - **공용 수식어** 를 적용하기 전에 각 뷰가 가진 **전용 수식어** 를 구분해서 **우선 적용** 해야한다.

    - 수식어의 반환타입을 살펴보면 알 수 있다.

    - **수식어는 이전에 뷰를 감싼 새로운 뷰를 만들어 내고, 그다음 수식어는 다시 그 뷰를 감싼다.**

      

      

    2. 이미지

    - UIImage 객체를 만들어줄 **필요가 없다**.

    - ```SwiftUI
      Image("불러올 이미지 이름")
      ```

      

    - **.frame** 수식어를 사용하여 뷰가 차지하는 공간을 바꿔줄 수 있다.

    - ```SwiftUI
      Image("SwiftUI").frame(width:" 50, height: 50")
      ```

    - .frame 수식어보다 먼저 적용되는 **.resizable** 메소드를 사용하여 이미지 크기를 번경해줄 수 있다.

    - ```SwiftUI
       .resizable(capInsets: .init(top: 0, leading: 0, bottom: 0, trailing: 0))
      ```

      

    - **.scaledToFit** 수식어와 **.sacledToFill** 수식어는 각각 비율을 유지한채로 가능한한 최대로 늘려주는데 ~fit수식어는 최대 크기를 주어진 공간 내에서 처리하고, ~Fill 수식어는 화면 밖을 넘어나 더 크게 표현될 수 있다. 

      

    - 이미지의 비율에 대해 좀더 세부적인 조정이 필요하다면 **aspectRatio** 수식어를 사용해야 한다.

    - ```SwiftUI
      .aspectRatio(CGSize(width: 1.6, height: 1), contentMode: fit)
      //contentMode를 적용하고, 너비가 높이에 비해 1.6배의 비율을 가지도록 한다.
      ```

      

    - **ClipShape** 수식어를 이용해 원하는 모양으로 자를 수 있다.

    - ```SwiftUI
      .clipShape(Circle())
      ```

      

    - 이미지에는 **template**와 **original** 두개의 렌더링 모드가 사용된다.

    - **template** - 불투명 영역이 가진 색을 무시하고 원하는 색으로 번경해 사용 가능

    - **original** - 항상 이미지 본래의 색을 유지합니다.

    - ```SwiftUI
      .randeringMode(.original)
      ```

    - **SF Symblos**이라는 애플에서 제공하는 이미지를 사용할 수도 있다.

      

      

    3. 뷰 레이아웃

    - **스택** 은 뷰를 배치하는데 쓰는 컨테이너 뷰이다.

      

    - 가로 방향으로 뷰를 배열하는 **HStack** 

    - 세로 방향으로 배열하는 **VStack**

    - 뷰 계층을 겹겹이 쌓아 올리는 **ZStack** 이 있다. 

      

    - 프로퍼티에는 반드시 하나의 값만 반환해야하기 때문에 이러한 컨테이너 뷰를 사용한다.

    - ```SwiftUI
      Hstack {
      	Rectangle()
      		.fill(Color.green)
      		.frame(width: 150, height: 150)
      	Rectangle()
      		.fill(Color.yellow)
      		.frame(width: 150, height: 150)
      }
      ```

      

    - **spacing**의 값을 명시적으로 지정해 줌으로써 원하는 간격만큼 떨어지게 할 수 있다.

    - ```SwiftUI
      Hstack(spacing: 0) {...}
      ```

      

    - 객체를 정렬해주는 **Alignment** 매개변수는 각 스택마다 서로 **다른** 값을 받아들인다.

    - 예를 들면, 가로 방향으로 배열해주는 HStack은 세로 방향에 대한 정렬값을 주어야 한다.

    - ```SwiftUI
      Hstack(alignment: .top) {
      	Rectangle().fill(Color.green).frame(width: 150, height: 150)
      	Rectangle().fill(Color.yellow)
      		.frame(width: 150, height: 550)
      }
      ```

      
      
    - **스택에도 뷰 프로토콜이 가진 수식어를 사용할 수 있다.**

    - ```SwiftUI
      HStack {
      	Text("HStack").font(.title).foregroundColor(Color.blue)
      	Text()
      }
      ```

      
      
    - **Spacer** 는 뷰 사이의 **간격을 설정**하거나 **뷰의 크기를 확장**할 용도로 사용되는 **레이아웃**을 위한 뷰이다.

      

    - 스택 **외부** 에서 사용될 경우 부모 뷰가 제공하는 공간 내에서 **가능한 최대** 의 크기로 확장된다. (시각적 요소 적용 가능)

      

    - ZStack에서 사용될 경우 스택 외부에서 사용된 Spacer와 **동일하게 취급**.

      

    - HStack이나 VStack에서 사용될 경우 시각적 요소가 **제외**되고, 단순히 **공간을 차지하기 위한 역할**로만 기능.

    - ```SwiftUI
      HStack {
      	Spacer()
      	Text("Spacer").font(.title).background(Color.yellow)
      }
      ```

      

    - Spacer의 크기를 제한하고 싶다면 **frame** 수식어를 사용.

    - ```SwiftUI
      Spacer().frame(width: 100)
      ```

      

    - **minlength** 를 사용하면 **최소 간격**을 지정할 수 있다.

    - ```SwiftUI
      Spacer(minLength: 100)
      ```

      

