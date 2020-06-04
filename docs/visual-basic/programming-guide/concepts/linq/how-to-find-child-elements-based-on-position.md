---
title: 'Postupy: Vyhledání podřízených elementů na základě pozice (XPath – LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 6831e1db-5e97-444f-a7a1-d0a87104b005
ms.openlocfilehash: d6dd1150ae3e4ad586e476b777b1f7d47d60c261
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405258"
---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-visual-basic"></a>Postupy: hledání podřízených elementů na základě pozice (XPath-LINQ to XML) (Visual Basic)
Někdy chcete najít prvky na základě jejich pozice. Je možné, že budete chtít najít druhý prvek nebo můžete chtít najít třetí prostřednictvím pátého prvku.  
  
 Výraz XPath je:  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 Existují dva přístupy k zápisu tohoto [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazu opožděným způsobem. Můžete použít <xref:System.Linq.Enumerable.Skip%2A> <xref:System.Linq.Enumerable.Take%2A> operátory a, nebo můžete použít <xref:System.Linq.Enumerable.Where%2A> přetížení, které přijímá index. Při použití <xref:System.Linq.Enumerable.Where%2A> přetížení použijte lambda výraz, který přijímá dva argumenty. Následující příklad ukazuje obě metody výběru na základě pozice.  
  
## <a name="example"></a>Příklad  
 Tento příklad najde druhý prostřednictvím čtvrtého `Test` prvku. Výsledkem je kolekce prvků.  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: testovací konfigurace (LINQ to XML)](sample-xml-file-test-configuration-linq-to-xml.md).  
  
```vb  
Dim testCfg As XElement = XElement.Load("TestConfig.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    testCfg.Elements("Test").Skip(1).Take(3)  
  
'LINQ to XML query  
Dim list2 As IEnumerable(Of XElement) = _  
    testCfg.Elements("Test"). _  
    Where(Function(ByVal el, ByVal idx) idx >= 1 And idx <= 3)  
  
' XPath expression  
Dim list3 As IEnumerable(Of XElement) = _  
    testCfg.XPathSelectElements("Test[position() >= 2 and position() <= 4]")  
  
If list1.Count() = list2.Count() And _  
       list1.Count() = list3.Count() And _  
       list1.Intersect(list2).Count() = list1.Count() And _  
       list1.Intersect(list3).Count() = list1.Count() Then  
  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```console  
Results are identical  
<Test TestId="0002" TestType="CMD">  
  <Name>Find succeeding characters</Name>  
  <CommandLine>Examp2.EXE</CommandLine>  
  <Input>abc</Input>  
  <Output>def</Output>  
</Test>  
<Test TestId="0003" TestType="GUI">  
  <Name>Convert multiple numbers to strings</Name>  
  <CommandLine>Examp2.EXE /Verbose</CommandLine>  
  <Input>123</Input>  
  <Output>One Two Three</Output>  
</Test>  
<Test TestId="0004" TestType="GUI">  
  <Name>Find correlated key</Name>  
  <CommandLine>Examp3.EXE</CommandLine>  
  <Input>a1</Input>  
  <Output>b1</Output>  
</Test>  
```  
  
## <a name="see-also"></a>Viz také

- [LINQ to XML pro uživatele XPath (Visual Basic)](linq-to-xml-for-xpath-users.md)
