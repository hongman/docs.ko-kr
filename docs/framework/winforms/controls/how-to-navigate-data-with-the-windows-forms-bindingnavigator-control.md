---
title: "방법: Windows Forms BindingNavigator 컨트롤을 사용하여 데이터 탐색 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "BindingNavigator 컨트롤[Windows Forms], 데이터 탐색"
  - "데이터[Windows Forms], 탐색"
  - "데이터 탐색"
  - "예제[Windows Forms], BindingNavigator 컨트롤"
ms.assetid: 0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 방법: Windows Forms BindingNavigator 컨트롤을 사용하여 데이터 탐색
Windows Forms의 <xref:System.Windows.Forms.BindingNavigator> 컨트롤을 통해 개발자는 자신이 만든 폼에서 간단한 데이터 탐색 및 조작 사용자 인터페이스를 최종 사용자에게 제공할 수 있습니다.  
  
 <xref:System.Windows.Forms.BindingNavigator> 컨트롤은 데이터 집합의 첫 번째 레코드, 마지막 레코드, 다음 레코드 및 이전 레코드를 탐색하도록 미리 구성된 단추와 레코드 추가 및 삭제 단추가 있는 <xref:System.Windows.Forms.ToolStrip> 컨트롤입니다.  <xref:System.Windows.Forms.BindingNavigator> 컨트롤은 <xref:System.Windows.Forms.ToolStrip> 컨트롤이므로 쉽게 단추를 추가할 수 있습니다.  [방법: Windows Forms BindingNavigator 컨트롤에 로드, 저장 및 취소 단추 추가](http://msdn.microsoft.com/library/safa4957\(v=vs.110\))를 참조하세요.  
  
 <xref:System.Windows.Forms.BindingNavigator> 컨트롤의 각 단추에 대해 프로그래밍 방식으로 동일한 기능을 허용하는 <xref:System.Windows.Forms.BindingSource> 구성 요소의 해당 멤버가 있습니다.  예를 들어 <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> 단추는 <xref:System.Windows.Forms.BindingSource> 구성 요소의 <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> 메서드에 해당하고 <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> 단추는 <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> 메서드에 해당합니다.  따라서 <xref:System.Windows.Forms.BindingNavigator> 컨트롤이 데이터 레코드를 탐색할 수 있게 하려는 경우 해당 <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> 속성을 폼의 적절한 <xref:System.Windows.Forms.BindingSource> 구성 요소로 설정하면 됩니다.  
  
### BindingNavigator 컨트롤을 설정하려면  
  
1.  `bindingSource1`이라는 <xref:System.Windows.Forms.BindingSource> 구성 요소와 `textBox1` 및 `textBox2`라는 <xref:System.Windows.Forms.TextBox> 컨트롤 두 개를 추가합니다.  
  
2.  `bindingSource1` 을 데이터에 바인딩하고 textbox 컨트롤을 `bindingSource1`에 바인딩합니다.  이렇게 하려면 다음 코드를 폼에 붙여넣고 폼의 생성자나 <xref:System.Windows.Forms.Form.Load> 이벤트 처리 메서드에서 `LoadData`를 호출합니다.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3.  `bindingNavigator1`이라는 <xref:System.Windows.Forms.BindingNavigator> 컨트롤을 폼에 추가합니다.  
  
4.  `bindingNavigator1`의 <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> 속성을 `bindingSource1`로 설정합니다.  이 작업은 디자이너나 코드에서 수행할 수 있습니다.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## 예제  
 다음 코드 예제는 앞에 나열된 단계의 전체 예제입니다.  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## 코드 컴파일  
 이 예제에는 다음 사항이 필요합니다.  
  
-   System, System.Data, System.Drawing, System.Windows.Forms and System.Xml 어셈블리에 대한 참조  
  
 명령줄에서 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 또는 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]용으로 이 예제를 빌드하는 방법에 대한 자세한 내용은 [명령줄에서 빌드](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) 또는 [csc.exe를 사용한 명령줄 빌드](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)를 참조하세요.  [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]에서 코드를 새 프로젝트에 붙여넣어 이 예제를 빌드할 수도 있습니다.  [방법: Visual Studio를 사용하여 전체 Windows Forms 코드 예제 컴파일 및 실행](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))을 참조하세요.  
  
## 참고 항목  
 <xref:System.Windows.Forms.BindingNavigator>   
 [BindingNavigator 컨트롤](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)   
 [ToolStrip 컨트롤](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)