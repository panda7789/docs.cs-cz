---
title: "Postupy: vyhledání okamžitou předchozí stejné úrovni (XPath-technologie LINQ to XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec046283-9fe2-4440-b295-860bf700099d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6eb74dc4c106deadb92da1414e359d567fda6df
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-visual-basic"></a>Postupy: vyhledání okamžitou předchozí stejné úrovni (XPath-technologie LINQ to XML) (Visual Basic)
Někdy budete chtít najít okamžitou předchozí položky do uzlu. Kvůli rozdílu ve sémantika poziční predikáty pro předchozí na stejné úrovni osy v XPath naproti tomu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], to je jedno z zajímavějšího porovnání.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotaz používá <xref:System.Linq.Enumerable.Last%2A> operátor najít poslední uzel v kolekci vrácený <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>. Výraz XPath naopak používá k nalezení okamžitě předchozí prvek predikát s hodnotou 1.  
  
```vb  
Dim root As XElement = _   
    <Root>  
        <Child1/>  
        <Child2/>  
        <Child3/>  
        <Child4/>  
    </Root>  
Dim child4 As XElement = root.Element("Child4")  
  
' LINQ to XML query  
Dim el1 As XElement = child4.ElementsBeforeSelf().Last()  
  
' XPath expression  
Dim el2 As XElement = _  
    DirectCast(child4.XPathEvaluate("preceding-sibling::*[1]"),  _  
    IEnumerable).Cast(Of XElement)().First()  
  
If el1 Is el2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(el1)  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```  
Results are identical  
<Child3 />  
```  
  
## <a name="see-also"></a>Viz také  
 [Technologie LINQ to XML pro uživatele XPath (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
