---
title: "notMarshalable MDA | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "managed debugging assistants (MDAs), interface pointer not marshalable"
  - "interface pointer not marshalable MDA"
  - "MDAs (managed debugging assistants), interface pointer not marshalable"
  - "marshaling, run-time errors"
  - "managed debugging assistants (MDAs), marshaling"
  - "marshalable interface pointers"
  - "MDAs (managed debugging assistants), marshaling"
  - "notMarshalable MDA"
ms.assetid: 96e7b2c1-843f-4d64-b519-740c3a18b50a
caps.latest.revision: 11
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 11
---
# notMarshalable MDA
`notMarshalable` MDA\(관리 디버깅 도우미\)는 CLR\(공용 언어 런타임\)이 컨텍스트 간에 인터페이스를 마샬링하는 동안 등록된 유효한 프록시\/스텁이 없는 COM 인터페이스 포인터 또는 잘못된 `IMarshal` 인터페이스 구현을 발견할 때 활성화됩니다.  
  
## 증상  
 호출이 서비스되지 않거나 COM 인터페이스 포인터에 대한 잘못된 컨텍스트에서 호출이 발생합니다.  
  
## 원인  
 컨텍스트 간에 인터페이스를 마샬링하는 동안 등록된 유효한 프록시\/스텁이 없거나 잘못된 `IMarshal`이 있습니다.  
  
## 해결  
 프록시 스텁이 등록되어 있고 `IMarshal` 구현이 유효한지 확인합니다.  
  
## 런타임에 대한 영향  
 이 MDA는 런타임에 아무런 영향을 미치지 않습니다.  
  
## 출력  
 문제를 설명하는 메시지입니다.  
  
## 구성  
  
```  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## 참고 항목  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Interop 마샬링](../../../docs/framework/interop/interop-marshaling.md)