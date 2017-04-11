---
title: "연결 쿼리 예제(C#) | Microsoft 문서"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5426fbf710917b537d44e25966a8bc51d78f298e
ms.lasthandoff: 03/13/2017


---
# <a name="chaining-queries-example-c"></a>연결 쿼리 예제(C#)
이 예제에서는 이전 예제를 기반으로 하며 지연된 실행과 지연 계산을 모두 사용하는 두 쿼리를 연결할 때 발생하는 상황을 보여 줍니다.  
  
## <a name="example"></a>예제  
 이 예제에는 지정된 문자열을 소스 컬렉션의 모든 문자열에 추가한 다음 새 문자열을 생성하는 `AppendString` 확장 메서드가 추가로 도입되었습니다.  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source >{0}<", str);  
            yield return str.ToUpper();  
        }  
    }  
  
    public static IEnumerable<string>  
      AppendString(this IEnumerable<string> source, string stringToAppend)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("AppendString: source >{0}<", str);  
            yield return str + stringToAppend;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        IEnumerable<string> q1 =  
            from s in stringArray.ConvertCollectionToUpperCase()  
            select s;  
  
        IEnumerable<string> q2 =  
            from s in q1.AppendString("!!!")  
            select s;  
  
        foreach (string str in q2)  
        {  
            Console.WriteLine("Main: str >{0}<", str);  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
 이 예제는 다음과 같은 출력을 생성합니다.  
  
```  
ToUpper: source >abc<  
AppendString: source >ABC<  
Main: str >ABC!!!<  
  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
  
```  
  
 이 예제에서 각 확장 메서드가 소스 컬렉션의 항목마다 한 번씩 작동하는 것을 확인할 수 있습니다.  
  
 이 예제에서 알아 두어야 할 점은 컬렉션을 생성하는 쿼리를 연결했지만 중간 컬렉션이 구체화되지 않는다는 것입니다. 대신 각 항목이 한 지연 메서드에서 다음 지연 메서드로 전달됩니다. 이렇게 하면 먼저 문자열 배열을 하나 가져온 다음 대문자로 변환된 두 번째 문자열 배열을 만들고 마지막으로 각 문자열 끝에 느낌표가 추가된 세 번째 문자열 배열을 만드는 방법보다 훨씬 적은 메모리를 사용합니다.  
  
 이 자습서의 다음 항목에서는 중간 구체화를 보여 줍니다.  
  
-   [중간 구체화(C#)](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)  
  
## <a name="see-also"></a>참고 항목  
 [자습서: 여러 쿼리 연결(C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)