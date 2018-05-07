---
title: 'Postupy: hledání podřízených elementů na základě pozice (XPath-technologie LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: e35bb269-ec86-4c96-8321-12491a0eb2c3
ms.openlocfilehash: ffe10bd5b263e56b6f2ee1708688523a2b0dd018
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-c"></a>Postupy: hledání podřízených elementů na základě pozice (XPath-technologie LINQ to XML) (C#)
Někdy budete chtít najít elementy, které jsou založeny na jejich umístění. Můžete chtít najít druhý prvkem, nebo můžete chtít najít třetí prostřednictvím páté elementu.  
  
 Výraz XPath je:  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 Existují dva přístupy k zápisu to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazu opožděné způsobem. Můžete použít <xref:System.Linq.Enumerable.Skip%2A> a <xref:System.Linq.Enumerable.Take%2A> operátory, nebo můžete použít <xref:System.Linq.Enumerable.Where%2A> přetížení, které přijímá indexu. Při použití <xref:System.Linq.Enumerable.Where%2A> přetížení, použijte výraz lambda, která přebírá dva argumenty. Následující příklad ukazuje obě metody výběru na základě pozice.  
  
## <a name="example"></a>Příklad  
 Tento příklad vyhledá druhý prostřednictvím čtvrtý `Test` elementu. Výsledkem je kolekci elementů.  
  
 Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: Konfigurace testu (technologie LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).  
  
```csharp  
XElement testCfg = XElement.Load("TestConfig.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    testCfg  
    .Elements("Test")  
    .Skip(1)  
    .Take(3);  
  
// LINQ to XML query  
IEnumerable<XElement> list2 =  
    testCfg  
    .Elements("Test")  
    .Where((el, idx) => idx >= 1 && idx <= 3);  
  
// XPath expression  
IEnumerable<XElement> list3 =  
  testCfg.XPathSelectElements("Test[position() >= 2 and position() <= 4]");  
  
if (list1.Count() == list2.Count() &&  
    list1.Count() == list3.Count() &&  
    list1.Intersect(list2).Count() == list1.Count() &&  
    list1.Intersect(list3).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
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
 [Technologie LINQ to XML pro uživatele XPath (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
