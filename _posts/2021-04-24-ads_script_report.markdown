---
layout:  post
permalink: /ads_script_report/
title: 구글 애즈 스크립트 Ads Scripts로 리포트 자동발송하기! Report automation.
date: 2021-04-24 15:00:00 +09:00
feature: '/images/posts/13/thumb.png'
image: '/images/posts/13/head.png'
categories:
  - high_skill
tags:
  - 구글애즈스크립트
  - 구글리포트자동화
  - 구글키워드리포트
  - 구글광고리포트
  - 광고리포트자동화
  - googleadsscripts
  - 구글리포트자동발송
  - googlereportautomation
  - reportautomation
description: 구글 애즈 스크립트로 데일리 키워드 리포트 자동 발송! Google Ads Scripts report automation
---

### Ads Script 작성 방법.

Ads Scripts를 이용해서 업무를 자동화 할 수 있는 것 중 가장 간단한 것이 리포트 발송일 것 같은데요,

그래서 가장 먼저 전일자 광고 운영 실적을 가져오는 리포트를 구글 스프레드시트에 옮기고, 그 시트를 메일로 자동 발송해주는 작업을 해보도록 하겠습니다.


![ads_script](/images/posts/13/scriptwrite.png)

구글 Ads Scripts를 쓰는 곳은 구글 광고 계정 안에 있는데요, 구글 광고 계정에서 도구 및 설정 > 일괄 작업 > 스크립트로 들어가줍니다.

![ads_script_function](/images/posts/13/scriptfunction.png)

(+)를 눌러 새스크립트 작성 창에 들어가면, function main()이 보이는데 이 부분은 그대로 두고 중괄호{}안에 스크립트를 작성해주면 됩니다.
<br><small>**함수명이 main이 아니라 다른 것으로 변경되면 함수가 실행되지 않더라구요!</small>

![ads_script_allow](/images/posts/13/allow.png)

*위 화면과 같이 인증하라는 알러트가 뜰 텐데요, Ads Sciprt로 계정에 접근하는 것을 허용해주기 위해서 인증도 진행해주시면 됩니다.

자 이제 스크립트 작성을 위한 준비가 끝났습니다.




### Ads Scripts 로 리포트 발송 자동화 하기.

![report_order](/images/posts/13/report_order.png)

리포트 작성을 위한 스크립트 작성 순서입니다. 먼저 조건에 맞는 키워드를 불러온 다음, 그 키워드에서 보고서로 넣을 값들을 골라 스프레드시트에 옮겨 작성하고, 그 스프레드 시트의 URL을 이메일로 보내 줄 겁니다.

아래에 차근차근 순서대로 작성해보겠습니다. 따라서 작성해보세요~


#### 1.리포트를 옮길 스프레드 시트를 준비하고, 첫열의 라벨(리포트 항목) 작성해주기.
<small>*여기서 주의 할 점은 데일리로 리포트 값이 없데이트 되어야 하기 때문에, <span style="background-color:#FFD966">데이터 입력 전 시트를 비워주는 것</span>입니다.</small>

<div class="colorscripter-code" style="color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#fafafa;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #e5e5e5"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#666;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#a71d5d">var</span>&nbsp;spreadsheetUrl&nbsp;<span style="color:#ff3399"></span><span style="color:#a71d5d">=</span>&nbsp;<span style="color:#63a35c">'공유스프레드시트&nbsp;URL(링크공유&nbsp;편집자&nbsp;권한)'</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#a71d5d">var</span>&nbsp;spreadsheet&nbsp;<span style="color:#ff3399"></span><span style="color:#a71d5d">=</span>&nbsp;SpreadsheetApp.openByUrl(spreadsheetUrl);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#a71d5d">var</span>&nbsp;ss&nbsp;<span style="color:#ff3399"></span><span style="color:#a71d5d">=</span>&nbsp;spreadsheet.getSheetByName(<span style="color:#63a35c">'시트1'</span>);&nbsp;&nbsp;<span style="color:#999999">//스프레드시트&nbsp;내&nbsp;데이터를&nbsp;작성할&nbsp;시트의&nbsp;이름</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;ss.clear();&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//데일리로&nbsp;값이&nbsp;없데이트&nbsp;되어야&nbsp;하므로,&nbsp;데이터&nbsp;입력&nbsp;전&nbsp;시트&nbsp;비워주기</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#a71d5d">var</span>&nbsp;sheetArray</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#ff3399"></span><span style="color:#a71d5d">=</span>[[<span style="color:#63a35c">'Campaign'</span>,<span style="color:#63a35c">'Group'</span>,<span style="color:#63a35c">'Keyword'</span>,<span style="color:#63a35c">'Impressions'</span>,<span style="color:#63a35c">'Clicks'</span>,<span style="color:#63a35c">'AvgCPC'</span>,<span style="color:#63a35c">'Cost'</span>,<span style="color:#63a35c">'CVR'</span>,<span style="color:#63a35c">'Conversions'</span>&nbsp;]];&nbsp;<span style="color:#999999">//&nbsp;리포트항목&nbsp;작성하기</span></div></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#e5e5e5;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>
<br>
#### 2.특정 조건을 만족하는 키워드 리스트 가져오기.
<div class="colorscripter-code" style="color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#fafafa;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #e5e5e5"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#666;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#a71d5d">var</span>&nbsp;keywords&nbsp;<span style="color:#ff3399"></span><span style="color:#a71d5d">=</span>&nbsp;AdsApp.keywords()</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;.withCondition(<span style="color:#63a35c">'Impressions&nbsp;&gt;&nbsp;0'</span>)&nbsp;<span style="color:#999999">//노출량이&nbsp;0&nbsp;이상이고</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;.forDateRange(<span style="color:#63a35c">'YESTERDAY'</span>)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//기간&nbsp;범위는&nbsp;어제이고</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;.orderBy(<span style="color:#63a35c">'Impressions&nbsp;DESC'</span>)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//순서는&nbsp;노출순으로&nbsp;내림차순으로</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;.get();&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//키워드&nbsp;가져오기</span></div></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#e5e5e5;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>
<br>
#### 3.리포트 항목별로 키워드별 데이터를 불러와 스프레드시트 배열에 넣어주기.

