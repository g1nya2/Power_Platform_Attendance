# Power Apps로 QR 체크인 앱 만들기
## 1. SharePoint로 이동하기
먼저, [Microsoft 365](https://www.microsoft365.com/) 에 들어가서 로그인 해줍니다.
<br/><br/>
![스크린샷 2024-03-28 133322](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/ebc816b3-4995-42f9-9e25-3d7f56fcbb16)
<br/><br/>
로그인 한 후 왼편의 '모든 앱(Apps)'를 눌러 이동합니다.
가운데에 'SharePoint'가 보이시죠? 이걸 클릭합니다.
<br/><br/>
<br/><br/>
## 2. SharePoint List 만들기
![스크린샷 2024-03-28 133744](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/7b3b0299-80c7-4994-831f-80f66320b45d)
<br/><br/>
SharePoint에 접속하시면 왼편에 메뉴들이 나와 있습니다.
거기서 목록(List)를 만들어 보겠습니다.
다음으로 목록(List)를 눌러 새로운 목록(List)를 만듭니다.
동그라미 안에 `+` 모양의 메뉴를 누릅니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-28 134122](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/cb3fa093-5adc-48f6-af83-99c836f17308)
<br/><br/>
이번 핸즈온에서는 미리 내려받은 파일을 가져오는 방법으로 하겠습니다. 그리과 같이 `From Excel`를 눌러 미리 내려받은 [동아리원 명단2](https://github.com/g1nya2/Power_Platform_Attendance/blob/main/%EB%8F%99%EC%95%84%EB%A6%AC%EC%9B%90%EB%AA%85%EB%8B%A82.xlsx) 파일을 업로드 해줍니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-28 134208](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/cb305e42-70c5-464b-bc1e-d76f3bf86315)
<br/><br/>
**파일업로드**를 눌러 내려받은 파일[동아리원 명단2](https://github.com/g1nya2/Power_Platform_Attendance/blob/main/%EB%8F%99%EC%95%84%EB%A6%AC%EC%9B%90%EB%AA%85%EB%8B%A82.xlsx)을 업로드 합니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-29 035550](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/39d5ed88-f068-4008-a222-27fdaf086632)
<br/><br/>
일반 엑셀 파일을 가져오는 경우에는 각 컬럼별 속성(붉은 색 테두리 쳐둔 부분)을 잘 확인하셔야 합니다.

출석여부를 다루는 Attendance 컬럼은 **선택항목**로 해둔 점을 눈여겨 봐주세요.
'다음(Next)'를 눌러 SharePoint List를 만듭니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-29 035658](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/86aaf178-af4f-4bc4-8cb9-5d09fa770bab)
<br/><br/>
이름은 `WebinarBookingList_01`로 해주고, `내목록`에 저장하고 만들어줍니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-29 035751](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/8e8138e4-f8c6-4b40-8f09-f091218dac3a)
![스크린샷 2024-03-29 035822](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/fbd703ab-8771-4fd4-95d5-ce45953846cc)
<br/><br/>
Attendance 라는 컬럼이 Choice 이기 때문에 나중에 출석체크를 확인할 때 Boolean으로 처리가 어렵습니다. 그래서 `Attendance_Status`라는 '예/아니요' 타입의 컬럼을 추가로 만듭니다.

나중에 출석체크할 때 토글로 사용할 계획입니다.
<br/><br/>
<br/><br/>
## 3. SharePoint List에서 앱 만들기
이제 앱을 만들어 봅시다.
![스크린샷 2024-03-29 035901](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/6bbacab8-fe67-42af-97bd-5716ea5f3830)
<br/><br/>
목록(list) 위에 있는 메뉴에서 **"Integrate > Power Apps > Create an app"** 순서로 앱을 만듭니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-29 040005](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/ad26d6d9-44ac-44ea-bf1d-004e8234b67a)
<br/><br/>
조금 기다리면 만들어집니다.
이렇게 만들어진 곳을 '캔버스(Canvas)'라고 합니다. 그림을 그리는 것처럼 앱을 만들 수 있다는 뜻이겠죠? 
<br/><br/>
<br/><br/>
## 4. 앱에 새로운 스크린 만들기


