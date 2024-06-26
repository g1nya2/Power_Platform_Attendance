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
준비사항: 앱의 Home Screen에 추가할 이미지 파일을 내려받아주세요. [Home Screen용 이미지 파일 내려받기](https://github.com/g1nya2/Power_Platform_Attendance/blob/main/QR%20%EC%8A%A4%EC%BA%90%EB%84%88%EC%95%B1%20%EC%82%AC%EC%A7%84.png)

![스크린샷 2024-03-29 040304](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/4fe89175-6e99-4737-877f-25ddc4474c17)
<br/><br/>
Power Apps Canvas의 왼편 메뉴 가운데 Media(이미지)를 선택한 후에 내려받은 이미지 파일을 `업로드`를 눌러 해당 Media에 올립니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-29 040325](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/01b07ab8-524c-4c7d-af76-72383a2fc2c6)
<br/><br/>
이미지 파일을 올린 이후 스크린에 끌어다가 배치하거나, `캔버스에 추가`버튼을 통해 배치해줍니다.
크기 자유롭게 조정하시고, 위치 적절한 곳에 자유롭게 배치하시면 됩니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-29 040352](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/9f776968-edc0-418f-a5cf-5b37ea9f898d)
<br/><br/>
이렇게 확인되셨나요?
<br/><br/>
<br/><br/>
![스크린샷 2024-03-29 040424](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/2c13341b-7691-4a34-929f-3ce8b6816bdc)
<br/><br/>
이제 버튼을 추가해볼겁니다.
`+`를 누른후, `버튼`을 검색하고, 아래 `버튼`을 선택합니다. 버튼을 **2개** 추가해줄거라 2번해주시면 됩니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-29 040446](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/40345bb2-0d9e-4024-ac70-6215af9ac4f4)
<br/><br/>
위 사진과 같이 적절한 위치에 버튼을 배치해주세요.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-29 040644](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/ac38ebc9-e9e2-402d-b434-7b39f549830a)
<br/><br/>
먼저, 첫번째 버튼을 `명단확인`으로 텍스트를 바꿔주고, 함수값에 
```
Navigate(BrowseScreen1)
```
이라고 작성해줍니다.
<br/><br/>
> Navigate 함수를 쓰면 버튼을 눌렀을때 해당 스크린으로 이동할 수 있습니다.

<br/><br/>
<br/><br/>
![스크린샷 2024-03-29 040725](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/c3c18e5b-717b-492e-b4d9-709e565fa1c6)
<br/><br/>
마찬가지로 두번째 버튼을 `QR스캔`으로 텍스트를 바꿔주고, 함수값에 
```
Navigate(QRScan)
```
이라고 작성해줍니다.
<br/><br/>
> Navigate 함수를 쓰면 버튼을 눌렀을때 해당 스크린으로 이동할 수 있습니다.
<br/><br/>
<br/><br/>
## 6. Home 스크린에 미디어 추가 및 버튼 추가
BrowseScreen1과 QRScan으로 이동하는 버튼을 Home에서 만들었으니 각 스크린에서 Home으로 가는 기능도 추가해야겠죠?
<br/><br/>
![스크린샷 2024-03-29 040842](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/f8e4f7c3-d0c4-43a7-b800-9f97a95e5be7)
<br/><br/>
`+`를 선택후, 홈을 검색한다음 `홈`을 선택하면 홈으로 가는 아이콘을 추가할 수 있습니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-29 041054](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/64e216ea-a912-440a-8bb0-6e450c721c0b)
<br/><br/>
위처럼 아이콘 색을 바꿀 수 있고, 홈으로 이동해야하기 때문에 함수에
```
Navigate(Home)
```
을 작성해줍니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-29 041131](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/b6d5b945-cf9b-4126-8712-0882c2436fd4)
<br/><br/>
마찬가지로 QRScan스크린에도 위 과정을 통해 홈으로 가는 아이콘을 추가해줍니다.
<br/><br/>
<br/><br/>
## 7. 바코드 판독기 추가하기
![스크린샷 2024-03-29 041441](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/237452b5-8f20-41f8-8696-1a0719b8330b)
<br/><br/>
QRScan 스크린에서 `+삽입` 선택 후, 바코드를 검색하면 나오는 `바코드 판독기`를 선택해줍니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-29 041538](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/f3360ff4-472f-4645-b63b-08da268b10fe)
<br/><br/>
텍스트를 `QR코드 스캔`으로 바꿔줍니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-29 041809](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/b10fbcfe-5964-43ba-a61d-ca6cb43f6bb7)
Power Apps에서 Barcode Reader 기능을 활용하여 QR 코드에서 일부 값을 추출하고 해당 값을 Text Label에 표시하는 함수를 만들어줍니다.
> 1. QR 코드 값 추출:
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

## 8. QR 코드 스캔한 값 확인하기
Text Label을 5개 추가한 후 '이름'과 '소속'을 각각 키(key)와 값(value)으로 나타낼 수 있게 합니다.
<br/><br/>
![스크린샷 2024-03-29 042153](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/d6af980f-c2a5-4df3-93c8-2d95527fec23)
<br/><br/>
QRScan 스크린에서 `+`를 누르고, '텍스트'를 검색 후 `텍스트 레이블`을 선택하여 추가해줍니다. 총 6번을 해서 각각 위 사진처럼 배치해줍니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-29 042453](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/e6bcc021-8474-4577-8362-e9732c5cb4de)
<br/><br/>
각각 레이블의 이름을 인식하기 쉽게 잘 바꾸어줍니다.
1. 이름을 표시하기 위해 'lblName'이라고 이름짓고,
2. QR Scan을 통해 가져온 값 가운데 이름을 담기위해 'vName'이라고 이름짓습니다.
3. 'vName'에는 Text Label의 "Text"에 스캔해서 취득한 "이름"을 나타내게 할 생각입니다.
4. 동명이인이 아닌 걸 확인하기 위해 소속을 표시하려고 'lblOrg'와 'vOrg'로 이름 짓습니다. 
5. 마지막 출석상태 라벨은 그냥 자유롭게 지어주시면 됩니다. 저는 'check'라고 적었네요
<br/><br/>
<br/><br/>
![스크린샷 2024-03-29 042543](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/00d6b191-bd20-4377-89b3-b0a3e0309c33)
<br/><br/>
이렇게 될 수 있겠네요..!
이제 뭐가 뭔지 인식하기 쉽겠죠?

