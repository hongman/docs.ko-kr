---
title: "방법: 선행 형제 찾기(XPath 및 LINQ to XML)(C#)"
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
ms.assetid: b281ff99-d08a-43d0-bea1-eff831b2f8ae
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c49dd8998b0ad1e2a579b44f07462fb1111f3094
ms.contentlocale: ko-kr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-find-preceding-siblings-xpath-linq-to-xml-c"></a>방법: 선행 형제 찾기(XPath 및 LINQ to XML)(C#)
이 항목에서는 XPath `preceding-sibling` 축과 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 자식 <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName> 축을 비교합니다.  
  
 XPath 식은 다음과 같습니다.  
  
 `preceding-sibling::*`  
  
 <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> 및 <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName>의 결과는 문서 순서로 되어 있습니다.  
  
## <a name="example"></a>예제  
 다음 예제에서는 `FullAddress` 요소를 찾은 다음 `preceding-sibling` 축을 사용하여 이전 요소를 검색합니다.  
  
 이 예제에서는 XML 문서 [샘플 XML 파일: 고객 및 주문(LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md)을 사용합니다.  
  
```csharp  
XElement co = XElement.Load("CustomersOrders.xml");  
  
XElement add = co.Element("Customers").Element("Customer").Element("FullAddress");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 = add.ElementsBeforeSelf();  
  
// XPath expression  
IEnumerable<XElement> list2 = add.XPathSelectElements("preceding-sibling::*");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list2)  
    Console.WriteLine(el);  
```  
  
 이 예제는 다음과 같은 출력을 생성합니다.  
  
```  
Results are identical  
<CompanyName>Great Lakes Food Market</CompanyName>  
<ContactName>Howard Snyder</ContactName>  
<ContactTitle>Marketing Manager</ContactTitle>  
<Phone>(503) 555-7555</Phone>  
```  
  
## <a name="see-also"></a>참고 항목  
 [XPath 사용자를 위한 LINQ to XML(C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)

