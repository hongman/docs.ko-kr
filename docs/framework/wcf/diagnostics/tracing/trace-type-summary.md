---
title: "추적 형식 요약 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 추적 형식 요약
[Source Levels](http://go.microsoft.com/fwlink/?LinkID=94943)에서는 Critical, Error, Warning, Information, Verbose 등의 다양한 추적 수준을 정의하고 추적 경계와 동작 전송 이벤트의 출력을 토글하는 `ActivityTracing` 플래그에 대한 설명을 제공합니다.  
  
 <xref:System.Diagnostics>에서 내보낼 수 있는 추적 형식을 [TraceEventType](http://go.microsoft.com/fwlink/?LinkId=95169)\(영문\)에서 검토할 수도 있습니다.  
  
 다음 표에서는 가장 중요한 항목을 보여 줍니다.  
  
|추적 형식|설명|  
|-----------|--------|  
|중요|오류 또는 응용 프로그램 충돌|  
|오류|복구할 수 있는 오류|  
|경고|정보 메시지|  
|정보|중요하지 않은 문제|  
|Verbose|추적 디버깅|  
|시작|처리의 논리 단위 시작|  
|일시 중단|처리의 논리 단위 일시 중단|  
|Resume|처리의 논리 단위 다시 시작|  
|중지|처리의 논리 단위 중지|  
|전송|상관 관계 ID의 변경|  
  
 동작은 위의 추적 형식의 조합으로 정의됩니다.  
  
 다음은 로컬\(추적 소스\) 범위에서 이상적인 동작을 정의하는 정규식입니다.  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 이는 동작이 다음 조건을 만족해야 함을 의미합니다.  
  
-   Start 및 Stop 추적에 의해 각각 시작되고 중지되어야 합니다.  
  
-   Suspend 추적 또는 Resume 추적의 바로 앞에 Transfer 추적이 있어야 합니다.  
  
-   Suspend 추적 및 Resume 추적이 존재할 경우 이 사이에 추적이 있으면 안 됩니다.  
  
-   위와 같은 조건이 충족되는 한 Critical\/Error\/Warning\/Information\/Verbose\/Transfer 추적은 여러 개가 있을 수 있습니다.  
  
 다음은 전역 범위에서 이상적인 동작을 정의하는 정규식입니다.  
  
```  
R+   
```  
  
 로컬 범위에서 동작에 대한 정규식인 R을 포함합니다.  이는 다음으로 변환됩니다.  
  
```  
[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+  
```