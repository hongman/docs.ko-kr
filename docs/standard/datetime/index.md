---
title: "날짜, 시간 및 표준 시간대 | Microsoft Docs"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time zone objects [.NET Framework]
- date and time data [.NET Framework]
- time zones [.NET Framework]
- times [.NET Framework], time zones
- time [.NET Framework], time zones
ms.assetid: 295c16e0-641b-4771-94b3-39c1ffa98c13
caps.latest.revision: 22
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: a6e7e748f67cf9d2dbfe5dd9bb9b14ecf2d8c331
ms.contentlocale: ko-kr
ms.lasthandoff: 05/05/2017

---

# <a name="dates-times-and-time-zones"></a>날짜, 시간 및 표준 시간대

.NET에서는 기본 <xref:System.DateTime> 구조 외에도 표준 시간대를 사용할 수 있는 클래스를 지원합니다.

* <xref:System.TimeZone>

  이 클래스를 사용하여 시스템의 현지 표준 시간대와 UTC(협정 세계시) 영역을 사용합니다.<xref:System.TimeZone> 클래스는 대체로 <xref:System.TimeZoneInfo> 클래스로 대체됩니다.

* <xref:System.TimeZoneInfo>

  이 클래스를 사용하여 시스템에 미리 정의된 표준 시간대를 사용하고, 새 표준 시간대를 만들고, 한 표준 시간대에서 다른 표준 시간대로 날짜 및 시간을 쉽게 변환할 수 있습니다. 새 개발을 위해서는 <xref:System.TimeZone> 클래스 대신 <xref:System.TimeZoneInfo> 클래스를 사용합니다.

* <xref:System.DateTimeOffset>

  이 구조를 사용하여 UTC의 해당 오프셋(또는 차이)가 알려진 날짜 및 시간을 사용합니다. <xref:System.DateTimeOffset> 구조체는 날짜 및 시간 값을 UTC의 해당 시간 오프셋과 결합합니다. UTC와의 관련성으로 인해 개별 날짜 및 시간 값은 단일 지점을 명확하게 식별합니다. 이렇게 하면 <xref:System.DateTime> 값보다 <xref:System.DateTimeOffset> 값이 한 컴퓨터에서 다른 컴퓨터로 이식 가능합니다.

설명서의 이 섹션에서는 표준 시간대로 작업하고 날짜 및 시간 한 시간 표준 시간대에서 다른 표준 시간대로 변환할 수 있는 표준 시간대 인식 응용 프로그램을 만들기 위해 필요한 정보를 제공합니다.

## <a name="in-this-section"></a>단원 내용

[표준 시간대 개요](../../../docs/standard/datetime/time-zone-overview.md)
 표준 시간대 인식 응용 프로그램을 만드는 데 관련된 용어, 개념 및 문제에 관해 설명합니다.

[DateTime, DateTimeOffset, TimeSpan 및 TimeZoneInfo 중 선택](../../../docs/standard/datetime/choosing-between-datetime.md)
 날짜 및 시간 데이터를 사용하는 경우 <xref:System.DateTime>, <xref:System.DateTimeOffset> 및 <xref:System.TimeZoneInfo> 형식을 사용할 시기를 설명합니다.

[로컬 시스템에 정의된 표준 시간대 찾기](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
 로컬 시스템에서 발견된 표준 시간대를 열거하는 방법에 관해 설명합니다.

[방법: 컴퓨터에 있는 표준 시간대 열거](../../../docs/standard/datetime/enumerate-time-zones.md)
 컴퓨터의 레지스트리에 정의된 표준 시간대를 열거하고 사용자가 목록에서 미리 정의된 표준 시간대를 선택할 수 있는 예제를 제공합니다.

[방법: 미리 정의된 UTC 및 현지 표준 시간대 개체에 액세스](../../../docs/standard/datetime/access-utc-and-local.md)
 협정 세계시 및 현지 표준 시간대에 액세스하는 방법에 관해 설명합니다.

[방법: TimeZoneInfo 개체 인스턴스화](../../../docs/standard/datetime/instantiate-time-zone-info.md)
 로컬 시스템 레지스트리에서 <xref:System.TimeZoneInfo> 개체를 인스턴스화하는 방법에 관해 설명합니다.

[DateTimeOffset 개체 인스턴스화](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md)
 <xref:System.DateTimeOffset> 개체를 인스턴스화할 수 있는 방법 및 <xref:System.DateTime> 값을 <xref:System.DateTimeOffset> 값으로 변환할 수 있는 방법에 관해 설명합니다.

[방법: 조정 규칙을 사용하지 않고 표준 시간대 만들기](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)
 일광 절약 시간제에서 전환을 지원하지 않는 사용자 지정 표준 시간대를 만드는 방법을 설명합니다.

[방법: 조정 규칙을 사용하여 표준 시간대 만들기](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)
 일광 절약 시간제에서 전환을 하나 이상 지원하는 사용자 지정 표준 시간대를 만드는 방법을 설명합니다.

[표준 시간대 저장 및 복원](../../../docs/standard/datetime/saving-and-restoring-time-zones.md)
 표준 시간대 데이터의 serialization 및 deserialization에 대한 <xref:System.TimeZoneInfo> 지원에 관해 설명하고 이러한 기능을 사용할 수 있는 일부 시나리오를 보여 줍니다.

[방법: 포함 리소스에 표준 시간대 저장](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
 사용자 지정 표준 시간대를 만들고 리소스 파일에 해당 정보를 저장하는 방법을 설명합니다.

[방법: 포함 리소스에서 표준 시간대 복원](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) 
 포함 리소스 파일에 저장된 사용자 지정 표준 시간대를 인스턴스화하는 방법을 설명합니다.

[날짜 및 시간에 대한 산술 연산 수행](../../../docs/standard/datetime/performing-arithmetic-operations.md)
 <xref:System.DateTime> 및 <xref:System.DateTimeOffset> 값의 추가, 빼기 및 비교와 관련된 문제에 관해 설명합니다.

[방법: 날짜 및 시간 산술 연산의 표준 시간대 사용](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)
 표준 시간대의 조정 규칙을 반영하는 날짜 및 시간 산술 연산을 수행하는 방법에 관해 설명합니다.

[DateTime 및 DateTimeOffset 간의 변환](../../../docs/standard/datetime/converting-between-datetime-and-offset.md)
 <xref:System.DateTime> 및 <xref:System.DateTimeOffset> 값 간에 변환하는 방법에 관해 설명합니다.

[표준 시간대 간에 시간 변환](../../../docs/standard/datetime/converting-between-time-zones.md)
 한 표준 시간대를 다른 표준 시간대로 변환하는 방법에 관해 설명합니다.

[방법: 모호한 시간 확인](../../../docs/standard/datetime/resolve-ambiguous-times.md)
 모호한 시간을 표준 시간대의 표준 시간에 매핑하여 해결하는 방법에 관해 설명합니다.

[방법: 사용자의 모호한 시간 확인 작업 허용](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
 사용자가 모호한 현지 시간과 협정 세계시 간의 매핑을 확인하도록 하는 방법을 설명합니다.

## <a name="reference"></a>참조

<xref:System.TimeZoneInfo?displayProperty=fullName>
