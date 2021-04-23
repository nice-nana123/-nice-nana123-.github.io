---
layout:  post
permalink: /ads_script/
title: 구글 애즈 스크립트 Ads Script 알아보기!
date: 2021-04-21 20:00:00 +09:00
feature: '/images/posts/12/thumb.png'
image: '/images/posts/12/head.png'
categories:
  - high_skill
tags:
  - 구글애즈스크립트
  - googleadsscript
  - 구글캠페인최적화
  - 구글자동입찰
  - googleappsscript
description: 구글 캠페인 관리를 손쉽게 자동화 할 수 있는 Google Ads Script를 알아보자!
---

### Ads Script가 뭔가요?

![ads_script](/images/posts/12/adsscript.png)

Ads script는 말 그대로 Google Ads 를 조작하기 위한 스크립트입니다. 구글에서 제공하는 여러 메서드들을 이용하여 구글 캠페인을 관리하거나 데이터를 추출할 수 있습니다. Javascript 기초내용만 알면 사용이 가능한 수준이라고 해서 Javascript 공부 겸 Ads Script를 적용해보았습니다.

이 외 추가적으로 궁금한 내용은 [(링크)](https://developers.google.com/google-ads/scripts?hl=en)로 확인해보세요 :)
<br>*Ads Script 한국어 지원이 따로 없어서 영어로 보시거나 크롬 번역기를 이용해서 보셔야합니다.

### Ads Script를 사용하기 위해 기본적으로 알아야 할 내용들

Ads Script를 활용하기 위해서는 먼저 어떤 부분을 조작할 수 있고, 어떻게 조작할 수 있는지를 알아야겠죠?
대량 생성이나 관리 같은 부분은 Ads Editor로도 충분히 쉽게 활용할 수 있어서, Ads Script를 이용하는 이점을 주기적인 효율 관리에 초첨을 두고 어떻게 조작할 수 있을지 고민해보았습니다.

![ads_script_element](/images/posts/12/adsscript_element.png)


먼저, 캠페인 효율 관리에 Ads script를 사용하기 위해서는 Ads script의 Entity/Iterator/Selector 를 이해해야하는데요, 번역하자면 객체, 반복자, 선택자 쯤으로 옮길 수 있을 것 같습니다.

1.Entity

Entity는 객체, 즉 우리가 Ads Script로 조작할 수 있는 요소들이 무엇인지 어떤 일들을 할 수 있는지가 설명 되어있습니다. 계정/캠페인/그룹의 세팅 내용에 접근하여 수정하거나 생성/제거하는 것들을 할 수 있고 소재 등록이나 보고서 추출까지 할 수 있는 것을 확인해볼 수 있습니다.

아래는 구글에서 정리해둔 내용을 한글로 정리해서 적어둔 표인데요, 자세한 내용은 [(링크)](https://developers.google.com/google-ads/scripts/docs/features/entities?hl=en
)를 봐주세요.

![ads_script_entites](/images/posts/12/entities.png)


2.Iterator

Iterator는 반복문을 써보셨던 분이라면 익숙하실텐데요, 아무래도 소재나 키워드관리를 할 때 하나의 키워드만을 관리하기위해 스크립트를 이용하는 것은 소요이 없기 때문에 반복문으로 활용을 하게 될 겁니다. Google Ads Script는 반복문을 쉽게 사용할 수 있도록 while문으로 순회할 수 있는 메서드(hasNext(), next())를 제공하고 있습니다.

- 일반적인 반복문 사용

<div class="colorscripter-code" style="color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#fafafa;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #e5e5e5"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#666;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">for</span>&nbsp;(<span style="color:#ff3399">var</span>&nbsp;i&nbsp;<span style="color:#039C43"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#308ce5">0</span>;&nbsp;i&nbsp;<span style="color:#039C43"></span><span style="color:#ff3399">&lt;</span>&nbsp;myArray.<span style="color:#0099cc">length</span>;&nbsp;i<span style="color:#039C43"></span><span style="color:#ff3399">+</span><span style="color:#039C43"></span><span style="color:#ff3399">+</span>)&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">var</span>&nbsp;myObject&nbsp;<span style="color:#039C43"></span><span style="color:#ff3399">=</span>&nbsp;myArray[i];</div><div style="padding:0 6px; white-space:pre; line-height:130%">}&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#e5e5e5text-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#e5e5e5;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>
<br>
- while문을 이용한 배열 순회

<div class="colorscripter-code" style="color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#fafafa;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #e5e5e5"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#666;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">while</span>&nbsp;(myIterator.<span style="color:#ff9b51">hasNext()</span>)&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#ff3399">var</span>&nbsp;myObject&nbsp;<span style="color:#039C43"></span><span style="color:#ff3399">=</span>&nbsp;myIterator.<span style="color:#ff9b51">next()</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%">}&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#e5e5e5text-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#e5e5e5;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>
<br>while문과 hasNext()와 next()를 이용하여 보다 쉽게 여러개의 Google Ads 요소들을 조작 할 수 있습니다.


3.Selector

Google Ads Script에서 Selector는 특정 조건을 만족하는 요소들만 선택하고 싶은 경우에 사용할 수 있습니다.


여기서 선택할 수 있는 조건들은 노출, 클릭, 전환 등의 실적데이터는 물론, 광고 운영 기간으로도 선택해올 수 있고, 그것을 특정 기준으로 정렬하거나 순서대로 몇개만 가져올 수도 있습니다.
이 조건들을 조합해서도 사용을 할 수가 있는데요,

예를 들어, 어제자 운영된 키워드 중 노출이 되었던 키워드의 실적만 골라보고 싶을 때 라든지, 특정 ID를 가지고 있는 요소만 가져오고 싶을 때라든지.
혹은 조금 더 복잡하게 어제 운영되었던 키워드 중 노출량이 가장 많았던 상위 50개 키워드만 가져오고싶을 때 선택자들을 조합해서 가져올 수 있습니다.

아래 사용 예시를 보면 어제 운영되었던 캠페인 중 노출이 1,000회 이상, 클릭이 10회 이상인 캠페인을 노출 수 기준으로 내림차순으로 가져오도록 선택하였습니다.

<div class="colorscripter-code" style="color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#fafafa;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #e5e5e5"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#666;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#010101;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">var</span>&nbsp;campaignSelector&nbsp;<span style="color:#039C43"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:purple">AdsApp</span>.campaigns();</div><div style="padding:0 6px; white-space:pre; line-height:130%">.withCondition(<span style="color:#993333">"Clicks&nbsp;&gt;&nbsp;10"</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">.withCondition(<span style="color:#993333">"Impressions&nbsp;&gt;&nbsp;1000"</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">.orderBy(<span style="color:#993333">"Impressions&nbsp;DESC"</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">.forDateRange(<span style="color:#993333">"YESTERDAY"</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">.get();</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#e5e5e5text-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#e5e5e5;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>
<br>
Google Ads Script Selector에 대해서 더 자세히 알고 싶다면 [(링크)](https://developers.google.com/google-ads/scripts/docs/concepts/selectors?hl=en
)를 확인해주세요.




오늘은 구글 애즈 스크립트로 할 수 있는 것들과, 스크립트로 Googld Ads를 조작하기 위해 알아두어야 하는 기본 내용들을 정리해보았는데요, 이제 개념을 어느정도 알게 되었다면 실제 업무에 활용을 해봐야겠죠?!

다음 글에서는 Ads Scripts를 이용해 실제 운영 중인 캠페인을 자동으로(?) 최적화 하는 방법에 대해서 적어보겠습니다.

-----------------------------
