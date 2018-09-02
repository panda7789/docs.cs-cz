---
title: 'Postupy: vyhledání podřízených elementů na základě pozice (XPath – LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 6831e1db-5e97-444f-a7a1-d0a87104b005
ms.openlocfilehash: 9f18da12786b4c44dc21e54c8d5020f49ef9ecb6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43390783"
---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-visual-basic"></a>Postupy: vyhledání podřízených elementů na základě pozice (XPath – LINQ to XML) (Visual Basic)
Někdy budete chtít najít prvky založené na jejich umístění. Můžete chtít najít druhý element nebo můžete chtít najít třetí prostřednictvím pátého prvku pole.  
  
 Výraz XPath je:  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 Existují dva přístupy k psaní to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazu opožděné způsobem. Můžete použít <xref:System.Linq.Enumerable.Skip%2A> a <xref:System.Linq.Enumerable.Take%2A> operátory, nebo můžete použít <xref:System.Linq.Enumerable.Where%2A> přetížení přebírající indexu. Při použití <xref:System.Linq.Enumerable.Where%2A> přetížení, můžete použít výraz lambda, který přebírá dva argumenty. Následující příklad ukazuje obě metody na základě pozice výběru.  
  
## <a name="example"></a>Příklad  
 Tento příklad vyhledá druhé až čtvrté `Test` elementu. Výsledkem je kolekci elementů.  
  
 Tento příklad používá následujícího dokumentu XML: [ukázkový soubor XML: Konfigurace testu (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).  
  
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
  
```  
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
 [LINQ to XML pro uživatele jazyka XPath (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
