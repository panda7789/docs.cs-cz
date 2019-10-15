---
title: 'Postupy: Vyhledání bezprostředního předchozího uzlu na stejné úrovni (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: ec046283-9fe2-4440-b295-860bf700099d
ms.openlocfilehash: bc54239d2ddaafcc46413ed13c274449daaba0c7
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320605"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-visual-basic"></a>Postupy: Vyhledání bezprostředního předchozího uzlu na stejné úrovni (XPath-LINQ to XML) (Visual Basic)
Někdy chcete najít bezprostřední předchozí položku na stejné úrovni jako uzel. Z důvodu rozdílu v sémantikě pozičních predikátů pro předchozí osy na stejné úrovni v cestě XPath a na rozdíl od [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] se jedná o jedno z zajímavějších porovnání.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu používá dotaz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] operátor <xref:System.Linq.Enumerable.Last%2A> k nalezení posledního uzlu v kolekci, který vrátila <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>. Naopak výraz XPath používá predikát s hodnotou 1 pro nalezení bezprostředně předcházejícího prvku.  
  
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
  
```console
Results are identical  
<Child3 />  
```  
  
## <a name="see-also"></a>Viz také:

- [LINQ to XML pro uživatele XPath (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
