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
## 3. Power Automate로 자동화흐름 만들기<br/><br/>
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
> 참가자에게 이메일을 보내기 전에, 잘 실행되는지 테스트를 하겠습니다.
>‘저장’ 후 ‘테스트’를 누릅니다.

<br/><br/>
<br/><br/>
![스크린샷 2024-03-19 085940](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/9fddae34-15f4-4f5d-a6fe-a98e4edc74dc)
<br/><br/>
`수동`으로 `테스트`를 누릅니다.
이후 `흐름실행`을 누르고,
<br/><br/>
<br/><br/>
![스크린샷 2024-03-19 090038](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/0aaa0b3f-e5ee-4119-b004-b82327a39eea)
<br/><br/>
‘흐름실행페이지’에 들어가 ‘테스트 성공’이라고 뜨는지 확인해주면 됩니다.
<br/><br/>
<br/><br/>
다시 SharePoint에 들어가보면<br/><br/>
![스크린샷 2024-03-19 090505](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/967bde3a-7d3c-4e41-b910-35b3e7f85055)
<br/><br/>
‘QR’이 성공적으로 생긴걸 확인할 수 있습니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-19 090753](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/9a0b31e0-dec2-4432-bd31-ca134b57a75a)
<br/><br/>
`작업추가`를 눌러줍니다.
> 이제 QR을 생성했으니, 이메일을 보내는 작업을 만들겁니다.

<br/><br/>
<br/><br/>
![스크린샷 2024-03-19 091054](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/8ed445f2-b03a-471d-a19c-d95163944c10)
<br/><br/>
‘메일’을 검색 후, ‘메일 보내기’를 선택합니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-19 091327](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/3eecd513-be69-4a3c-9079-5e41cca230f9)
<br/><br/>
‘받는 사람’에 ‘이메일’을 선택해주고,
<br/><br/>
<br/><br/>
![스크린샷 2024-03-19 091537](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/a4e5f0e5-52a8-4ee5-bc49-649ae538bec9)
<br/><br/>
각각 다음과 같이 작성한후, QR코드 이미지가 외부에서 생성되어 해당 주소를 입력해야하므로 QR 코드 이미지 주소를 HTML 태그를 통해서 입력하게 되어 '<img src=“해당주소”>'와 같이 직접 HTML 태그로 작성합니다.
따라서, `</>`표시를 누릅니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-19 091815](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/6b00e3f0-bd50-48c7-97ed-0dc9853f5aec)
<br/><br/>
'</p>'위에 `<img src=“QR”>`을 작성해줍니다.
<br/><br/>
<br/><br/>
## 3. Power Automate 흐름 실행 후, 결과 확인하기 <br/><br/>
![스크린샷 2024-03-19 092255](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/fb38c82a-63f8-4445-83e5-80ab88f99c58)
<br/><br/>
이제 `실행`버튼을 누르면 실행됩니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-19 092434](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/f1d87c66-4e71-49ff-ba80-57dee1e861c9)
<br/><br/>
무사히 실행된 것을 확인할 수 있습니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-19 092813](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/846d85ff-a1bb-4781-827d-5a0aea2ac647)
<br/><br/>
이와 같은 흐름으로 완성된 것을 확인할 수 있습니다.
<br/><br/>
<br/><br/>
![스크린샷 2024-03-28 052556](https://github.com/g1nya2/Power_Platform_Attendance/assets/105257807/eceda130-1415-4b35-b891-45c6e0883a1c)
<br/><br/>
메일함에 들어가보니 성공적으로 메일이 도착해있네요!
<br/><br/>
<br/><br/>
이렇게 동아리원 엑셀 파일과 Power Automate만 있다면 QR를 값에 따라 자동생성해서 이메일로 발송해주는 시스템을 코드없이 만들어내실 수 있습니다!
<br/><br/>
그럼 이번엔 이메일로 발송된 QR코드를 현장에서 인식하여, 출석체크를 할 수 있도록 출석체크 앱을 한번 만들어 볼까요?
=> [<section02>로 넘어가기](https://github.com/g1nya2/Power_Platform_Attendance/blob/main/Start-here/section02%20/Power%20Apps_make_QR_check-in_app.md)
