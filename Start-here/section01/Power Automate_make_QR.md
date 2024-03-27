# Power Automate에서 QR 생성 후, 배포하기
## 1. Microsoft 365 에서 Teams로 이동하기<br/><br/>
먼저, [Microsoft 365](https://www.microsoft365.com/) 에 들어가서 로그인 해줍니다.
<br/><br/>
![스크린샷 2024-03-28 021345](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/0df5e344-63bb-4ebc-a4a8-0776d328742d)
<br/><br/>
왼쪽 배너의 Teams로 들어갑니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-18 062912](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/c20de3c3-e1c3-4c9a-8fbb-6fc79634bd8e)
![스크린샷 2024-03-18 063007](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/ebb7df18-a633-4dd2-a303-753b8c49965a)
<br/><br/>
Teams 내에서 새로운 팀을 만듭니다. `팀 만들기`를 눌러서 만들어주시면 됩니다.
<br/><br/>
<br/><br/>
## 2. Teams 내에 리스트 만들기<br/><br/>
![스크린샷 2024-03-18 063042](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/36c32fd8-894a-4a0c-bb61-174897357b4f)
<br/><br/>
`+`버튼을 누릅니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-18 063130](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/9398a80b-8fbf-4f23-80e6-97a0181fea08)
<br/><br/>
`LIST`를 찾아 선택 후, 저장합니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-18 063233](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/04758c3a-a3ba-4582-89ca-2a0f81928d2b)
<br/><br/>
`목록 만들기`를 선택합니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-18 063346](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/44cc7a02-981b-49b1-9a78-1df02ae9c6b2)
<br/><br/>
`Excel에서`를 선택한 후, 다운 받아둔 동아리원 명단 엑셀파일을 업로드해줍니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-18 064115](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/5b314f52-1caf-4ad9-9ca8-fca0de486c61)
<br/><br/>
이름 위를 `제목`으로 바꿔주고, `다음`을 선택한 후, `만들기`를 해줍니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-18 064244](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/278cf029-b4f7-43e9-8c65-c5ad0fa073b8)
<br/><br/>
생성된 것을 확인할 수 있습니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-18 064423](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/678c37f7-2455-4812-90ef-47d2e2936305)
<br/><br/>
`SharePoint에서 열기`를 선택합니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-18 064715](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/39990817-66d8-46f6-87c2-58f3ca74b89f)
<br/><br/>
`열추가`를 누른 다음 '이름'에 `QR`이라고 적고, '유형'을 `여러줄 텍스트`로 해준 다음 저장해줍니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-19 102931](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/966fd0a8-c51f-4a97-87ff-772f73df9e8a)
<br/><br/>
`열추가`를 선택하고 `예/아니요`를 선택한 다음, `다음`을 선택합니다. `이름`에 `출석현황`이라고 적어준 후 저장합니다.
> 보통 동아리원 명단 엑셀 파일 내에 동아리원 이메일, 이름, 학번, 학부정도만 기록되어 있어, 여기서 추가해주었습니다. <br/>엑셀에서 먼저 추가한 후 바로 리스트를 만들어도 됩니다.

<br/><br/>
## 3. Power Automate로 자동화흐름 만들기기<br/><br/>
![스크린샷 2024-03-18 064918](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/f65f3d28-c189-4ed6-aedd-c0d7ec39ad2d)
<br/><br/>
`통합`->`Power Automate`->`흐름만들기`
<br/><br/>
<br/><br/>
![스크린샷 2024-03-18 065042](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/e2dc89cd-e07d-48ef-8ae2-6b0bf08b5c9b)
<br/><br/>
`흐름보기`를 선택합니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-18 065150](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/8cfc4e58-02ef-46bc-b4c5-f4f88ed51d59)
<br/><br/>
`새 흐름`->`인스턴트 클라우드 흐름` 선택합니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-18 065322](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/7922d0d4-12b0-4449-bbe9-b11d82983154)
<br/><br/>
`흐름이름`을 `QR생성`이라고 적고, `수동으로 흐름 트리거`를 선택한 후 `만들기`를 선택합니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-18 065827](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/e08b2677-a5c1-43f1-8c18-57a25627a9e2)
<br/><br/>
'sharepoint'검색 후, `항목가져오기(2개이상)`을 선택합니다
<br/><br/>
<br/><br/>
![스크린샷 2024-03-18 070237](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/1a8eb1f6-82c3-4837-a6d0-11b47e5b05cd)
<br/><br/>
‘사이트 주소’ , ‘목록이름’ 전 단계에서 만든걸로 각각 선택 후 `새 단계`를 선택합니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-18 070454](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/848c338b-b84b-4ecb-80c2-fd998f1531e9)
<br/><br/>
`조인`을 선택합니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-19 082010](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/43432944-de29-4ffd-b0c6-34549b75247d)
<br/><br/>
'보낸 사람'에 `이름`과 `학부`를 선택해줍니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-19 082152](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/c7a31ccb-74aa-458c-88d1-514a5d461f2d)
<br/><br/>
`[ , ]` 와 같은 형태로 묶어줍니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-19 082405](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/477d8741-f148-413f-aebf-587955e8a3f4)
<br/><br/>
‘join with’에 `|`를 적어줍니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-19 082519](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/73730023-175b-40fb-b3a5-cff3d82788b1)
<br/><br/>
`작업추가`를 눌러줍니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-19 084658](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/2213e507-91cc-4a15-be5d-a829a828f084)
<br/><br/>
‘업데이트’를 검색후 `항목 업데이트`를 선택합니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-19 084819](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/5c59cb88-0cb5-41a8-b62c-41786f4f07a1)
<br/><br/>
‘사이트 주소’ , ‘목록이름’ 아까 전에 만든걸로 각각 선택 후 ‘ID’에는 `ID`를 선택합니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-19 085026](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/df83d9dc-975d-4737-a253-ab7f80da0219)
<br/><br/>
‘QR’에 `출력`을 선택합니다. 
> 그렇게 되면, 이름과 학부를 파이프로 합친 값이 QR에 저장됩니다.

<br/><br/>
<br/><br/>
![스크린샷 2024-03-19 085604](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/75bf8e9d-f4b1-4617-8029-621de3d6d3ed)
<br/><br/>
여기다 QR을 만들어주는 오픈소스를 이용해 `https://quickchart.io/qr?text=`를 '출력' 앞에 붙여주게 되면, 자동으로 QR이 만들어집니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-19 085851](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/4a4929bd-c9a0-4cc2-8a38-6518482e8a65)
> 참가자에게 이메일을 보내기 전에, 잘 실행되는지 테스트를 하겠습니다.<br/><br/>
‘저장’ 후 ‘테스트’를 누릅니다.
<br/><br/>
<br/><br/>







