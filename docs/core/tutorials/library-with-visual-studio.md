---
title: "Visual Studio 2017에서 C# 및 .NET Core를 사용하여 .NET Standard 클래스 라이브러리 빌드"
description: "Visual Studio 2017을 사용하여 C#으로 작성된 .NET Standard 클래스 라이브러리를 만드는 방법을 알아봅니다."
keywords: ".NET Core, .NET Standard 클래스 라이브러리, Visual Studio 2017"
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: c849ca26-6a25-4d35-9544-f343af88e0e7
ms.translationtype: HT
ms.sourcegitcommit: 3a25c1c3b540bac8ef963a8bbf708b0700c3e9e2
ms.openlocfilehash: 8b86f8f9cd02484cb91af3206606aced8fed1ecd
ms.contentlocale: ko-kr
ms.lasthandoff: 08/12/2017

---
# <a name="building-a-class-library-with-c-and-net-core-in-visual-studio-2017"></a>Visual Studio 2017에서 C# 및 .NET Core로 클래스 라이브러리 빌드

*클래스 라이브러리*는 응용 프로그램에서 호출되는 형식 및 메서드를 정의합니다. .NET Standard 2.0을 대상으로 하는 클래스 라이브러리는 .NET Standard의 해당 버전을 지원하는 모든 .NET 구현에서 라이브러리를 호출할 수 있습니다. 클래스 라이브러리를 마칠 때 타사 구성 요소로 배포할지 또는 하나 이상의 응용 프로그램과 함께 번들 구성 요소로 포함할지 결정할 수 있습니다.

> [!NOTE]
> .NET Standard 버전 및 지원되는 플랫폼 목록은 [.NET Standard](../../standard/net-standard.md)를 참조하세요.

이 항목에서는 단일 문자열 처리 메서드를 포함하는 간단한 유틸리티 라이브러리를 만들어 보겠습니다. <xref:System.String> 클래스의 멤버인 것처럼 호출할 수 있도록 [확장 메서드](../../csharp/programming-guide/classes-and-structs/extension-methods.md)로 구현하겠습니다.

## <a name="creating-a-class-library-solution"></a>클래스 라이브러리 솔루션 만들기

먼저 클래스 라이브러리 프로젝트의 솔루션과 관련 프로젝트를 만들어 보겠습니다. Visual Studio 솔루션은 하나 이상의 프로젝트에 대한 컨테이너로 작동합니다. 솔루션을 만들려면

1. Visual Studio 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

1. **새 프로젝트** 대화 상자에서 **기타 프로젝트 형식** 노드를 확장하고 **Visual Studio 솔루션**을 선택합니다. 솔루션의 이름을 "ClassLibraryProjects"로 지정하고 **확인** 단추를 선택합니다.

   ![새 프로젝트 대화 상자](./media/library-with-visual-studio/newproject.png)

## <a name="creating-the-class-library-project"></a>클래스 라이브러리 프로젝트 만들기

클래스 라이브러리 프로젝트를 만듭니다.

1. **솔루션 탐색기**에서 **ClassLibraryProjects** 솔루션 파일을 마우스 오른쪽 단추로 클릭하고 상황에 맞는 메뉴에서 **추가** > **새 프로젝트**를 선택합니다.

1. **새 프로젝트 추가** 대화 상자에서 **Visual C#** 노드를 확장하고 **.NET Standard** 노드, **클래스 라이브러리(.NET Standard)** 프로젝트 템플릿을 차례로 선택합니다. **이름** 텍스트 상자에 프로젝트 이름으로 "StringLibrary"를 입력합니다. **확인**을 선택하여 클래스 라이브러리 프로젝트를 만듭니다.

   ![새 프로젝트 추가 대화 상자](./media/library-with-visual-studio/libproject.png)

   그런 다음 코드 창이 Visual Studio 개발 환경에서 열립니다.

   ![기본 클래스 라이브러리 템플릿 코드를 보여 주는 Visual Studio 응용 프로그램 창](./media/library-with-visual-studio/stringlibrary.png)

1. 라이브러리에 올바른 버전의 .NET Standard가 대상으로 지정되었는지 확인합니다. **솔루션 탐색기** 창에서 라이브러리 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다. **대상 프레임워크** 텍스트 상자에 .NET Standard 2.0을 대상으로 하는 것이 표시됩니다.

   ![클래스 라이브러리에 대한 프로젝트 속성](./media/library-with-visual-studio/properties.png)

1. 코드 창의 코드를 다음 코드로 바꾸고 파일을 저장합니다.

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   클래스 라이브러리 `UtilityLibraries.StringLibrary`에는 `StartsWithUpper`라는 메서드가 포함됩니다. 이 메서드는 현재 문자열 인스턴스가 대문자로 시작하는지 여부를 나타내는 <xref:System.Boolean> 값을 반환합니다. 유니코드 표준은 대문자와 소문자를 구분합니다. <xref:System.Char.IsUpper(System.Char)?displayProperty=fullName> 메서드는 문자가 대문자인 경우 `true`를 반환합니다.

1. 메뉴 모음에서 **빌드** > **솔루션 빌드**를 선택합니다. 프로젝트가 오류 없이 컴파일되어야 합니다.

   ![빌드에 성공했음을 표시하는 출력 창](./media/library-with-visual-studio/buildsucceeds.png)

## <a name="next-step"></a>다음 단계

라이브러리를 성공적으로 빌드했습니다. 해당 메서드를 호출하지 않았으므로 예상대로 작동하는지 알지 못합니다. 라이브러리 개발의 다음 단계는 [단위 테스트 프로젝트](testing-library-with-visual-studio.md)를 사용하여 테스트하는 것입니다.
