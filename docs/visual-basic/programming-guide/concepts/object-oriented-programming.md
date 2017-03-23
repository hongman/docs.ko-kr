---
title: "개체 지향 프로그래밍 (Visual Basic) | Microsoft 문서"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d5491b3bd5a25908194d02063f688a319509bb77
ms.lasthandoff: 03/13/2017

---
# <a name="object-oriented-programming-visual-basic"></a>개체 지향 프로그래밍 (Visual Basic)
Visual Basic 캡슐화, 상속, 다형성 등 개체 지향 프로그래밍에 대 한 모든 지원을 제공 합니다.  
  
 *캡슐화* 관련된 속성, 메서드 및 기타 멤버의 그룹을 하나의 단위나 개체로 취급 하는 의미 합니다.  
  
 *상속* 기존 클래스를 기반으로 새 클래스를 만들 수 있는 능력을 나타냅니다.  
  
 *다형성* 동일한 속성 또는 메서드를 각각 다른 방식에서으로 구현 하는 경우에를 서로 바꾸어 사용할 수 있는 여러 클래스를 포함할 수 없음을 의미 합니다.  
  
 이 단원에서는 다음과 같은 개념에 대해 설명합니다.  
  
-   [클래스 및 개체](#Classes)  
  
    -   [클래스 멤버](#Members)  
  
         [속성 및 필드](#Properties)  
  
         [메서드](#Methods)  
  
         [생성자](#Constructors)  
  
         [소멸자](#Destructors)  
  
         [이벤트](#Events)  
  
         [중첩된 클래스](#NestedClasses)  
  
    -   [액세스 한정자 및 액세스 수준](#AccessModifiers)  
  
    -   [클래스 인스턴스화](#InstantiatingClasses)  
  
    -   [공유 클래스 및 멤버](#Static)  
  
    -   [익명 형식](#AnonymousTypes)  
  
-   [상속](#Inheritance)  
  
    -   [멤버 재정의](#Overriding)  
  
-   [인터페이스](#Interfaces)  
  
-   [제네릭](#Generics)  
  
-   [대리자](#Delegates)  
  
##  <a name="Classes"></a>클래스 및 개체  
 용어 *클래스* 및 *개체* 사용 되는 경우가 실제로 하지만 서로 교체 하 여 클래스를 설명는 *형식* 나타내고 개체는 사용 가능한 개체의 *인스턴스* 클래스입니다. 따라서, 개체를 만드는 작업 라고 *인스턴스화*합니다. 청사진에 비유한다면 클래스는 청사진이고 개체는 해당 청사진을 사용하여 만든 빌딩입니다.  
  
 클래스를 정의하려면  
  
```vb  
Class SampleClass  
End Class  
```  
  
 Visual Basic에서 밝은 버전의 클래스도 제공 *구조* 큰 개체 배열을 만들어야 하 고 실행 해야 할 때 유용 하는 메모리를 너무 많이 사용 하지 않아도 됩니다.  
  
 구조체를 정의하려면  
  
```vb  
Structure SampleStructure  
End Structure  
```  
  
 자세한 내용은 다음을 참조하세요.  
  
-   [Class 문](../../../visual-basic/language-reference/statements/class-statement.md)  
  
-   [Structure 문](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
###  <a name="Members"></a>클래스 멤버  
 각 클래스는 서로 다른 점이 *클래스 멤버* 클래스 데이터, 클래스 동작을 정의 하는 메서드 및 서로 다른 클래스와 개체 간의 통신을 제공 하는 이벤트를 설명 하는 속성을 포함 하는 합니다.  
  
####  <a name="Properties"></a>속성 및 필드  
 필드 및 속성은 개체가 포함하는 정보를 나타냅니다. 필드는 직접 읽거나 설정할 수 있기 때문에 변수와 비슷합니다.  
  
 필드를 정의하려면  
  
```vb  
Class SampleClass  
    Public SampleField As String  
End Class  
```  
  
 속성에는 값을 설정하고 가져오는 방법을 보다 세밀하게 제어할 수 있는 get 및 set 프로시저가 있습니다.  
  
 Visual Basic을 사용 하면 속성 값을 저장 하기 위한 전용 필드를 만들거나이 필드는 내부적으로 자동으로 만들고 속성 프로시저에 대 한 기본 논리를 제공 하는 소위 자동 구현 속성을 사용 하 여 있습니다.  
  
 자동 구현 속성을 정의하려면  
  
```vb  
Class SampleClass  
    Public Property SampleProperty as String  
End Class  
```  
  
 속성 값을 읽고 쓰기 위해 몇 가지 추가 작업을 수행해야 하는 경우 다음과 같이 속성 값을 저장하기 위한 필드를 정의하고, 속성 값을 저장 및 검색하기 위한 기본 논리를 제공합니다.  
  
```vb  
Class SampleClass  
    Private m_Sample As String  
    Public Property Sample() As String  
        Get  
            ' Return the value stored in the field.  
            Return m_Sample  
        End Get  
        Set(ByVal Value As String)  
            ' Store the value in the field.  
            m_Sample = Value  
        End Set  
    End Property  
End Class  
```  
  
 대부분의 속성에는 속성 값을 설정하고 가져오는 메서드나 프로시저가 있습니다. 그러나 읽기 전용 또는 쓰기 전용 속성을 만들어 속성을 수정하거나 읽지 못하도록 제한할 수도 있습니다. 이렇게 하려면 Visual Basic에서는 `ReadOnly` 및 `WriteOnly` 키워드를 사용하면 되고 그러나 자동 구현 속성 읽기 전용 또는 쓰기 전용일 수 없습니다.  
  
 자세한 내용은 다음을 참조하세요.  
  
-   [Property 문](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Get 문](../../../visual-basic/language-reference/statements/get-statement.md)  
  
-   [Set 문](../../../visual-basic/language-reference/statements/set-statement.md)  
  
-   [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)  
  
-   [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)  
  
####  <a name="Methods"></a>메서드  
 A *메서드* 개체에서 수행할 수 있는 작업입니다.  
  
> [!NOTE]
>  Visual Basic에서는 두 가지 방법으로 메서드를 만들 수 있습니다. 메서드가 값을 반환하지 않으면 `Sub` 문을 사용하고 메서드가 값을 반환하면 `Function` 문을 사용합니다.  
  
 클래스의 메서드를 정의하려면  
  
```vb  
Class SampleClass  
    Public Function SampleFunc(ByVal SampleParam As String)  
        ' Add code here  
    End Function  
End Class  
```  
  
 클래스가 여러 구현 소유할 수 또는 *오버 로드*, 매개 변수 또는 매개 변수 형식이 다른 동일한 메서드의 합니다.  
  
 메서드를 오버로드하려면  
  
```vb  
Overloads Sub Display(ByVal theChar As Char)  
    ' Add code that displays Char data.  
End Sub  
Overloads Sub Display(ByVal theInteger As Integer)  
    ' Add code that displays Integer data.  
End Sub  
```  
  
 대부분의 경우 클래스 정의 내에서 메서드를 선언하지만 그러나 Visual Basic에서는 *확장 메서드* 클래스의 실제 정의 밖에 있는 기존 클래스에 메서드를 추가할 수 있도록 합니다.  
  
 자세한 내용은 다음을 참조하세요.  
  
-   [Function 문](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Sub 문](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
-   [오버로드](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
-   [확장명 메서드](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
  
####  <a name="Constructors"></a>생성자  
 생성자는 지정된 형식의 개체를 만들 때 자동으로 실행되는 클래스 메서드로, 일반적으로 새 개체의 데이터 멤버를 초기화합니다. 생성자는 클래스를 만들 때 한 번만 실행할 수 있습니다. 또한 생성자의 코드는 항상 클래스의 다른 코드보다 먼저 실행됩니다. 그러나 다른 메서드를 만들 때와 동일한 방법으로 여러 생성자 오버로드를 만들 수 있습니다.  
  
 클래스의 생성자를 정의하려면  
  
```vb  
Class SampleClass  
    Sub New(ByVal s As String)  
        // Add code here.  
    End Sub  
End Class  
```  
  
 자세한 내용은 참조: [개체 수명: 개체가 만들어지고 소멸 되는 하는 방법을](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)합니다.  
  
####  <a name="Destructors"></a>소멸자  
 소멸자는 클래스의 인스턴스를 소멸하는 데 사용됩니다. .NET Framework에서는 응용 프로그램의 관리되는 개체에 대해 가비지 수집기가 자동으로 메모리를 할당하고 해제하지만 응용 프로그램에서 만들어지는 관리되지 않는 개체를 정리하려면 여전히 소멸자가 필요할 수 있습니다. 각 클래스에는 소멸자가 하나씩만 있을 수 있습니다.  
  
 소멸자 및.NET Framework의 가비지 수집에 대 한 자세한 내용은 참조 [가비지 수집](../../../standard/garbagecollection/index.md)합니다.  
  
####  <a name="Events"></a>이벤트  
 클래스나 개체에서는 특정 상황이 발생할 때 이벤트를 통해 다른 클래스나 개체에 이를 알려 줄 수 있습니다. 이벤트를 보냅니다 (또는 발생) 하는 클래스 라고는 *게시자* 되는 이벤트를 수신 (또는 처리) 클래스 라고 하 고 *구독자*합니다. 이벤트에 대 한 자세한 내용은 어떻게 발생 하 고 참조를 처리 된 [이벤트](http://msdn.microsoft.com/library/b6f65241-e0ad-4590-a99f-200ce741bb1f)합니다.  
  
-   이벤트를 선언 하려면 사용 된 [Event 문](../../../visual-basic/language-reference/statements/event-statement.md)합니다.  
  
-   이벤트를 발생 시키기 위해 사용 하 여는 [RaiseEvent 문](../../../visual-basic/language-reference/statements/raiseevent-statement.md)합니다.  
  
-   선언적 방식으로 이벤트 처리기를 지정 하려면는 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) 문 및 [처리](../../../visual-basic/language-reference/statements/handles-clause.md) 절.  
  
-   수 동적으로 추가, 제거 및 변경 이벤트와 연결 된 이벤트 처리기를 사용 하 여는 [AddHandler 문](../../../visual-basic/language-reference/statements/addhandler-statement.md) 및 [RemoveHandler 문](../../../visual-basic/language-reference/statements/removehandler-statement.md) 와 함께 [AddressOf 연산자](../../../visual-basic/language-reference/operators/addressof-operator.md)합니다.  
  
####  <a name="NestedClasses"></a>중첩된 클래스  
 다른 클래스 내에 정의 된 클래스 라고 *중첩*합니다. 기본적으로 중첩 클래스는 전용입니다.  
  
```vb  
Class Container  
    Class Nested  
    ' Add code here.  
    End Class  
End Class  
```  
  
 중첩 클래스의 인스턴스를 만들려면 다음과 같이 컨테이너 클래스의 이름, 점, 중첩 클래스의 이름을 차례로 입력합니다.  
  
```vb  
Dim nestedInstance As Container.Nested = New Container.Nested()  
```  
  
###  <a name="AccessModifiers"></a>액세스 한정자 및 액세스 수준  
 모든 클래스 및 클래스 멤버를 사용 하 여 다른 클래스에 제공할 액세스 수준을 지정할 수 *액세스 한정자*합니다.  
  
 다음과 같은 액세스 한정자를 사용할 수 있습니다.  
  
|Visual Basic 한정자|정의|  
|---------------------------|----------------|  
|[공용](../../../visual-basic/language-reference/modifiers/public.md)|동일한 어셈블리의 다른 코드나 해당 어셈블리를 참조하는 다른 어셈블리의 코드에서 형식이나 멤버에 액세스할 수 있습니다.|  
|[전용](../../../visual-basic/language-reference/modifiers/private.md)|동일한 클래스의 코드에서만 형식이나 멤버에 액세스할 수 있습니다.|  
|[보호됨](../../../visual-basic/language-reference/modifiers/protected.md)|동일한 클래스의 코드나 파생 클래스의 코드에서만 형식이나 멤버에 액세스할 수 있습니다.|  
|[Friend](../../../visual-basic/language-reference/modifiers/friend.md)|동일한 어셈블리의 코드에서는 형식이나 멤버에 액세스할 수 있지만 다른 어셈블리의 코드에서는 액세스할 수 없습니다.|  
|`Protected Friend`|동일한 어셈블리의 코드 또는 다른 어셈블리의 파생 클래스에서 형식이나 멤버에 액세스할 수 있습니다.|  
  
 자세한 내용은 참조 [Visual Basic의 액세스 수준을](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)합니다.  
  
###  <a name="InstantiatingClasses"></a>클래스 인스턴스화  
 개체를 만들려면 클래스를 인스턴스화하거나 클래스 인스턴스를 만들어야 합니다.  
  
```vb  
Dim sampleObject as New SampleClass()  
```  
  
 클래스를 인스턴스화한 후에는 인스턴스의 속성과 필드에 값을 할당하고 클래스 메서드를 호출할 수 있습니다.  
  
```vb  
' Set a property value.  
sampleObject.SampleProperty = "Sample String"  
' Call a method.  
sampleObject.SampleMethod()  
```  
  
 클래스를 인스턴스화하는 동안 속성에 값을 할당하려면 다음과 같이 개체 이니셜라이저를 사용합니다.  
  
```vb  
Dim sampleObject = New SampleClass With   
    {.FirstProperty = "A", .SecondProperty = "B"}  
```  
  
 자세한 내용은 다음을 참조하세요.  
  
-   [New 연산자](../../../visual-basic/language-reference/operators/new-operator.md)  
  
-   [개체 이니셜라이저: 명명된 형식과 익명 형식](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
  
###  <a name="Static"></a>공유 클래스 및 멤버  
 클래스의 공유 멤버 속성, 프로시저 또는 클래스의 모든 인스턴스에서 공유 되는 필드입니다.  
  
 정의 하려면 공유 멤버:  
  
```vb  
Class SampleClass  
    Public Shared SampleString As String = "Sample String"  
End Class  
```  
  
 공유 멤버에 액세스 하려면이 클래스의 개체를 만들지 않고 클래스의 이름을 사용 합니다.  
  
```vb  
MsgBox(SampleClass.SampleString)  
```  
  
 Visual Basic의 모듈은 공유 멤버에만 공유 있으며 인스턴스화할 수 없습니다. 공유 멤버 또한 액세스할 수 없습니다 공유 되지 않는 속성, 필드 또는 메서드  
  
 자세한 내용은 다음을 참조하세요.  
  
-   [공유](../../../visual-basic/language-reference/modifiers/shared.md)  
  
-   [Module 문](../../../visual-basic/language-reference/statements/module-statement.md)  
  
###  <a name="AnonymousTypes"></a>익명 형식  
 익명 형식을 사용하면 데이터 형식에 대한 클래스 정의를 작성하지 않고 개체를 만들 수 있습니다. 대신 컴파일러가 클래스를 생성합니다. 이 클래스는 사용할 수 있는 이름이 없고 개체를 선언할 때 지정하는 속성을 포함합니다.  
  
 익명 형식의 인스턴스를 만들려면  
  
```vb  
' sampleObject is an instance of a simple anonymous type.  
Dim sampleObject =   
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}  
```  
  
 자세한 내용은 참조: [익명 형식](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)합니다.  
  
##  <a name="Inheritance"></a>상속  
 상속을 사용하면 다른 클래스에 정의된 동작을 다시 사용, 확장 및 수정하는 새 클래스를 만들 수 있습니다. 멤버가 상속 되는 클래스 라고는 *기본 클래스*, 해당 멤버를 상속 하는 클래스 라고 하 고는 *파생 클래스*합니다. 하지만 Visual Basic의 모든 클래스에서 암시적으로 상속는 <xref:System.Object>.NET 클래스 계층 구조를 지원 하 고 모든 클래스에 하위 수준 서비스를 제공 하는 클래스입니다.</xref:System.Object>  
  
> [!NOTE]
>  Visual Basic 다중 상속을 지원 하지 않습니다. 즉, 파생된 클래스에 대 한 기본 클래스가 하나만 지정할 수 있습니다.  
  
 기본 클래스에서 상속하려면  
  
```vb  
Class DerivedClass  
    Inherits BaseClass  
End Class  
```  
  
 기본적으로 모든 클래스는 상속될 수 있지만 클래스가 기본 클래스로 사용되지 않아야 하는지 여부를 지정하거나 기본 클래스로만 사용될 수 있는 클래스를 만들 수도 있습니다.  
  
 클래스가 기본 클래스로 사용될 수 없도록 지정하려면  
  
```vb  
NotInheritable Class SampleClass  
End Class  
```  
  
 클래스가 기본 클래스로만 사용되고 인스턴스화되지 않도록 지정하려면  
  
```vb  
MustInherit Class BaseClass  
End Class  
```  
  
 자세한 내용은 다음을 참조하세요.  
  
-   [Inherits 문](../../../visual-basic/language-reference/statements/inherits-statement.md)  
  
-   [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
  
-   [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
  
###  <a name="Overriding"></a>멤버 재정의  
 기본적으로 파생 클래스는 해당 기본 클래스에서 모든 멤버를 상속합니다. 상속된 멤버의 동작을 변경하려면 해당 멤버를 재정의해야 합니다. 즉, 파생 클래스에 해당 메서드, 속성 또는 이벤트의 새로운 구현을 정의할 수 있습니다.  
  
 다음 한정자는 속성 및 메서드가 재정의되는 방식을 제어하는 데 사용됩니다.  
  
|Visual Basic 한정자|정의|  
|---------------------------|----------------|  
|[재정의 가능](../../../visual-basic/language-reference/modifiers/overridable.md)|파생 클래스에서 클래스 멤버를 재정의할 수 있도록 합니다.|  
|[재정의](../../../visual-basic/language-reference/modifiers/overrides.md)|기본 클래스에 정의된 가상(재정의 가능) 멤버를 재정의합니다.|  
|[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)|멤버가 상속 클래스에서 재정의되지 않도록 합니다.|  
|[MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)|파생 클래스에서 클래스 멤버가 재정의되도록 합니다.|  
|[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)|기본 클래스에서 상속된 멤버를 숨깁니다.|  
  
##  <a name="Interfaces"></a>인터페이스  
 인터페이스는 클래스와 마찬가지로 속성, 메서드 및 이벤트를 정의하지만 클래스와는 달리 구현을 제공하지 않습니다. 인터페이스는 클래스에 의해 구현되며 클래스와는 별개의 엔터티로 정의됩니다. 인터페이스는 계약을 나타내므로 인터페이스를 구현하는 클래스에서는 해당 인터페이스의 모든 부분을 정의된 그대로 정확하게 구현해야 합니다.  
  
 인터페이스를 정의하려면  
  
```vb  
Public Interface ISampleInterface  
    Sub DoSomething()  
End Interface  
```  
  
 클래스에서 인터페이스를 구현하려면  
  
```vb  
Class SampleClass  
    Implements ISampleInterface  
    Sub DoSomething  
        ' Method implementation.  
    End Sub  
End Class  
```  
  
 자세한 내용은 다음을 참조하세요.  
  
-   [인터페이스](../../../visual-basic/programming-guide/language-features/interfaces/index.md)  
  
-   [Interface 문](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
-   [Implements 문](../../../visual-basic/language-reference/statements/implements-statement.md)  
  
##  <a name="Generics"></a>제네릭  
 클래스, 구조체, 인터페이스 및 메서드는.NET Framework에 포함 될 수 있습니다 *형식 매개 변수* 저장 하거나 사용할 수 있는 개체의 형식을 정의 하는 합니다. 제네릭의 가장 일반적인 예는 컬렉션에 저장할 개체의 형식을 지정할 수 있는 컬렉션입니다.  
  
 제네릭 클래스를 정의하려면  
  
```vb  
Class SampleGeneric(Of T)  
    Public Field As T  
End Class  
```  
  
 제네릭 클래스의 인스턴스를 만들려면  
  
```vb  
Dim sampleObject As New SampleGeneric(Of String)  
sampleObject.Field = "Sample string"  
```  
  
 자세한 내용은 다음을 참조하세요.  
  
-   [제네릭](https://msdn.microsoft.com/library/ms172192)  
  
-   [Visual Basic의 제네릭 형식](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
  
##  <a name="Delegates"></a>대리자  
 A *위임* 메서드 시그니처를 정의 하는 형식이 고 호환 되는 시그니처가 있는 메서드에 대 한 참조를 제공할 수 있습니다. 대리자를 통해 메서드를 호출할 수 있습니다. 대리자는 메서드를 다른 메서드에 인수로 전달하는 데 사용됩니다.  
  
> [!NOTE]
>  이벤트 처리기는 대리자를 통해 호출되는 메서드라고 할 수 있습니다. 대리자를 사용 하 여 이벤트 처리에서 하는 방법에 대 한 자세한 내용은 참조 [이벤트](http://msdn.microsoft.com/library/b6f65241-e0ad-4590-a99f-200ce741bb1f)합니다.  
  
 대리자를 만들려면  
  
```vb  
Delegate Sub SampleDelegate(ByVal str As String)  
```  
  
 대리자가 지정한 시그니처와 일치하는 메서드에 대한 참조를 만들려면  
  
```vb  
Class SampleClass  
    ' Method that matches the SampleDelegate signature.  
    Sub SampleSub(ByVal str As String)  
        ' Add code here.  
    End Sub  
    ' Method that instantiates the delegate.  
    Sub SampleDelegateSub()  
        Dim sd As SampleDelegate = AddressOf SampleSub  
        sd("Sample string")  
    End Sub  
End Class  
```  
  
 자세한 내용은 다음을 참조하세요.  
  
-   [대리자](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
  
-   [Delegate 문](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
-   [AddressOf 연산자](../../../visual-basic/language-reference/operators/addressof-operator.md)  
  
## <a name="see-also"></a>참고 항목  
 [Visual Basic 프로그래밍 가이드](../../../visual-basic/programming-guide/index.md)