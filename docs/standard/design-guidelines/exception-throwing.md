---
title: "예외 Throw | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "예외를 throw"
  - "명시적으로 예외 throw"
  - "예외 throw, 설계 지침"
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 예외 Throw
이 섹션에서 설명 하는 예외를 throw 할 지침 실행이 실패의 의미를 정의 하는 것 필요 합니다. 멤버가 수행할 수 없는 될 때마다 실행 오류가 발생 \(어떤 멤버 이름을 의미 함\)를 수행할 수 있습니다. 예를 들어 하는 경우는 `OpenFile` 메서드 호출자에 게는 열린된 파일 핸들을 반환할 수 없습니다, 실행 실패로 간주 합니다.  
  
 대부분의 개발자가 null 참조 또는 0으로 나누기와 같은 사용 오류에 대 한 예외를 사용에 대해 잘 알고 되 고 있습니다. 프레임 워크 예외는 실행 오류를 비롯 한 모든 오류 조건에 대 한 사용 됩니다.  
  
 **X 하지 않으려면** 오류 코드를 반환 합니다.  
  
 예외는 프레임 워크에서 오류를 보고 하는 기본 수단입니다.  
  
 **✓ 수행** 예외를 throw 하 여 실행 실패를 보고 합니다.  
  
 **✓ 고려** 프로세스를 종료 하면를 호출 하 여 `System.Environment.FailFast` \(.NET Framework 2.0 기능\) 코드에서 안전 하 게 추가 실행 하지 않은 경우 예외를 throw 하는 대신 합니다.  
  
 **X 하지 않으려면** 가능한 경우 컨트롤의 일반 흐름에 대 한 예외를 사용 합니다.  
  
 시스템 오류 및 잠재적 경합 상태를 사용 하 여 작업을 제외 하 고 사용자가 예외를 throw 하지 않는 코드를 작성할 수 있도록 프레임 워크 디자이너 Api를 디자인 해야 합니다. 예를 들어 사용자가 예외를 throw 하지 않는 코드를 작성할 수 있도록 멤버를 호출 하기 전에 사전 조건을 확인 하는 방법을 제공할 수 있습니다.  
  
 다른 멤버의 사전 조건을 확인 하는 데 사용 되는 멤버는 종종 테스터 라면 라고 하 고 실제로 작업을 수행 하는 멤버는 doer가 호출 됩니다.  
  
 Tester\-doer 패턴 수는 허용치 보다 성능 오버 헤드가 만들어야 하는 경우가 있습니다. 이러한 경우에는 소위 Try 구문 분석 패턴 고려해 야 \(참조 [예외 및 성능](../../../docs/standard/design-guidelines/exceptions-and-performance.md) 자세한 내용은\).  
  
 **✓ 고려** 성능에 미치는 영향 예외를 throw 합니다. 초당 100 보다 throw 속도 눈에 띄게 대부분의 응용 프로그램의 성능에 영향을 줄 가능성이 높습니다.  
  
 **✓ 수행** 문서 멤버의 위반으로 인해 공개적으로 호출할 수 멤버에 의해 throw 되는 모든 예외는 시스템 오류\) \(아니라 계약 및 계약의 일부로 처리 합니다.  
  
 예외는 계약의 일부인 변경 안 버전에서 마다 \(즉, 예외 형식을 변경 하지 않아야 및 새 예외 다음에 추가할 수 없습니다\).  
  
 **X 하지 않으면** 공용 멤버 여부 throw 하거나 수 있는 일부 옵션에 기반 합니다.  
  
 **X 하지 않으려면** 반환 값으로 예외를 반환 하는 공용 멤버를 소유 또는 `out` 매개 변수입니다.  
  
 예외를 throw 할 때 해당 하는 대신 공용 Api에서 반환 사용의 많은 예외 기반의 오류 보고의 이점이 없습니다.  
  
 **✓ 고려** 예외 작성기 메서드를 사용 합니다.  
  
 다른 위치에서 동일한 예외를 throw 하려면 일반적 됩니다. 코드 크기를 늘리지를 방지 하려면 예외를 만들고 해당 속성을 초기화 하는 도우미 메서드를 사용 합니다.  
  
 또한 예외를 throw 하는 멤버를 얻지 부터는 인라인 처리 합니다. 작성기 내에 throw 문을 이동 인라인 될 멤버를 허용할 수 있습니다.  
  
 **X 하지 않으려면** 예외 필터 블록에서 예외를 throw 합니다.  
  
 예외 필터에서 예외가 발생 하는 경우 예외는 CLR에서 발생 하 고 필터 false 반환 합니다. 이 동작은 필터를 실행 하 고 명시적으로 false 반환 구분 되지 않으며 디버깅 하는 매우 어렵습니다.  
  
 **X 방지** 명시적으로 finally 블록에서 예외를 throw 합니다. Throw 하는 메서드를 호출 하 여 발생 하는 암시적으로 throw 된 예외를 사용할 수 있습니다.  
  
 *부분 © 2005, 2009 Microsoft Corporation. All rights reserved.*  
  
 *피어슨 교육, i n c.에서의 사용 권한 때마다 다시 인쇄 [Framework 디자인 지침: 규칙, 특징 및 다시 사용할 수 있는.NET 라이브러리, 제 2 판에 대 한 패턴](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 및 Brad Abrams Addison\-wesley Professional에서 2008 년 10 월 22 일 Microsoft Windows 개발 시리즈의 일부로 게시 합니다.*  
  
## 참고 항목  
 [프레임 워크 디자인 지침](../../../docs/standard/design-guidelines/index.md)   
 [예외에 대 한 디자인 지침](../../../docs/standard/design-guidelines/exceptions.md)