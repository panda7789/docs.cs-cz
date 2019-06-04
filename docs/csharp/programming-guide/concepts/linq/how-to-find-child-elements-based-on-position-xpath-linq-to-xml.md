---
title: 'Postupy: Vyhledání podřízených elementů na základě pozice (XPath – LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: e35bb269-ec86-4c96-8321-12491a0eb2c3
ms.openlocfilehash: b889c727fb59853cabc6f238c574764700dbbf3e
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485618"
---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-c"></a><span data-ttu-id="9736a-102">Postupy: Vyhledání podřízených elementů na základě pozice (XPath – LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="9736a-102">How to: Find Child Elements Based on Position (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="9736a-103">Někdy budete chtít najít prvky založené na jejich umístění.</span><span class="sxs-lookup"><span data-stu-id="9736a-103">Sometimes you want to find elements based on their position.</span></span> <span data-ttu-id="9736a-104">Můžete chtít najít druhý element nebo můžete chtít najít třetí prostřednictvím pátého prvku pole.</span><span class="sxs-lookup"><span data-stu-id="9736a-104">You might want to find the second element, or you might want to find the third through the fifth element.</span></span>  
  
 <span data-ttu-id="9736a-105">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="9736a-105">The XPath expression is:</span></span>  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 <span data-ttu-id="9736a-106">Existují dva přístupy k psaní to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazu opožděné způsobem.</span><span class="sxs-lookup"><span data-stu-id="9736a-106">There are two approaches to writing this [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query in a lazy way.</span></span> <span data-ttu-id="9736a-107">Můžete použít <xref:System.Linq.Enumerable.Skip%2A> a <xref:System.Linq.Enumerable.Take%2A> operátory, nebo můžete použít <xref:System.Linq.Enumerable.Where%2A> přetížení přebírající indexu.</span><span class="sxs-lookup"><span data-stu-id="9736a-107">You can use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> operators, or you can use the <xref:System.Linq.Enumerable.Where%2A> overload that takes an index.</span></span> <span data-ttu-id="9736a-108">Při použití <xref:System.Linq.Enumerable.Where%2A> přetížení, můžete použít výraz lambda, který přebírá dva argumenty.</span><span class="sxs-lookup"><span data-stu-id="9736a-108">When you use the <xref:System.Linq.Enumerable.Where%2A> overload, you use a lambda expression that takes two arguments.</span></span> <span data-ttu-id="9736a-109">Následující příklad ukazuje obě metody na základě pozice výběru.</span><span class="sxs-lookup"><span data-stu-id="9736a-109">The following example shows both methods of selecting based on position.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9736a-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="9736a-110">Example</span></span>  
 <span data-ttu-id="9736a-111">Tento příklad vyhledá druhé až čtvrté `Test` elementu.</span><span class="sxs-lookup"><span data-stu-id="9736a-111">This example finds the second through the fourth `Test` element.</span></span> <span data-ttu-id="9736a-112">Výsledkem je kolekci elementů.</span><span class="sxs-lookup"><span data-stu-id="9736a-112">The result is a collection of elements.</span></span>  
  
 <span data-ttu-id="9736a-113">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Otestujte konfiguraci (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9736a-113">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="9736a-114">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="9736a-114">This example produces the following output:</span></span>  
  
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
