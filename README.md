# Power_Platform_Attendance
## 서문
아직도 참석자 명단 작성을 수기로 한다고요?
동아리 행사 시, 종이에 수기로 명단 작성하는 것 불편하지 않으신가요?
동아리원 명단 엑셀만 있다면 신청자에게 자동으로 출석 QR 코드 발송해주고, 입장하면서 스캔만 해주면 자동으로 참석자 명단이 만들어진다는 사실!

## 파워오토메이트와 파워앱스
노코드/로우코드(no-code/low-code) 툴인 파워앱스(Power Apps)와 파워오토메이트(Power Automate)를 활용하여 출석 QR코드를 참가자에게 자동으로 배부하고(Power Automate), QR코드 체크하는 앱을 만들어(Power Apps) 보겠습니다. 코드를 거의 작성하지 않고 어느정도까지 자동화가 되는지 새로운 노코드/로우코드의 세계를 맛보세요.

## 핸즈온 주제
오늘의 핸즈온은 크게 [section01. '파워오토메이트'를 통해 QR생성 후, 이메일로 자동 배포하기](https://github.com/g1nya2/Power_Platform_Attendance/tree/main/Start-here/section01) 와 [section02. '파워앱스'로 QR체크인 앱 만들기](https://github.com/g1nya2/Power_Platform_Attendance/tree/main/Start-here/section02) 두가지 내용으로 구성되어있습니다. 이를 통해 더이상 수기로 참석자 명단 작성하지말고, 참석자 명단을 자동으로 받는 방법을 배워보세요.

여기서부터 시작하세요 : [Start-here](https://github.com/g1nya2/Power_Platform_Attendance/tree/main/Start-here)

## 준비물 및 참고할 사이트
### 1. 엑셀 파일 , SharePoint List
이번 핸즈온에서 사용할 파일은 '엑셀' 파일입니다. 보통 동아리원 명단을 엑셀로 가지고 있는 경우가 많아, 엑셀 파일을 바탕으로 하였습니다.

section01 실습에 사용할 파일: [동아리원 명단](https://github.com/g1nya2/Power_Platform_Attendance/blob/main/%EB%8F%99%EC%95%84%EB%A6%AC%EC%9B%90%EB%AA%85%EB%8B%A8.xlsx) <- 다운받으세요.

section02 실습에 사용할 파일 :[동아리원 명단2](https://github.com/g1nya2/Power_Platform_Attendance/blob/main/%EB%8F%99%EC%95%84%EB%A6%AC%EC%9B%90%EB%AA%85%EB%8B%A82.xlsx) <- 다운받으세요.
#### 다운받은 엑셀파일에는 이메일이 임의의 값으로 지정되어있으니 실습전에 본인 이메일로 바꿔서 작성해주시면 됩니다. 사전에 이 작업부터 해주세요.

### 2. QR 코드 생성
오픈 소스로 QR를 생성하는 곳이 있습니다. `https://quickchart.io/`는 오픈소스로 차트 이미지를 만들어 주는 곳인데, 이 중 [QR코드 생성 API](https://quickchart.io/documentation/qr-codes/)가 있어, 이를 활용하여 QR 생성합니다.
```
https://quickchart.io/qr?text=홍길동|율도국
```
위와 같이 '홍길동'과 '율도국'을 파이프(|)로 병합한 값을 QR코드로 생성해줍니다. 위 주소를 복사해서 주소창에 입력하면 QR코드를 확인할 수 있습니다.

### 3. Power Apps 모바일 앱 내려받기
실습을 위해 모바일용 Power Apps를 내려받아야합니다. 핸드폰으로 이후 QR 체크인을 하는데에 쓰입니다.

