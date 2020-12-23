# vrclass-app-sdk
- 권장 Unity 버전및 언어 : Unity 2018.2.20f1, C#
- 클래스브이 VR Class App와 체험 앱 간 연동 및 메시지 전달 방법에 대한 가이드입니다.
- SDK는 수정 및 기능 추가 등의 업데이트가 될 수 있습니다.

# 선행 작업

1.	using ClassV_SDK 로 namespace ClassV_SDK를 선언합니다.
2.	제일 먼저 선행되어야 할 작업은 Prefabs 폴더 안 SDK_Manager_student를 씬에 임포트 한 뒤 ExperienceAppManager의 StartExperienceApp()를 호출해주세요. SDK 사용을 위한 인증 코드를 전달받고, 앱이 정상적으로 실행되었음을 서버에 알리는 작업입니다.

# 메시지 전달받기
메시지는 폴링 방식으로 2초 간격으로 json을 호출하여 서버에서 선생님이 보낸 메시지를 가져옵니다. 이러한 메시지 호출 작업을 시작하려면 GetMessageManager.cs의 GetMessage()를 호출하세요.
메시지가 전달된 시간과 현재 시간을 비교하여 3초 이내의 메시지는 수신하여 학생들에게 보여줘야합니다. 3초 이내에 전달된 메시지가 있다면 GetMessageManager.ShowMessageflag 가 true로 변경됩니다. 이때 팝업창을 띄워 학생들에게 메시지를 노출시켜주세요. 
Demo 폴더의 Student 씬에 샘플이 구현되어 있습니다.
 * 향후 FCM등의 Push 방식으로 변경 예정에 있습니다.

# 앱 종료 및 클래스브이로 복귀
선생님이 종료 메시지를 보내면 체험 앱이 종료되고 클래스브이로 복귀합니다. 
선생님이 종료 메시지를 보내지 않았지만 클래스브이로 복귀하려면 ExperienceAppManager.cs의ExitExperienceApp()을 호출해주세요.
