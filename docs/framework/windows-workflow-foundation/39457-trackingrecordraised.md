---
title: "39457 - TrackingRecordRaised | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a2731d1-c731-4b79-bb69-016cb69ef481
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 39457 - TrackingRecordRaised
## 속성  
  
|||  
|-|-|  
|ID|39457|  
|키워드|WFRuntime|  
|수준|정보|  
|채널|Microsoft\-Windows\-응용 프로그램 서버\-응용 프로그램\/디버그|  
  
## 설명  
 TrackingRecord가 TrackingParticipant에서 발생했음을 나타냅니다.  
  
## 메시지  
 추적 레코드 %1이\(가\) %2\(으\)로 증가했습니다.  
  
## 설명  
  
|데이터 항목 이름|데이터 항목 형식|설명|  
|---------------|---------------|--------|  
|RecordNumber|xs:string|추적 레코드 번호입니다.|  
|ParticipantId|xs:string|추적 참가자입니다.|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName에서 반환되는 문자열입니다.|