> 주의: 실습은 이름을 ID처럼 사용하고 있는데, 동명이인인 경우에는 실제 문제가 될 수 있습니다. 같은 이름인 사람도 따로 구분할 수 있는 ID를 부여해서(가령 행사 신청시 'webinar01'과 같이 고유한 번호를 부여해서) 다른 사람과 구분하는 것이 매우 중요합니다.

<br/><br/>
<br/><br/>
![스크린샷 2024-03-29 042720](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/40ce6305-280f-453c-b41f-c637959427b8)
<br/><br/>
`vName`에 Text Label의 "Text"에 스캔해서 취득한 "이름"을 나타내게 할 생각입니다.
따라서, 스캔할 때 저장해둔 변수 "vNameValue"만 입력하면 끝납니다. 함수에
```
vNameValue
```
라고 입력해주시면 됩니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-29 043141](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/5a747a68-f0bf-499a-9da6-f9133f9eae4e)
<br/><br/>
'vOrg'는 Lookup 함수를 사용해서 QR코드를 스캔해서 가져온 이름에 해당하는 사람의 소속을 가져옵니다.
vOrg는 "Text"의 값을 스캔한 사람의 이름을 기준으로 소속을 가져와야 하므로 "Text" 상태의 함수를 LookUp을 사용해서 가져옵니다. 함수에 아래와 같이 적어주면 됩니다.
```
LookUp(WebinarBookingList_01, Title = vNameValue, organization)
```
<br/><br/>
<br/><br/>
## 9. QR 코드 스캔한 사람의 출석상태 체크
Toggle 버튼으로 손쉽게 출석여부를 확인하고 상태값을 업데이트 합니다. 
![스크린샷 2024-03-29 043231](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/e9a2cc06-7dae-4e8b-9239-8ddcac8a331c)
<br/><br/>
`+`를 선택하고 토글을 검색한 후 `토글`을 눌러줍니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-29 043330](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/02ed38e9-2485-45c9-a53c-afabceb60736)
Toggle 버튼에는 "예/아니요" 타입의 "Attendance_Status"라는 컬럼을 활용합니다.
Toggle 버튼은 "Attendance_Status"라는 컬럼의 값과 동기화를 해줍니다. 즉, 해당 참가자의 "Attendance_Status"가 "Yes"인 경우에는 "On"이 되게 하고, "No"인 경우에는 "Off"가 되게 합니다.
왼쪽 위에 `Default`로 해주셔야하고, 함수에는
```
LookUp(WebinarBookingList_01, Title = vNameValue, Attendance_Status)
```
적어주면 됩니다.
<br/><br/>
<br/><br/>
## 10. QR 코드 이미지 표시하기
"Image"라는 메뉴를 활용해서 QR코드를 스캔한 후에 스캔한 사람의 QR 코드 이미지를 앱에서 보여주며 확인할 수 있게 해보겠습니다.
꼭 필요하지는 않으나 이미지를 불러와서 앱에 표시하는 기능을 익히는 정도로 실습해보려고 합니다.
<br/><br/>
![스크린샷 2024-03-29 043433](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/7f7e5d41-2306-452d-bd3c-66b575c8af4d)
"이미지"는 상단 메뉴에서 추가하실 수 있습니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-29 043454](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/780a9c83-5a66-448c-a02b-94d563619e02)
위와 같이 원하는 위치에 배치하면 됩니다.
그리고 함수를 다음과같이 적어줍니다.
```
"LookUp(WebinarBookingList_01, Title = vNameValue, QR)"
```
참고로 "Image"를 테이블 또는 외부에서 불러올 때 이미지 주소는 문자여야 하므로 따옴표로 감싸줘야 합니다.
<br/><br/>
<br/><br/>
## 11. 출석상태 변경후 SharePoint List에 변경한 값 업데이트 하기(Patch)
![스크린샷 2024-03-29 043605](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/2d682db7-57bd-41b3-a996-2e3f5622b011)
<br/><br/>
`+`누른 후 버튼을 검색하구 `버튼`을 선택하여 추가해줍니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-29 043651](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/ed35b4c9-e777-4fac-a135-42f1e6ce86f7)
<br/><br/>
이 때 Patch가 성공하면 If 함수를 사용해서 성공과 실패의 경우 메세지를 달리 보여주게 처리합니다.
```
Set(varPatchResult, Patch(WebinarBookingList_01, LookUp(WebinarBookingList_01, Title=vNameValue), {Attendance_Status: Toggle1.Value}));
If(!IsError(varPatchResult), Notify("출석 상태 변경 성공", NotificationType.Success), Notify("출석 상태 변경 오류", NotificationType.Error));
```
<br/><br/>
<br/><br/>
## 12. 앱 게시하기.
![스크린샷 2024-03-29 043753](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/e6abcbe5-017c-4d90-a16b-a6f79679c2a9)
<br/><br/>
오른쪽 위를 아이콘을 선택해 게시해주면 됩니다.
<br/><br/>
<br/><br/>
