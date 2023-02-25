# iOSInterviewquestions
iOS개발자들에게 필요한 자료들을 정리하고 있는 중입니다.

면접때 받은 질문이나 공부한내용들

수정해야할 내용이나 추가해야할 내용은 언제든지 PR날려주세요!

```
답이 적혀있지 않은 이유는 해당 내용을 암기식으로 외우기 보다 찾아보고 공부하면서 습득 하시는게 좋기때문입니다.
해당내용을 찾아보면서 관련된 내용들 까지 같이 공부하시면서 해당 내용을 본인의 것으로 얻으시기 바랍니다.
```

모두의 힘을 모아봅시다 👯‍♀️👯‍♂️
감사합니다:)

# Required
아래 내용들은 최대한 많이 공부해놓는것이 좋습니다 📝

+ 면접시기가 wwdc이후 (7월~11월)이라면 해당년도 wwdc세션들을 봐 두시면 매우매우매우 좋습니다.

[Apple All Videos](https://developer.apple.com/videos/all-videos/)

## iOS
- Bounds 와 Frame 의 차이점을 설명하시오.

Bounds와 Frame은 모두 CGRect 타입이며 origin 즉 원점을 나타내는 데이터와 size를 나타내는 데이터를 갖고있습니다.
Bounds는 자신만의 좌표시스템에서의 View의 위치와 크기 값이고 origin은 디폴트로 (0,0)으로 설정되어 있으며 주로 View내부에 그림을 그릴 때 (drawRect) 사용합니다.
Frame은 superView(한 단계 상위 뷰)의 좌표시스템안에서 view의 위치와 크기 값이고 주로 View의 위치나 크기를 설정하는 경우 사용합니다.

-------------
<br>

- 실제 디바이스가 없을 경우 개발 환경에서 할 수 있는 것과 없는 것을 설명하시오.


시뮬레이터는 Mac에서 실행되는 앱이기 때문에 CPU, 메모리 및 네트워크 연결을 비롯한 컴퓨터 리소스에 액세스할 수 있지만 실제 디바이스의 메모리 및 네트워크 속도와 다르기 때문에 실제 디바이스가 없다면 정확한 성능 테스트를 할 수 없습니다. 실제 맥에서는 부드럽게 실행되던 앱이 실제 디바이스로 테스트했을 때는 부드럽지 않을 수도 있습니다. 그리고 페이스 아이디를 이용할 때 직접 얼굴인식은 안되지만 인식됨, 안됨 처리를 해볼 수는 있습니다. 하드웨어 적으로는 가속도, 가압계, 주변광, GPS 등 여러 센서 기능을 이용할 수가 없습니다. 또한 카메라, 마이크, 전화 기능도 사용할 수 없고, 마우스로 시뮬레이터를 터치하기 때문에 두 손가락으로 하는 줌 아웃 등의 기능을 테스트 할 수 없습니다. API 측면에서도 Apple의 푸시 알림 받기와 보내기를 지원하지 않습니다.

-------------
<br>

- 앱의 콘텐츠나 데이터 자체를 저장/보관하는 특별한 객체를 무엇이라고 하는가?

Core data

-------------
<br>

- 앱 화면의 콘텐츠를 표시하는 로직과 관리를 담당하는 객체를 무엇이라고 하는가?

UIViewController
UIKit 앱의 뷰 계층 구조를 관리하는 객체이다
뷰의 사용자 상호 작용에 응답한다
전체 인터페이스의 레이아웃을 관리한다
앱에서 다른 ViewController를 포함한 다른객체들과 조정을 한다
데이터가 변경되면 뷰의 콘텐츠를 업데이트할 수 있다

-------------
<br>

- App thinning에 대해서 설명하시오.

디바이스에 애플리케이션이 설치될때, 앱스토어와 운영체제가 디바이스에 맞게 설치되도록 설치 최적화 기술을 의미한다. 최소한의 디스크 사용과 빠른 다운로드가 가능하다

1. 슬라이싱

앱이 지원하는 여러 디바이스에 각각의 조각 애플리케이션 번들 생성, 해당 디바이스에 적합한 조각을 전달에 설치한다.
개발자가 앱스토어 커넥트에 앱을 업로드 하면, 앱스토어에서 다양한 버전의 조각들을 생성하고 사용자가 가장 알맞는 조각을 다운로드 하게 해준다

2. 비트코드

기계 언어로 번역되기 전단계이다
비트코드를 사용해서 업로드 하면 애플에서 애플리케이션을 다시 컴파일해서 앱 바이너리 생성한다
비트코드를 사용하지 않아도, fat binary가 업로드 되기는 하지만 비트코드를 사용하면 다시 컴파일 할 때 최적화 할 수 있다

3. 주문형 리소스

필요할 때만 다운로드 받을 수 있다
예를 들어 체험판 -> 본판 or 게임에서 저레벨에서 고레벨로 갈 때

-------------
<br>

###
- 앱이 시작할 때 main.c 에 있는 UIApplicationMain 함수에 의해서 생성되는 객체는 무엇인가?

@UIApplicationMain: 코코아 터치 프레임워크에서 앱의 라이프 사이클을 시작하는 함수

앱 실행과정
object-c
1.앱이 실행되면서 맨 처음 main()함수가 실행된다
2.main()함수는 UIApplicationMain()함수를 호출한다
3.UIApplicationMain()함수가 UIApplication객체를 생성한다. 이 객체는 앱의 본체에 해당.
4.UIApplication객체는 info.plist 파일로부터 앱 구성에 필요한 정보들을 로드한다.
5.이벤트 루프 및 초기설정을 진행한다.
6.실행 완료 직전에 앱 델리게이트의 application(_:didFinishLaunchingWithOptions:)메소드가 호출된다.

swift : 스위프트는 main 함수가 없지만 @main 이라는 어노테이션 표기가 있다. 이 표기를 통해서 object-c의 1-5 과정이 대체된다

@main 어노테이션을 찾고 그 클래스를 실행한다
AppDelegate클래스의 application(:didFinishLaunchingWithOptions:)메소드를 호출한다(앱이 실행될때 처리할 내용이 있으면 여기에 작성)
이벤트루프 실행, 작성한 코드들이 실행
앱이 종료될때 앱에대한 메모리 제거를 위해서 pplicationWillTerminate(:)메소드를 호출(앱이 종료될떄 처리할 내용이 있으면 어기에 작성)

-------------
<br>

- @Main에 대해서 설명하시오.

@main은 프로그램 실행 시작 시 진입점으로 타입을 지정하기 위한 Swift 언어의 기능이다. 사용자는 탑 레벨의 코드를 작성하는 대신 @main단일 유형의 속성을 사용할 수 있고, 라이브러리와 프레임워크는 프로토콜이나 클래스 상속을 통해 맞춤형 진입점 동작을 제공할 수 있다. 

-------------
<br>

- 앱이 foreground에 있을 때와 background에 있을 때 어떤 제약사항이 있나요?

Foreground에 있을 때에는 메모리 및 기타 시스템 리소스에 대해서 background보다 높은 우선순위를 가지며 시스템은 이러한 리소스를 사용할 수 있도록 필요에 따라 background 앱을 종료합니다
Background에 있을 때에는 가능한 적은 메모리 공간을 사용해야하며 자원 할당에 있어 foreground 상태 보다 우선순위가 낮습니다

-------------
<br>

- 상태 변화에 따라 다른 동작을 처리하기 위한 앱델리게이트 메서드들을 설명하시오.

상태변화에 따른 앱딜리게이트 메서드는,

애플리케이션이 실행된 직후 사용자의 화면에 보여지기 직전에 호출 되는 application메서드가 있고,

애플리케이션이 최초 실행될 때 호출되는 application 메서드,


13.0이후 scenedelegate메서드로 바뀜..? (4가지)

애플리케이션이 InActive 상태로 전환되기 직전에 호출되는 applicationWillResignActive,

애플리케이션이 백그라운드 상태로 전환된 뒤 호출되는 applicationDidEnterBackground,

애플리케이션이 Active상태가 되기 전에 호출되는 applicationWillEnterForeground,

애플리케이션이 Active상태로 전환된 후 호출하는 applicationDidBecomeActive,

애플리케이션이 종료되기 직전에 호출되는 applicationWillTerminate메서드 등이 있습니다.

-------------
<br>

- 앱이 In-Active 상태가 되는 시나리오를 설명하시오.

전화나 메시지 같은 인터럽트가 발생하거나, 미리알림 같은 특정 알림창이 화면을 덮어서 앱이 실질적으로 event를 받지 못하는 상태 In-Active 상태가 된다.
앱을 처음켜거나, foreground에서 background, background에서 foreground 상태가 될 때도 in-Active 상태를 거쳐간다.

-------------
<br>

- scene delegate에 대해 설명하시오.

iOS13 이후 UI 생명주기에 관한 이벤트를 처리하기 위해 사용하는 객체입니다.
앱을 실행하면 UIKit이 일반적으로 UIScene의 서브클래스인  UIWindowScene 객체를 생성합니다.
즉,  SceneDelegate란 UI 상태에 따른 이벤트처리를 하기 위한 객체입니다.



-------------
<br>

- UIApplication 객체의 컨트롤러 역할은 어디에 구현해야 하는가?

UIApplicationMain 함수


-------------
<br>

- App의 Not running, Inactive, Active, Background, Suspended에 대해 설명하시오.

Not running은 앱이 실행되지 않은 상태를 말하고 Inactive는 app이 실행중이지만 사용자로부터 event를 받을 수 없는 상태입니다. Active는 app이 실제 실행중이고 사용자 event를 받아서 상호작용할 수 있는상태이고 background는 홈화면으로 나가거나 다른 app으로 전환되어 app이 보이지 않는 곳에서 코드를 실행하고 있는 상태입니다.suspend는 앱이 background상태이며 앱이 메모리에 남아 있긴하나 코드를 실행하고 있지 않은 상태입니다.

-------------
<br>

###
- NSOperationQueue 와 GCD Queue 의 차이점을 설명하시오.

NSOperationQueue

Objective-C 기반 고수준 API
GCD보다 약간의 오버헤드가 더 발생되고 느리다. But KVO 지원 및 작업취소등을 지원
다양한 작업들 중에서 의존성을 추가할 수 있다
재사용, 취소, 중지 가능하다
NSOperation을 만들어서 병렬 or 직렬로 스레드 풀을 사용가능하다.
GCD Queue

C기반 로우레벨의 API
Global Queue에서 QOS 우선순위를 줄 수 있다.
Main Queue: 메인 스레드에서 사용될 것 들을 처리, UI코드
Dispatch Queues: 디스패치 큐는 FIFO 순서로 작업을 실행시키는 역할을 담당
Serial Dispatch Queue: 시리얼 디스패치 큐는 한번에 한 작업만 실행
Concurrent Dispatch Queue: 컨커런트 디스패치 큐는 시작한 작업이 끝나는것을 기다리지 않고 가능한 많은 작업을 실행
Main Dispatch Queue: 앱의 메인 스레드에서 작업을 실행할 수있는 전역에서 사용가능한 시리얼 큐

-------------
<br>

- GCD API 동작 방식과 필요성에 대해 설명하시오.

GCD (Grand Central Dispatch)
백그라운드에서 스레드를 관리하면서 작업을 실행시키는 저수준 API를 제공하는 라이브러리

Dispatch Queue : FIFO 순서로 작업을 실행
Serial Dispatch Queue : 한 번에 한 작업만 실행
Concurrent Dispatch Queue : 작업이 끝나는 것을 기다리지 않고 가능한 많은 작업 실행 (병렬)
Main Dispatch Queue : 앱의 메인 스레드에서 작업할 수 있는 전역에서 사용 가능한 시리얼 큐
DispatchQueue Class
Task를 담아두면 선택된 스레드에서 실행

Serial Dispatch Queue : 등록된 작업을 한 번에 하나씩 처리한다. 처리 중인 작업이 완료되면 다음 작업을 실행한다.
Concurrent Dispatch Queue : 여러 작업을 동시에 처리한다.
앱이 실행될 때의 Queue
Main Queue : 메인 스레드(UI 스레드)에서 사용되는 Serial Queue. 모든 UI 처리는 메인 스레드에서 처리한다.
Global Queue : 편의상 사용할 수 있게 만들어 놓은 Concurrent Queue. 처리 우선순위를 위한 qos (quality of service) 파라미터를 제공해 병렬적으로 동시에 처리한다.
=> 작업 완료 순서를 정할 수는 없지만, 우선적으로 일을 처리하게 할 수는 있다.
sync : 동기
async : 비동기. 네트워크, 파일 I/O 등의 시간이 많이 소요되는 작업에 사용한다.
serial/concurrent와 sync/async는 관련이 없다

serial과 concurrent는 한 번에 하나만 작업하는지 여러개를 작업하는지의 차이이고,

sync와 async는 처리가 끝날 때까지 기다리는지 기다리지 않는지의 차이이다.

✨필요성
간단한 비동기 작업의 경우 NSOperationQueue보다 GCD를 쓰는 것이 구현이 쉽다.

NSOperationQueue보다 빠르고 오버헤드가 적기 때문에 복잡한 로직이 아니면 GCD를 사용하는 것이 편하다.

-------------
<br>

- Global DispatchQueue 의 Qos 에는 어떤 종류가 있는지, 각각 어떤 의미인지 설명하시오.

1. userInteractive

main thread에서 작업, 사용자 인터페이스(UI) 새로고침 또는 애니메이션 수행과 같이 사용자와 상호작용 하는 작업
작업이 신속하게 수행되지 않으면, UI가 중단된 상태로 표시될 수 있음
반응성(responsiveness)과 성능(performance)에 중점을 둡니다.
Duration of work to be performed - 순식간에 끝난다.(Work is virtually instantaneous.)

2. userInitiated

사용자가 시작한 작업이며, 저장된 문서를 열거나, 사용자 인터페이스에서 무언가를 클릭할 때 작업을 수행하는 것과 같은 즉각적인 결과가 필요
사용자 상호작용을 계속하려면 작업이 필요합니다. (The work is required in order to continue user interaction) 반응성과 성능에 중점을 둡니다.
Duration of work to be performed : 거의 순식간이며, 몇 초 또는 그 이하입니다.

3. default

QoS의 priority level은 user-initiated와 utility사이에
이 QoS는 개발자가 작업을 분류하는데 사용하기 위한 것이 아님, QoS정보가 할당되지 않은 작업은 Default로 처리되며 GCD global queue는 이 level(default)에서 실행됩니다

4. utility

작업을 완료하는 데 약간의 시간이 걸릴 수 있으며, 데이터 다운로드 또는 import와 같은 즉각적인 결과가 필요하지 않음
유틸리티 작업에는 일반적으로 사용자가 볼 수 있는 progress bar가 있음, 반응성, 성능 및 에너지 효율성 간에 균형을 유지하는 데 중점

5. background

백그라운드에서 작동하며, indexing, 동기화 및 백업과 같이 사용자가 볼 수 없는 작업
에너지 효율성에 중점
Duration of work to be performed : 작업은 분(minutes) 또는 시간(hour)과 같은 상당한 시간(significant time)이 걸림

6. unspecified

이는 QoS정보가 없음을 나타내며, 환경 QoS(environmental QoS)를 추론해야 한다는 단서를 시스템에 제공
쓰레드가 기존(legacy) API를 사용하는 경우, Unspecified QoS를 사용할 수 있으며, 이경우 쓰레드가 QoS를 벗어날 수 있음

-------------
<br>

###
- iOS 앱을 만들고, User Interface를 구성하는 데 필수적인 프레임워크 이름은 무엇인가?

cocoa touch framework 가 UIKit을 포함하는데 이 UIKit이 사용자 인터페이스를 구성하는데에 필수적입니다.

iOS기본구조

1. coaoa touch

앱의 다양한 기능구현에 필요
다양한 핵심프레임워크를 포함하는 최상위 레벨 프레임워크

2. media

그래픽 관련 서비스나 오디오나 비디오 같은 멀티미디어 관련 서비스 제공

3. core services

문자열 처리, 데이터 집합, 네트워크 등의 서비스 제공

4. core os

하드웨어와 네트워크 관련된 low-level의 서비스를 제공

-------------
<br>

- Foundation Kit은 무엇이고 포함되어 있는 클래스들은 어떤 것이 있는지 설명하시오.

Foundation Kit은 Cocoa Touch framework에 포함되어 있는 프레임워크 중 하나로 String, Int 등의 원시 데이터 타입과 컬렉션 타입 및 운영체제 서비스를 사용해 앱의 기본적인 기능을 관리하는 프레임워크 입니다.

iterator, jsonEncoder, jsonDecoder 과 같은 데이터 관련 클래스가 정의되어 있습니다.

iterator: 배열이나 그와 유사한 자료 구조의 내부의 요소를 순회(traversing)하는 객체이다.
jsonEncoder: 데이터 유형의 인스턴스에서 JSON 개체로 변환하는 객체
jsonDecoder: JSON 개체에서 데이터 유형의 인스턴스로 변환하는 객체

-------------
<br>

- Delegate란 무엇인지 설명하고, retain 되는지 안되는지 그 이유를 함께 설명하시오.

delegate란 객체 지향 프로그래밍에서 하나의 객체가 모든 일을 처리하는 것이 아니라 처리해야 할 일 중 일부를 다른 객체에게 넘기는 것을 의미한다.

retain(유지하다) : 메모리가 해제되지 않아서 낭비되는 현상을 의미 (Memory Leak, 메모리 누수)

Delegate는 객체 간의 작업이여서 참조 값을 사용하기 때문에 retain 현상이 일어난다.

<br>

해결 방법

weak : 약한 참조

unowned : 약한 참조이고 해제된 메모리 영역에 재접근하지 않는다는 확신이 있을 때

-------------
<br>

- NotificationCenter 동작 방식과 활용 방안에 대해 설명하시오.

NotificationCenter는 등록된 모든 Observer에게 정보를 전달하는 메커니즘입니다. observer는 notification들을 감지하고 있고 sender는 필요할 때 해당 observer에게 notification들을 보내주는 역할을 합니다. 옵저버를 등록하고 등록된 옵저버를 감시하면서 변경사항이 발생하면 등록된 옵저버에게 알려줍니다.

객체 A : listener

객체 B : sender

NotificationCenter

1. 객체 A는 객체 B의 어떠한 행위를 관찰하기 위해 NotificationCenter에 옵저버를 등록한다.

2. 옵저버에는 어떤 객체를 관찰할 것인지, 어떤 행위를 관찰할 것인지 등이 들어감

3. 객체 A가 어떠한 행위를 한다.

4. 객체 A는 알림을 생성하고 NotificationCenter에 post함

5. NotificationCenter는 객체 B에게 등록한 옵저버에 대한 알림이 발생했다고 알려줌

예를들어 한 화면에서 파일을 다운로드하고 다른 화면으로 넘어가도 다운로드 완료 알림 팝업을 띄울수 있습니다.


-------------
<br>

- UIKit 클래스들을 다룰 때 꼭 처리해야하는 애플리케이션 쓰레드 이름은 무엇인가?

main thread

-------------
<br>

- App Bundle의 구조와 역할에 대해 설명하시오.

애플리케이션 번들은 애플리케이션의 성공적인 작동에 필요한 모든것을 저장합니다.

애플리케이션 번들은 앱의 코드를 포함하고 있는 실행 가능한 파일인 my app,
앱을 표시하는 application icons,
bundle ID, 버전 번호 등 앱에 대한 구성 정보를 포함하고 있는 파일인 info.plist,
앱의 시작 인터페이스를 보여주는 이미지인 launch images,
앱 런치 시간에 앱을 로드하기 위한 기본 인터페이스 객체(App delegate 객체의 인스턴스)를 포함한 MainWindow.nib,
기본 설정을 구성하고, 표시할 프로퍼티 리스트와 기타 리소스 파일이 포함되어있는 Settings.bundle,
이미지나 사운드 및 애플리케이션에 필요한 기타 커스텀 데이터 파일로 구성된 커스텀 리소스 파일로 구성됩니다.

-------------
<br>

- 모든 View Controller 객체의 상위 클래스는 무엇이고 그 역할은 무엇인가?

-------------
<br>

- 자신만의 Custom View를 만들려면 어떻게 해야하는지 설명하시오.

-------------
<br>

- View 객체에 대해 설명하시오.

-------------
<br>

- UIView 에서 Layer 객체는 무엇이고 어떤 역할을 담당하는지 설명하시오.

-------------
<br>

- UIWindow 객체의 역할은 무엇인가?

-------------
<br>

- UINavigationController 의 역할이 무엇인지 설명하시오.

-------------
<br>

- TableView를 동작 방식과 화면에 Cell을 출력하기 위해 최소한 구현해야 하는 DataSource 메서드를 설명하시오.

<br>

- 하나의 View Controller 코드에서 여러 TableView Controller 역할을 해야 할 경우 어떻게 구분해서 구현해야 하는지 설명하시오.

<br>

- setNeedsLayout와 setNeedsDisplay의 차이에 대해 설명하시오.

<br>

- stackView의 장점과 단점에 대해서 설명하시오.

<br>

###

- NSCache와 딕셔너리로 캐시를 구성했을때의 차이를 설명하시오.

<br>

- URLSession에 대해서 설명하시오.

<br>

- prepareForReuse에 대해서 설명하시오.

<br>

- 다크모드를 지원하는 방법에 대해 설명하시오.

<br>

- ViewController의 생명주기를 설명하시오.

<br>

- TableView와 CollectionView의 차이점을 설명하시오.

<br>

## Autolayout

- 오토레이아웃을 코드로 작성하는 방법은 무엇인가? (3가지)

<br>

- hugging, resistance에 대해서 설명하시오.

<br>

- Intrinsic Size에 대해서 설명하시오.

<br>

- 스토리보드를 이용했을때의 장단점을 설명하시오.

<br>

- Safearea에 대해서 설명하시오.

<br>

- Left Constraint 와 Leading Constraint 의 차이점을 설명하시오.

<br>

## Swift

- struct와 class와 enum의 차이를 설명하시오.

<br>

- class의 성능을 향상 시킬수 있는 방법들을 나열해보시오.

<br>

- Copy On Write는 어떤 방식으로 동작하는지 설명하시오.

<br>

- Convenience init에 대해 설명하시오.

<br>

- AnyObject에 대해 설명하시오.

<br>

- Optional 이란 무엇인지 설명하시오.

<br>

- Struct 가 무엇이고 어떻게 사용하는지 설명하시오.

<br>

- Subscripts에 대해 설명하시오.

<br>

- String은 왜 subscript로 접근이 안되는지 설명하시오.

<br>

- instance 메서드와 class 메서드의 차이점을 설명하시오.

<br>

- class 메서드와 static 메서드의 차이점을 설명하시오.

<br>

- Delegate 패턴을 활용하는 경우를 예를 들어 설명하시오.

<br>

- Singleton 패턴을 활용하는 경우를 예를 들어 설명하시오.

<br>

- KVO 동작 방식에 대해 설명하시오.

<br>

- Delegates와 Notification 방식의 차이점에 대해 설명하시오.

<br>

- 멀티 쓰레드로 동작하는 앱을 작성하고 싶을 때 고려할 수 있는 방식들을 설명하시오.

<br>

- MVC 구조에 대해 블록 그림을 그리고, 각 역할과 흐름을 설명하시오.

<br>

- 프로토콜이란 무엇인지 설명하시오.

<br>

- Protocol Oriented Programming과 Object Oriented Programming의 차이점을 설명하시오.

<br>

- Hashable이 무엇이고, Equatable을 왜 상속해야 하는지 설명하시오.

<br>

- mutating 키워드에 대해 설명하시오.

<br>

- 탈출 클로저에 대하여 설명하시오.

<br>

- Extension에 대해 설명하시오.

<br>

- Extension 내부에서 함수를 override할 수 있는지 설명하시오.

<br>

- 접근 제어자의 종류엔 어떤게 있는지 설명하시오.

<br>

- defer란 무엇인지 설명하시오.

<br>

- defer가 호출되는 순서는 어떻게 되고, defer가 호출되지 않는 경우를 설명하시오.

<br>

- property wrapper에 대해서 설명하시오.

<br>

- Generic에 대해 설명하시오.

<br>

- some 키워드에 대해 설명하시오.

<br>

- Result타입에 대해 설명하시오.

<br>

- Codable에 대하여 설명하시오.

<br>

- Closure에 대하여 설명하시오.

<br>

- Closure와 함수와의 관계에 대해 설명하시오.

## ARC

- ARC란 무엇인지 설명하시오.

<br>

- Retain Count 방식에 대해 설명하시오.

<br>

- Strong 과 Weak 참조 방식에 대해 설명하시오.

<br>

- 순환 참조에 대하여 설명하시오.

<br>

- 강한 순환 참조 (Strong Reference Cycle) 는 어떤 경우에 발생하는지 설명하시오.

<br>

## Functional Programming

- 순수함수란 무엇인지 설명하시오.

<br>

- 함수형 프로그래밍이 무엇인지 설명하시오.

<br>

- 고차 함수가 무엇인지 설명하시오.

<br>

- Swift Standard Library의 map, filter, reduce, compactMap, flatMap에 대하여 설명하시오.

## Architecture

- MVVM, MVI, Ribs, VIP 등 자신이 알고있는 아키텍쳐를 설명하시오.

<br>

- 의존성 주입에 대하여 설명하시오.

<br>

## SwiftUI

- @State에 대해서 설명하시오.

<br>

## Combine

- PassthroughSubject에 대해서 설명하시오

<br>

- @Published에 대해서 설명하시오

<br>

- AnyCancellable에 대해서 설명하시오

<br>

- sink에 대해서 설명하시오

<br>

- throttle과 debounce의 차이점을 설명하시오.

<br>

- Data를 Binding 하는 방법에 대해서 설명하시오.

# Optional
아래부터는 추가로 공부를 하면 좋을 내용들입니다.

Objective-c나 rx는 회사, 팀마다 사용하는곳이 차이가있고 신입이나 주니어기준으로 필수라고 여겨지지않기에 옵셔널에 추가하였습니다.

## Rx

- Reactive Programming이 무엇인지 설명하시오.

<br>

- RxSwift를 왜 사용하는지 설명하시오.

<br>

- RxSwift의 단점을 설명하시오.

<br>

- RxSwift에서 Hot Observable과 Cold Observable의 차이를 설명하시오.

<br>

- Subject의 종류와 차이점에 대해 설명하시오.

<br>

- Subject와 Driver의 차이를 설명하시오.

<br>

- Single, Completable, Maybe의 차이점에 대해 설명하고, 언제 적용하면 좋을지 설명하시오.

## MRC

- ARC 대신 Manual Reference Count 방식으로 구현할 때 꼭 사용해야 하는 메서드들을 쓰고 역할을 설명하시오.

<br>

- retain 과 assign 의 차이점을 설명하시오.

<br>

- 특정 객체를 autorelease 하기 위해 필요한 사항과 과정을 설명하시오.

<br>

- Autorelease Pool을 사용해야 하는 상황을 두 가지 이상 예로 들어 설명하시오. 

<br>

- 다음 코드를 실행하면 어떤 일이 발생할까 추측해서 설명하시오.
Ball *ball = [[[[Ball alloc] init] autorelease] autorelease];

## Advanced

- method swizzling이 무엇이고, 어떨 때 사용하는지 설명하시오.

<br>

- NSCoder 클래스는 어떤 상황에서 어떻게 써야 하는지 설명하시오.

<br>

- Responder Chain 구조에 대해 설명하고, First Responder 역할에 대해 설명하시오.

<br>

- NSObject부터 UIButton 까지 상속 과정의 계층과 역할을 설명하시오.

<br>

- shallow copy와 deep copy의 차이점을 설명하시오.

<br>

- Push Notification 방식에 대해 설명하시오.

<br>

- Foundation 과 Core Foundation 프레임워크의 차이점을 설명하시오.

<br>

- NSURLConnection 에서 사용하는 Delegate 메서드들에 대해 설명하시오.

<br>

- Synchronous 방식과 Asynchronous 방식으로 URL Connection을 처리할 경우의 장단점을 비교하시오.

<br>

- Plist 파일 구조와 Plist 파일에 저장된 데이터를 다루기 적합한 클래스를 설명하시오.

<br>

- Core Data와 Sqlite 같은 데이터 베이스의 차이점을 설명하시오.

<br>

- JSON 데이터를 처리하는 방식과 파서, 객체 변환 방식에 대해 설명하시오.

<br>

- 웹 서버와 HTTP 연결을 사용해서 데이터를 주거나 받으려면 사용해야 하는 클래스와 동작을 설명하시오.

<br>

- Protocol에서는 왜 var만 되는지 설명하시요.

<br>

- DispatchQueue.main.sync를 사용하는 상황을 설명하시오.

<br>

- Run Loops에 대해 설명하시오.

## Objective-C

- Swift의 클로저와 Objective-C의 블록은 어떤 차이가 있는가?

<br>

- Mutable 객체과 Immutable 객체는 어떤것이 있는지 예를 들고, 차이점을 설명하시오.

<br>

- dynamic과 property 의미와 차이를 설명하시오.

<br>

- @property로 선언한 NSString* title 의 getter/setter 메서드를 구현해보시오.

<br>

- @property에서 atomic과 nonatomic 차이점을 설명하고, 어떤것이 안전한지, 어느것이 기본인지 설명하시오.

<br>

- @property로 선언한다는 것의 의미를 설명하고, .h에 넣을 경우와 .m에 넣을 경우 차이점을 설명하시오.

<br>

- performSelector:withObject:afterDelay: 메시지를 보내면 인자값의 객체는 retain되는가? 그 이유를 함께 설명하시오.

<br>

- Objective-C 에서 캡슐화된 데이터를 접근하기 위한 방법들을 설명하시오.

<br>

- Fast Enumeration 이란 무엇인지 설명하시오. 

<br>

- unnamed category 방식에 대해 설명하시오.

<br>

- Category 확장과 Subclass 확장의 차이점을 설명하시오.

<br>

- Category 방식에 대해 설명하시오.

<br>

- Objective-C 에서 Protocol 이란 무엇인지 설명하시오.

<br>

- Objective-C++ 방식이 무엇인지 설명하고, 어떤 경우 사용해야 하는지 설명하시오.

