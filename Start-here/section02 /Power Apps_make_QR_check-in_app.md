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
![스크린샷 2024-03-29 040036](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/3c996491-679a-4282-b773-24ffdadb54be)
<br/><br/>
`+ 새 화면`을 선택한 후, `비어있음`을 선택하여 스크린을 만들 수 있습니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-29 040126](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/e372c886-295e-4c17-a85a-adff6de915e6)
<br/><br/>
위 과정을 통해 스크린을 총 2개 만들어주세요.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-29 040151](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/63e6d600-ca25-450a-90f6-3f6d8b5e5abc)
<br/><br/>
**Screen1**과 **Screan2**를 각각 `Home`과 `QRScan`으로 이름을 바꿔줍니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-29 040202](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/46bea62f-bd81-43a0-b15b-805b93585d74)
<br/><br/>
가장 위에 위치한 스크린이 앱을 실행했을 때 첫 화면이 되기 때문에'Home' 스크린을 가장 위로 올리는 작업을 해줍니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-29 040230](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/485bd5ca-e58c-484b-99e5-67b036eab4d6)
<br/><br/>
가장 위에다가 Home 스크린을 둔 것을 확인할 수 있습니다.
<br/><br/>
<br/><br/>
## 5. Home 스크린에 미디어 추가 및 버튼 추가
준비사항: 앱의 Home Screen에 추가할 이미지 파일을 내려받아주세요. [Home Screen용 이미지 파일 내려받기](https://github.com/g1nya2/Power_Platf므로, 여기서 name에 해당하는 값을 추출해야 합니다.
> - QR 코드를 스캔한 후, 해당 URL에서 name 값을 추출하는 방법은 다음과 같습니다:
> - QR 코드 스캔 결과를 BarcodeReader1.Barcodes로 가져옵니다.
> - 이후 First(BarcodeReader1.Barcodes).Value를 사용하여 name 값을 추출합니다.
> 2. Text Label에 값 표시:
> - 추출한 name 값을 vNameValue라는 변수에 저장합니다.
> -Text Label인 vName에서 vNameValue 값을 읽어 표시합니다.
<br/><br/>
결론적으로 **OnScan**모드에 작성할 함수는 아래와 같습니다.
```
// OnScan 이벤트에서 호출되는 함수
// QR 코드 스캔 결과에서 'name' 값을 추출하여 Text Label에 표시
ClearCollect(
    colBarcodes, // 임시 컬렉션 생성
    BarcodeReader1.Barcodes // QR 코드 스캔 결과 가져오기
);

// 'name' 값을 추출하여 변수에 저장
Set(
    vNameValue,
    First(Split(First(BarcodeReader1.Barcodes).Value, "|")).Value
);

// Text Label에 저장된 값 표시
UpdateContext({vName: vNameValue})
```
<br/><br/>
<br/><br/>







