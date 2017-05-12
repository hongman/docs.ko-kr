---
title: "UI Automation Support for the Pane Control Type | Microsoft Docs"
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
  - "UI Automation, Pane control type"
  - "Pane control type"
  - "control types, Pane"
ms.assetid: 79761191-4449-4630-899c-9cbdb8867d3f
caps.latest.revision: 25
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 25
---
# UI Automation Support for the Pane Control Type
> [!NOTE]
>  이 설명서는 <xref:System.Windows.Automation> 네임스페이스에 정의된 관리되는 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 클래스를 사용하려는 .NET Framework 개발자를 위한 것입니다.[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]에 대한 최신 정보는 [Windows 자동화 API: UI 자동화](http://go.microsoft.com/fwlink/?LinkID=156746)를 참조하세요.  
  
 이 항목에서는 Pane 컨트롤 형식에 대한 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 지원 정보를 제공합니다.[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]에서, 컨트롤 형식은 <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> 속성을 사용하기 위해 컨트롤이 충족해야 하는 조건 집합입니다. 이 조건에는 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 트리 구조, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 속성 값, 컨트롤 패턴에 대한 특정 지침이 포함됩니다.  
  
 Pane 컨트롤 형식은 프레임 또는 문서 창 내에서 개체를 나타내는 데 사용됩니다. 사용자는 창 컨트롤과 현재 창의 콘텐츠 내에서 탐색할 수 있지만 다른 창의 항목은 탐색할 수 없습니다. 따라서, 창 컨트롤은 창 또는 문서보다 낮은 그룹화 수준을 나타내지만 개별 컨트롤 이상의 수준은 나타내지 않습니다. 컨텍스트에 따라 사용자가 TAB, F6 또는 CTRL\+TAB을 눌러 창을 탐색합니다. Pane 컨트롤 형식에는 특정 키보드 탐색이 필요하지 않습니다.  
  
 다음 섹션에서는 Pane 컨트롤 형식에 필요한 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 트리 구조, 속성, 컨트롤 패턴, 이벤트를 정의합니다.[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 요구 사항은 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] 또는 [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]의 모든 목록 컨트롤에 적용됩니다.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## 필요한 UI 자동화 트리 구조  
 다음 표는 창 컨트롤과 관련된 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 트리의 컨트롤 뷰 및 콘텐츠 뷰를 보여주고 각 뷰에 포함될 수 있는 내용에 대해 설명합니다.[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 트리에 대한 자세한 내용은 [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)를 참조하세요.  
  
|컨트롤 뷰|콘텐츠 뷰|  
|-----------|-----------|  
|창|창|  
  
<a name="Required_UI_Automation_Properties"></a>   
## 필요한 UI 자동화 속성  
 다음 표에서는 값 또는 정의가 창 컨트롤과 특별히 관련된 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 속성을 나열하여 보여줍니다.[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 속성에 대한 자세한 내용은 [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)를 참조하세요.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 속성|값|노트|  
|------------------------------------------------------------------------------|-------|--------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|메모를 참조하세요.|이 속성의 값은 응용 프로그램의 모든 컨트롤에서 고유해야 합니다.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|메모를 참조하세요.|전체 컨트롤이 포함된 가장 바깥쪽 사각형입니다.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|메모를 참조하세요.|컨트롤이 키보드 포커스를 받을 수 있으면 해당 컨트롤은 이 속성을 지원해야 합니다.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|메모를 참조하세요.|이 속성의 값은 항상 명확하고 간결하며 의미 있는 제목이어야 합니다.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|메모를 참조하세요.|이 속성은 클릭할 때 창이 포커스를 받을 수 있도록 하는 창 컨트롤의 클릭 가능한 지점을 노출합니다.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|메모를 참조하세요.|창 컨트롤에는 일반적으로 정적 레이블이 없습니다. 정적 텍스트 레이블이 있는경우 이 속성을 통해 노출되어야 합니다.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|창|이 값은 모든 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 프레임워크에 대해 동일합니다.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"pane"|Pane 컨트롤 형식에 해당하는 지역화된 문자열입니다.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|창 컨트롤이 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 트리의 콘텐츠 뷰에 항상 포함됩니다.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|창 컨트롤이 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 트리의 컨트롤 뷰에 항상 포함됩니다.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|""|창 컨트롤의 도움말 텍스트는 해당 프레임의 용도 및 다른 프레임과의 관계를 설명해야 합니다.`NameProperty` 값으로 프레임의 용도 및 관계가 명확하게 나타나지 않으면 설명이 필요합니다. "|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>|메모를 참조하세요.|특정 키 조합을 사용할 때 창에 포커스가 제공되면 해당 정보는 이 속성을 통해 노출되어야 합니다.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## 필요한 UI 자동화 컨트롤 패턴  
 다음 표에서는 모든 창 컨트롤에서 지원되는 데 필요한 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 컨트롤 패턴을 나열하여 보여줍니다. 컨트롤 패턴에 대한 자세한 내용은 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)를 참조하세요.  
  
|컨트롤 패턴|지원|노트|  
|------------|--------|--------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider>|종속|창 컨트롤을 화면에서 이동, 크기 조정 또는 회전할 수 있는 경우 이 컨트롤 패턴을 구현합니다.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider>|Never|이 컨트롤 패턴을 구현해야 하는 경우 해당 컨트롤은 <xref:System.Windows.Automation.ControlType.Window> 컨트롤 형식을 기반으로 해야 합니다.|  
|<xref:System.Windows.Automation.Provider.IDockProvider>|종속|창 컨트롤을 도킹할 수 있는 경우 이 컨트롤 패턴을 구현합니다.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|종속|창 컨트롤을 스크롤할 수 있는 경우 이 컨트롤 패턴을 구현합니다.|  
  
<a name="Required_UI_Automation_Events"></a>   
## 필요한 UI 자동화 이벤트  
 다음 표에서는 모든 창 컨트롤에서 지원되는 데 필요한 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 이벤트를 나열하여 보여줍니다. 이벤트에 대한 자세한 내용은 [UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md)를 참조하세요.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 이벤트|지원\/값|노트|  
|-------------------------------------------------------------------------------|-----------|--------|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowClosedEvent>|Never|없음|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowOpenedEvent>|Never|없음|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AsyncContentLoadedEvent>|필수|없음|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> 속성 변경 이벤트.|필수|없음|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> 속성 변경 이벤트.|필수|없음|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 속성 변경 이벤트.|필수|없음|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> 속성 변경 이벤트.|종속|없음|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> 속성 변경 이벤트.|종속|없음|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> 속성 변경 이벤트.|종속|없음|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> 속성 변경 이벤트.|종속|없음|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> 속성 변경 이벤트.|종속|없음|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> 속성 변경 이벤트.|종속|없음|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowVisualStateProperty> 속성 변경 이벤트.|Never|없음|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|필수|없음|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|필수|없음|  
  
<a name="Pane_Control_Type_Example"></a>   
## Pane 컨트롤 형식 예제  
 다음 그림은 창 컨트롤 형식을 구현하는 컨트롤을 보여줍니다.  
  
 ![두 개의 창이 있는 애플릿 창의 스크린 샷](../../../docs/framework/ui-automation/media/uiauto-pane.png "uiauto\_pane")  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 트리 \- 컨트롤 뷰|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 트리 \- 콘텐츠 뷰|  
|---------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|  
|<ul><li>창</li><li>Tree\(스크롤 패턴\)<br /><br /> <ul><li>TreeItem</li><li>창</li><li>Edit\(스크롤 패턴\)</li></ul></li></ul>|-   창<br />-   Tree\(스크롤 패턴\)<br />-   TreeItem<br />-   …Pane<br />-   편집<br />-   \(스크롤 패턴\)|  
  
## 참고 항목  
 <xref:System.Windows.Automation.ControlType.Pane>   
 [UI Automation Control Types Overview](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)   
 [UI Automation Overview](../../../docs/framework/ui-automation/ui-automation-overview.md)