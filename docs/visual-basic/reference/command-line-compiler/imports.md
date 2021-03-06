---
title: "/imports (Visual Basic) | Microsoft 문서"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
caps.latest.revision: 15
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
ms.openlocfilehash: 1dcbba442413dba63aef31fd40a511bad5e8217b
ms.lasthandoff: 03/13/2017

---
# <a name="imports-visual-basic"></a>/imports(Visual Basic)
지정된 된 어셈블리에서 네임 스페이스를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```  
/imports:namespaceList  
```  
  
## <a name="arguments"></a>인수  
  
|용어|정의|  
|---|---|  
|`namespaceList`|필수 요소. 가져올 네임 스페이스의 쉼표로 구분 된 목록입니다.|  
  
## <a name="remarks"></a>주의  
 `/imports` 옵션 현재 소스 파일 또는 참조 된 어셈블리에서 집합 내에 정의 된 모든 네임 스페이스를 가져옵니다.  
  
 지정 된 네임 스페이스의 멤버 `/imports` 컴파일할 때 모든 소스 코드 파일에 사용할 수 있습니다. 사용 하 여는 [Imports 문 (.NET Namespace 및 형식)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) 단일 소스 코드 파일의 네임 스페이스를 사용 합니다.  
  
|설정 하려면 Visual Studio 통합된 개발 환경에서 /imports|  
|---|  
|1.  **솔루션 탐색기**에서 프로젝트를 선택합니다. 에 **프로젝트** 메뉴를 클릭 하 여 **속성**합니다. 자세한 내용은 [프로젝트 디자이너 소개](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)를 참조하세요.<br />2.  클릭 하 고 **참조** 탭 합니다.<br />3.  네임 스페이스 이름 옆에 있는 상자에 입력 된 **사용자 가져오기 추가** 단추입니다.<br />4.  클릭 하 고 **사용자 가져오기 추가** 단추입니다.|  
  
## <a name="example"></a>예제  
 다음 코드를 컴파일한 경우 `/imports:system` 지정 됩니다.  
  
 [!code-vb[VbVbalrCompiler #&21;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/imports_1.vb)]  
  
## <a name="see-also"></a>참고 항목  
 [Visual Basic 명령줄 컴파일러](../../../visual-basic/reference/command-line-compiler/index.md)   
 [참조 및 Imports 문](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)   
 [샘플 컴파일 명령줄](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
