---
title: "Create a Client-Side UI Automation Provider | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "UI Automation, creating client-side provider"
  - "client-side UI Automation provider, creating"
ms.assetid: d91edaf2-be28-41ec-a508-af421cb43c3d
caps.latest.revision: 11
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 11
---
# Create a Client-Side UI Automation Provider
> [!NOTE]
>  이 설명서는 <xref:System.Windows.Automation> 네임스페이스에 정의된 관리되는 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 클래스를 사용하려는 .NET Framework 개발자를 위한 것입니다.[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]에 대한 최신 정보는 [Windows 자동화 API: UI 자동화](http://go.microsoft.com/fwlink/?LinkID=156746)를 참조하세요.  
  
 이 항목에는 클라이언트 쪽 UI 자동화 공급자를 구현하는 방법을 보여 주는 예제 코드가 있습니다.  
  
## 예제  
 다음 예제 코드는 콘솔 창에 대해 매우 간단한 클라이언트 쪽 공급자를 구현하는 [!INCLUDE[TLA#tla_dll](../../../includes/tlasharptla-dll-md.md)]에 빌드할 수 있습니다. 이 코드에는 유용한 기능이 없지만, UI 자동화 클라이언트 응용 프로그램에서 등록할 수 있는 공급자 어셈블리를 설정하는 기본 단계를 확인할 수 있습니다.  
  
 [!code-csharp[UIAClientSideProvider_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSProviderProgram.cs#101)]
 [!code-vb[UIAClientSideProvider_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csproviderprogram.vb#101)]  
  
## 참고 항목  
 [UI Automation Providers Overview](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)   
 [Register a Client\-Side Provider Assembly](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)