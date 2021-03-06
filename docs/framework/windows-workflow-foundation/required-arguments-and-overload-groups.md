---
title: "필수 인수 및 오버로드 그룹 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 필수 인수 및 오버로드 그룹
활동을 실행하기 위해 특정 인수를 바인딩하도록 활동을 구성할 수 있습니다.`RequiredArgument` 특성은 활동의 특정 인수가 필수 인수임을 나타내고 `OverloadGroup` 특성은 필수 인수 범주를 그룹화하는 데 사용됩니다.활동 작성자는 특성을 사용하여 단순 활동 유효성 검사 구성 또는 복합 활동 유효성 검사 구성을 제공할 수 있습니다.  
  
## 필수 인수 사용  
 활동에서 `RequiredArgument` 특성을 사용하려면 <xref:System.Activities.RequiredArgumentAttribute>를 사용하여 원하는 인수를 나타냅니다.이 예제에서는 두 필수 인수를 가진 `Add` 활동을 정의합니다.  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 XAML에서는 또한 <xref:System.Activities.RequiredArgumentAttribute>를 사용하여 필수 인수를 나타냅니다.이 예제에서 `Add` 활동은 세 인수를 사용하여 정의되며 <xref:System.Activities.Statements.Assign%601> 활동을 사용하여 추가 작업을 수행합니다.  
  
```xaml  
<Activity x:Class="ValidationDemo.Add" ...>  
  <x:Members>  
    <x:Property Name="Operand1" Type="InArgument(x:Int32)">  
      <x:Property.Attributes>  
        <RequiredArgumentAttribute />  
      </x:Property.Attributes>  
    </x:Property>  
    <x:Property Name="Operand2" Type="InArgument(x:Int32)">  
      <x:Property.Attributes>  
        <RequiredArgumentAttribute />  
      </x:Property.Attributes>  
    </x:Property>  
    <x:Property Name="Result" Type="OutArgument(x:Int32)" />  
  </x:Members>  
  <Assign>  
    <Assign.To>  
      <OutArgument x:TypeArguments="x:Int32">[Result]</OutArgument>  
    </Assign.To>  
    <Assign.Value>  
      <InArgument x:TypeArguments="x:Int32">[Operand1 + Operand2]</InArgument>  
    </Assign.Value>  
  </Assign>  
</Activity>  
```  
  
 활동을 사용할 때 필수 인수가 바인딩되지 않을 경우 다음 유효성 검사 오류가 반환됩니다.  
  
 **필수 작업 인수 'Operand1'의 값을 제공하지 않았습니다.**   
> [!NOTE]
>  유효성 검사 오류 및 경고를 검사하고 처리하는 방법[!INCLUDE[crabout](../../../includes/crabout-md.md)][활동 유효성 검사 호출](../../../docs/framework/windows-workflow-foundation//invoking-activity-validation.md)을 참조하십시오.  
  
## 오버로드 그룹 사용  
 오버로드 그룹은 활동에서 유효한 인수 조합을 나타내는 메서드를 제공합니다.인수는 <xref:System.Activities.OverloadGroupAttribute>를 사용하여 그룹화됩니다.각 그룹에는 <xref:System.Activities.OverloadGroupAttribute>에 의해 지정되는 이름이 주어집니다. 활동은 오버로드 그룹의 인수 집합 하나만 바인딩되는 경우에 유효합니다.[OverloadGroups](../../../docs/framework/windows-workflow-foundation/samples/overloadgroups.md) 샘플의 다음 예제에서는 `CreateLocation` 클래스를 정의합니다.  
  
```csharp  
class CreateLocation: Activity  
{  
    [RequiredArgument]  
    public InArgument<string> Name { get; set; }  
  
    public InArgument<string> Description { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G1")]  
    public InArgument<int> Latitude { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G1")]  
    public InArgument<int> Longitude { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    [OverloadGroup("G3")]  
    public InArgument<string> Street { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    public InArgument<string> City { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    public InArgument<string> State { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G3")]  
    public InArgument<int> Zip { get; set; }                  
}  
```  
  
 이 활동의 목적은 미국 내 위치를 지정하는 데 있습니다.활동 사용자는 세 인수 그룹 중 하나를 사용하여 위치를 지정할 수 있습니다.유효한 인수 조합을 지정하기 위해 세 가지 오버로드 그룹이 정의됩니다.`G1`에는 `Latitude` 및 `Longitude` 인수가 포함됩니다.`G2`에는 `Street`, `City` 및 `State`가 포함됩니다.`G3`에는 `Street` 및 `Zip`이 포함됩니다.`Name`도 필수 인수이지만 오버로드 그룹에 속하지는 않습니다.이 활동이 유효하려면 `Name`을 단 하나의 오버로드 그룹의 모든 인수와 함께 바인딩해야 합니다.  
  
 [Database Access Activities](../../../docs/framework/windows-workflow-foundation/samples/database-access-activities.md) 샘플의 다음 예제에서는 두 개의 오버로드 그룹 `ConnectionString` 및 `ConfigFileSectionName`이 있습니다.이 활동이 유효하려면 `ProviderName`과 `ConnectionString` 인수가 바인딩되어 있거나 `ConfigName` 인수가 바인딩되어 있어야 하지만 둘 다가 바인딩되어서는 안 됩니다.  
  
```  
Public class DbUpdate: AsyncCodeActivity  
{  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
  
    [DependsOn("Parameters")]  
    public OutArgument<int> AffectedRecords { get; set; }       
}  
```  
  
 오버로드 그룹 사용을 정의할 경우  
  
-   오버로드 그룹은 하위 집합 또는 동등한 다른 오버로드 그룹 집합이 될 수 없습니다.  
  
    > [!NOTE]
    >  그러나 이 규칙에는 한 가지 예외가 있습니다.오버로드 그룹이 다른 오버로드 그룹의 하위 집합이고, 하위 집합에 `RequiredArgument`가 `false`인 인수만 있을 경우 오버로드 그룹은 유효합니다.  
  
-   오버로드 그룹은 겹칠 수 있지만 그룹의 교집합에 오버로드 그룹 중 하나 또는 둘 다의 모든 필수 인수가 포함되는 경우 오류가 발생합니다.이전 예제에서 `G2` 및 `G3` 오버로드 그룹은 겹쳤지만 교집합에 오버로드 그룹 중 하나 또는 둘 다의 모든 인수가 포함되지 않았으므로 유효했습니다.  
  
 오버로드 그룹에서 인수를 바인딩할 경우  
  
-   오버로드 그룹은 그룹의 모든 `RequiredArgument` 인수가 바인딩되는 경우 바인딩된 것으로 간주됩니다.  
  
-   그룹에 `RequiredArgument` 인수가 없고 하나 이상의 인수가 바인딩되는 경우 그룹은 바인딩된 것으로 간주됩니다.  
  
-   하나의 오버로드 그룹에 `RequiredArgument` 인수가 없는 경우가 아니면 오버로드 그룹이 바인딩되지 않은 경우 유효성 검사 오류가 발생합니다.  
  
-   두 개 이상의 오버로드 그룹이 바인딩되는 경우, 즉 한 오버로드 그룹의 모든 필수 인수가 바인딩되고 다른 오버로드 그룹의 인수도 바인딩되는 경우 오류가 발생합니다.