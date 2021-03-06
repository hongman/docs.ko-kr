---
title: "DataRepeater 컨트롤 (Visual Studio)에서 가상 모드 | Microsoft 문서"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- virtual data binding
- DataRepeater
- DataRepeater, virtual mode
ms.assetid: 5fb805dc-2d8b-4139-b1e3-86e4c2667221
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 85f7e250c57a507e891eb30756c0550098cce9e0
ms.lasthandoff: 03/13/2017

---
# <a name="virtual-mode-in-the-datarepeater-control-visual-studio"></a>DataRepeater 컨트롤의 가상 모드(Visual Studio)
많은 양의 테이블 형식 데이터를 표시 하려는 경우는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>컨트롤을 설정 하 여 성능을 향상 시킬 수 있습니다는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>속성을 `True` 명시적으로 해당 데이터 원본 컨트롤의 상호 작용을 관리 합니다.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>컨트롤은 런타임에 필요에 따라 데이터를 표시 하 고 데이터 소스와 상호 작용을 처리할 수 있는 몇 가지 이벤트를 제공 합니다.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
  
## <a name="how-virtual-mode-works"></a>가상 모드 작동 방식  
 에 대 한 가장 일반적인 시나리오는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>컨트롤의 자식 컨트롤을 바인딩하는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>에 대 한 데이터 디자인 타임에 원본 및 허용는 <xref:System.Windows.Forms.BindingSource>앞뒤로 필요에 따라 데이터를 전달 합니다.</xref:System.Windows.Forms.BindingSource> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 가상 모드를 사용 하는 경우 컨트롤은 데이터 원본에 바인딩되지 않은 이며 데이터 전달 됩니다 앞뒤로 기본 데이터 원본에 런타임 시.  
  
 때는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>속성이 `True`, 컨트롤을 추가 하 여 사용자 인터페이스를 만드는 **도구 상자** 바인딩된 컨트롤을 추가 하는 대신는 **데이터 원본** 창.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>  
  
 컨트롤 단위로 별로 이벤트는 발생 하 고 데이터의 표시를 처리 하는 코드를 추가 해야 합니다. 새 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>스크롤될는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>이벤트는 각 컨트롤에 대해 한 번씩 발생 하 고 각 컨트롤에 대 한 값을 제공 해야는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>이벤트 처리기입니다.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>  
  
 데이터 컨트롤 중 하나에 사용자가 변경 되는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>이벤트가 발생 하 고 데이터의 유효성을 검사 하 고 데이터 원본에 저장 해야 합니다.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>  
  
 사용자가 새 항목을 추가할 경우는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>이벤트가 발생 합니다.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> 이 이벤트 처리기를 사용 하 여 데이터 원본에 새 레코드를 만듭니다. 의도 하지 않은 변경 내용을 방지 하려면 모니터링 해야는 <xref:System.Windows.Forms.Control.KeyDown>각 컨트롤 및 호출에 대 한 이벤트 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A>사용자가 ESC 키를 누르면.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> </xref:System.Windows.Forms.Control.KeyDown>  
  
 데이터 소스가 변경 하는 경우 새로 고칠 수 있습니다는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>호출 하 여 컨트롤의 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>및 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>메서드.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 순서에서 두 메서드를 호출 해야 합니다.  
  
 에 대 한 이벤트 처리기를 구현 해야 하는 마지막으로 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved>항목이 삭제 될 때 및 필요에 따라 발생 하는 이벤트는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletingItems>및 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletedItems>DELETE 키를 눌러 항목을 삭제 하는 사용자 때마다 발생 하는 이벤트입니다.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletedItems> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.UserDeletingItems> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved>  
  
## <a name="implementing-virtual-mode"></a>가상 모드 구현  
 다음은 가상 모드를 구현 하는 데 필요한 단계입니다.  
  
#### <a name="to-implement-virtual-mode"></a>가상 모드 구현 하려면  
  
1.  끌기는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>에서 제어는 **Visual Basic PowerPacks** 탭에 **도구 상자** 폼 이나 컨테이너 컨트롤로.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 설정의 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>속성을 `True`.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>  
  
2.  컨트롤을 끌어는 **도구 상자** 의 항목 템플릿 영역 (위쪽 영역)으로 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>제어 합니다.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 각 필드는 표시 하려는 데이터 원본에 대 한 제어를 할 수 있습니다.  
  
3.  구현에 대 한 처리기는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>각 컨트롤에 대 한 값을 제공 하는 이벤트입니다.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded> 이 이벤트는 새 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>스크롤될.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> 코드는 다음 예와 같이, 라는 데이터 원본에 `Employees`합니다.  
  
     [!code-vb[#1 VbPowerPacksDataRepeaterVirtualMode](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_1.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode&#1;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_1.cs)]  
  
4.  구현에 대 한 처리기는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>이벤트 데이터를 저장 합니다.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> 이 이벤트는 사용자 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> 의 자식 컨트롤에 변경 내용이 커밋될 때 코드는 다음 예와 같이, 라는 데이터 원본에 `Employees`합니다.  
  
     [!code-vb[#2 VbPowerPacksDataRepeaterVirtualMode](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_2.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode&#2;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_2.cs)]  
  
5.  각 자식 컨트롤에 대 한 처리기를 구현 <xref:System.Windows.Forms.Control.KeyDown>이벤트 및 모니터 ESC 키.</xref:System.Windows.Forms.Control.KeyDown> 호출 된 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A>방지 하기 위해 메서드는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>이벤트가 발생 하지.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CancelEdit%2A> 코드에는 다음 예와 비슷하게 표시 됩니다.  
  
     [!code-vb[#3 VbPowerPacksDataRepeaterVirtualMode](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_3.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode&#3;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_3.cs)]  
  
6.  구현에 대 한 처리기는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>이벤트.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded> 이 이벤트는 사용자에 새 항목을 추가 하는 경우는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>제어 합니다.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 코드는 다음 예와 같이, 라는 데이터 원본에 `Employees`합니다.  
  
     [!code-vb[#4 VbPowerPacksDataRepeaterVirtualMode](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_4.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode&#4;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_4.cs)]  
  
7.  구현에 대 한 처리기는 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved>이벤트.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemsRemoved> 이 이벤트는 사용자는 기존 항목을 삭제 하는 경우에 발생 합니다. 코드는 다음 예와 같이, 라는 데이터 원본에 `Employees`합니다.  
  
     [!code-vb[#5 VbPowerPacksDataRepeaterVirtualMode](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_5.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode&#5;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_5.cs)]  
  
8.  제어 수준 유효성 검사에 대 한 처리기를 구현할 필요에 따라는 <xref:System.Windows.Forms.Control.Validating>자식 컨트롤의 이벤트.</xref:System.Windows.Forms.Control.Validating> 코드에는 다음 예와 비슷하게 표시 됩니다.  
  
     [!code-vb[#6 VbPowerPacksDataRepeaterVirtualMode](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/virtual-mode-in-the-datarepeater-control-visual-studio_6.vb) ] 
     [!code-cs [VbPowerPacksDataRepeaterVirtualMode&#6;](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/virtual-mode-in-the-datarepeater-control-visual-studio_6.cs)]  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValuePushed>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.NewItemNeeded>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemValueNeeded>   
 [DataRepeater 컨트롤 소개](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