<div class="colorscripter-code" style="color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#fafafa;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #e5e5e5"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#666;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div><div style="line-height:130%">8</div><div style="line-height:130%">9</div><div style="line-height:130%">10</div><div style="line-height:130%">11</div><div style="line-height:130%">12</div><div style="line-height:130%">13</div><div style="line-height:130%">14</div><div style="line-height:130%">15</div><div style="line-height:130%">16</div><div style="line-height:130%">17</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#a71d5d">while</span>(keywords.hasNext()){&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//키워드에&nbsp;다음&nbsp;값이&nbsp;있는&nbsp;동안</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#a71d5d">var</span>&nbsp;keyword&nbsp;<span style="color:#ff3399"></span><span style="color:#a71d5d">=</span>&nbsp;keywords.next();&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//keyword에&nbsp;다음&nbsp;키워드&nbsp;넣어주기</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;sheetArray.push([&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//아래&nbsp;값들을&nbsp;sheetArray&nbsp;배열에&nbsp;넣어주기&nbsp;</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;keyword.getCampaign().getName(),&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//키워드의&nbsp;캠페인&nbsp;이름&nbsp;가져오기</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;keyword.getAdGroup().getName(),&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//키워드의&nbsp;광고그룹&nbsp;이름&nbsp;가져오기</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;keyword.getText(),&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//키워드의&nbsp;텍스트&nbsp;가져오기</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;keyword.getStatsFor(<span style="color:#63a35c">'YESTERDAY'</span>).getImpressions(),&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//키워드의&nbsp;전일자&nbsp;노출량&nbsp;가져오기</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;keyword.getStatsFor(<span style="color:#63a35c">'YESTERDAY'</span>).getClicks(),&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//키워드의&nbsp;전일자&nbsp;클릭수&nbsp;가져오기</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;keyword.getStatsFor(<span style="color:#63a35c">'YESTERDAY'</span>).getAverageCpc(),&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//키워드의&nbsp;전일자&nbsp;평균&nbsp;CPC&nbsp;가져오기</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;keyword.getStatsFor(<span style="color:#63a35c">'YESTERDAY'</span>).getCost(),&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//키워드의&nbsp;전일자&nbsp;소진비용&nbsp;가져오기</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;keyword.getStatsFor(<span style="color:#63a35c">'YESTERDAY'</span>).getConversionRate(),&nbsp;&nbsp;&nbsp;<span style="color:#999999">//키워드의&nbsp;전일자&nbsp;전환율&nbsp;가져오기</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;keyword.getStatsFor(<span style="color:#63a35c">'YESTERDAY'</span>).getConversions(),&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//키워드의&nbsp;전일자&nbsp;전환수&nbsp;가져오기</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;]);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;}</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#e5e5e5text-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#e5e5e5;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>
<br>
#### 4.스프레드시트의 URL을 메일로 보내주기.

<div class="colorscripter-code" style="color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#fafafa;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #e5e5e5"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#666;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#a71d5d">if</span>(sheetArray.<span style="color:#066de2">length</span>&nbsp;<span style="color:#ff3399"></span><span style="color:#a71d5d">&gt;</span>&nbsp;<span style="color:#0099cc">0</span>){&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//sheetArray배열에&nbsp;내용이&nbsp;1개&nbsp;이상이면</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;ss.getRange(<span style="color:#0099cc">1</span>,<span style="color:#0099cc">1</span>,sheetArray.<span style="color:#066de2">length</span>,&nbsp;sheetArray[<span style="color:#0099cc">0</span>].<span style="color:#066de2">length</span>).setValues(sheetArray);&nbsp;<span style="color:#999999">//스프레드시트에&nbsp;내용&nbsp;채우기</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;MailApp.sendEmail(<span style="color:#63a35c">'이메일&nbsp;주소'</span>,<span style="color:#63a35c">'메일&nbsp;제목'</span>,&nbsp;<span style="color:#63a35c">'메일내용'</span>&nbsp;<span style="color:#ff3399"></span><span style="color:#a71d5d">+</span>&nbsp;spreadsheetUrl&nbsp;);&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//메일로&nbsp;보내주기</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#e5e5e5text-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#e5e5e5;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>

<br>
이렇게 작성 후 스크립트를 실행하게 되면, 메일이 들어오고 메일 내 스프레드 시트 링크를 통해 들어가면 전일자 키워드리포트를 확인 할 수 있습니다.

![result](/images/posts/13/result.png)


#### 5.규칙(주기/실행 시간) 설정해주기.

![frequency](/images/posts/13/frequency.png)

이제 스크립트를 저장하고 나와서, 실행 주기를 설정해줍니다. 보통은 출근하자마자 전일자 광고운영 실적을 확인하고 계실텐데요, 매일 아침 9시에 스크립트가 실행 되도록 해두면
9시마다 데일리 키워드리포트를 자동으로 받아 볼 수 있겠죠?!



오늘은 Ads Scripts로 Daily Report Automation을 해보았습니다. 어려운 듯 하지만, 한 번 작성해보면 대략 감이 잡히실 거에요.
다음에는 키워드 입찰관리의 번거로움을 없애주는 입찰 자동화를 위한 Ads Scripts 작성법을 정리해보겠습니다.


-----------------------------
