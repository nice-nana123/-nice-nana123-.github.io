---
layout:  post
permalink: /excel_data_load/
title: 엑셀에 외계어가 뜰 때?!👽 엑셀 데이터 한글 텍스트 깨질 때 변환하는 법!
date: 2021-04-10 23:50:00 +09:00
feature: '/images/posts/11/thumb.png'
image: '/images/posts/11/head.png'
categories:
  - go_home
tags:
  - 엑셀외계어
  - 엑셀데이터변환
  - 액셀한글깨짐
  - 엑셀CSV오류
  - 웹데이터엑셀로다운받기
  - 웹데이터가져오기
description: 웹에서 CSV로 데이터를 다운로드했는데 한글이 깨질때! 제대로 된 형태로 변환하는 방법!
---

### 괜찮은 자료를 찾아서 활용하기 위해 받았는데, 한글이 다 깨졌다?!

![excel_data](/images/posts/11/wordbreak.png)

업무에 쓸 만한 데이터를 간신히 찾았는데, 열고보니 외계어가 난무해서 활용을 포기하셨던 분들 주목해주세요!
이런 현상은 업무 중 꽤 자주 마주칠 수 있습니다. 데이터 인코딩-디코딩 방식의 차이로 이런 문제들이 발생하는데요, 데이터를 쓸 수 있게 엑셀로 가져오는 방법을 알아보겠습니다.


### 엑셀 '데이터 가져오기' 기능 활용해서 깨진 한글데이터 제대로 불러오기

사실 저도 이 기능을 모르기 전까진 데이터메뉴 들어가면 중복값 제거 기능 만 썼지, 아깝게 수집한 데이터들을 활용하지 못하고 날리거나,
정 써야 한다면 일일이 배껴쓰는.. 고생을 했었습니다.

엑셀 데이터 가져오기 기능은 데이터 메뉴에서 앞쪽 부분에서 확인할 수 있습니다. 자 그럼 어떻게 쓰는건지 순서대로 적어보겠습니다.

![excel-data-menu](/images/posts/11/newfile.png)

1.파일을 열지 않고, 엑셀창을 하나 켜둔다.
<br><small>-파일을 바로 열면 텍스트가 깨져서 나옵니다.</small>

2.데이터 - 텍스트/CSV 가져오기 클릭

![openfile](/images/posts/11/openfile.png)

3.열었을 때 오류가 났던 그 파일을 선택해준다.

![decodingdata1](/images/posts/11/decodingdata.png)

4.파일 원본 부분에서 형식을 유니코드(UTF-8)으로 선택해준다.

![decodingdata2](/images/posts/11/decodingdata2.png)

5.변환이 완료 된 파일을 [로드]하기!

![dataload](/images/posts/11/dataload.png)

6.변환된 데이터를 마음껏 이용하기!

### +a 웹에있는 데이터 엑셀로 가져오기!

웹페이지 상에 표로 들어가있는 데이터를 쉽게 엑셀로 가져올 수 있는 방법도 있습니다. 요즘 또 코로나 확진자가 증가 추세를 보이고 있는데, 국내 코로나 발생 현황 데이터를 한 번 가져와 볼까요?

![covid19](/images/posts/11/covid19.png)

위 페이지는 국가에서 운영하고 있는 코로나 국내/외 발생 현황을 공유하는 페이지[(link)](http://ncov.mohw.go.kr/bdBoardList_Real.do?brdId=1&brdGubun=11&ncvContSeq=&contSeq=&board_id=&gubun=)인데요, 해당 페이지에 표가 많아서 예제로 한 번 가져와보았습니다.

![excel-data-menu](/images/posts/11/excel-data-menu.png)

1.CSV 파일을 가져올 때 썼던 버튼 옆에 '웹'이라는 버튼을 누르기.

![webload](/images/posts/11/webload.png)

2.url부분에 데이터를 가져오고 싶은 페이지의 url을 넣고 [확인]누르기

![webdata](/images/posts/11/webdata.png)

3.팝업 좌측창에 뜬 데이터 리스트중 가지고 오고 싶은 데이터를 선택하고 [로드]버튼 누르기
<br><small>*지금은 표 형태의 데이터가 여러개라서, 여러개의 리스트가 뜨고 있습니다.</small>

![complete](/images/posts/11/complete.png)

4.로드 된 데이터를 잘 활용해준다.



오늘은 웹데이터를 잘 활용할 수 있는 방법 두가지를 알아보았습니다. 이 기능을 몰랐다면, 일일이 옮겨 적거나 되는대로 붙여넣어진 데이터의 열과 행을 재정비하는 공수를 들여야 하는데 데이터를 바로 가져올 수 있다면 훨씬 더 일의 효율이 올라가겠죠?! 그럼 오늘도 칼퇴하는 하루 되시길 바랍니다.

-----------------------------
