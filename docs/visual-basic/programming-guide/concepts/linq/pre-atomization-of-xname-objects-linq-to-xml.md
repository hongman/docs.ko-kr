---
title: "XName 개체 (LINQ to XML)의 사전 원자화 (Visual Basic) | Microsoft 문서"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 06ea104b-f44c-4bb2-9c34-889ae025c80d
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 519b64a96e03e098d7325cfb779bcd5d53db3741
ms.lasthandoff: 03/13/2017


---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-visual-basic"></a>XName 개체 (LINQ to XML)의 사전 원자화 (Visual Basic)
LINQ to XML의에서 성능을 향상 시키는 한 가지 방법은 미리 원자화 하는 <xref:System.Xml.Linq.XName>개체.</xref:System.Xml.Linq.XName> 사전 원자화에 대 한 문자열을 할당 하는 의미는 <xref:System.Xml.Linq.XName>개체의 생성자를 사용 하 여 XML 트리를 만들기 전에 <xref:System.Xml.Linq.XElement>및 <xref:System.Xml.Linq.XAttribute>클래스.</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XName> 그런 다음 문자열을 생성자에 전달 하는 대신는 사용 하는 문자열에서 암시적으로 변환 <xref:System.Xml.Linq.XName>를 전달 하는 초기화 된 <xref:System.Xml.Linq.XName>개체.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XName>  
  
 이렇게 하면 특정 이름이 반복되는 대형 XML 트리를 만드는 경우 성능이 향상됩니다. 이 위해 선언 하 고 초기화 <xref:System.Xml.Linq.XName>XML 트리를 생성 하 고 사용 하기 전에 개체는 <xref:System.Xml.Linq.XName>요소 및 특성 이름에 대 한 문자열을 지정 하는 대신 개체.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XName> 이 방법을 사용하면 같은 이름으로 매우 많은 요소 또는 특성을 만드는 경우 상당한 성능상의 이점을 얻을 수 있습니다.  
  
 이 방법을 사용할지 여부를 결정하려면 사용자 시나리오를 사전 원자화해 보는 것이 좋습니다.  
  
## <a name="example"></a>예제  
 다음은 이에 대한 예입니다.  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 이 예제는 다음과 같은 출력을 생성합니다.  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 다음 예제에서는 XML 문서가 네임스페이스에 있는 동일한 방법을 보여 줍니다.  
  
```vb  
Dim aw As XNamespace = "http://www.adventure-works.com"  
Dim Root__1 As XName = aw + "Root"  
Dim Data As XName = aw + "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XAttribute(XNamespace.Xmlns + "aw", aw), New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 이 예제는 다음과 같은 출력을 생성합니다.  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 다음 예제는 실제로 사용될 수 있는 것과 더욱 유사한 코드입니다. 이 예제에서 요소의 내용은 쿼리를 통해 제공됩니다.  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim t1 As DateTime = DateTime.Now  
Dim root__2 As New XElement(Root__1, From i In System.Linq.Enumerable.Range(1, 100000)New XElement(Data, New XAttribute(ID, i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
 위 예제는 이름이 사전 원자화되지 않은 다음 예제보다 더 나은 성능을 제공합니다.  
  
```vb  
Dim t1 As DateTime = DateTime.Now  
Dim root As New XElement("Root", From i In System.Linq.Enumerable.Range(1, 100000)New XElement("Data", New XAttribute("ID", i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
## <a name="see-also"></a>참고 항목  
 [성능 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)   
 [원자화 XName 및 XNamespace 개체 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)