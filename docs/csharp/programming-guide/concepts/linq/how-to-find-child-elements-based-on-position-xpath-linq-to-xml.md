---
title: 'Postupy: vyhledání podřízených elementů na základě pozice (XPath – LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: e35bb269-ec86-4c96-8321-12491a0eb2c3
ms.openlocfilehash: ffe10bd5b263e56b6f2ee1708688523a2b0dd018
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245051"
---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-c"></a><span data-ttu-id="2ff00-102">Postupy: vyhledání podřízených elementů na základě pozice (XPath – LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2ff00-102">How to: Find Child Elements Based on Position (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="2ff00-103">Někdy budete chtít najít prvky založené na jejich umístění.</span><span class="sxs-lookup"><span data-stu-id="2ff00-103">Sometimes you want to find elements based on their position.</span></span> <span data-ttu-id="2ff00-104">Můžete chtít najít druhý element nebo můžete chtít najít třetí prostřednictvím pátého prvku pole.</span><span class="sxs-lookup"><span data-stu-id="2ff00-104">You might want to find the second element, or you might want to find the third through the fifth element.</span></span>  
  
 <span data-ttu-id="2ff00-105">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="2ff00-105">The XPath expression is:</span></span>  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 <span data-ttu-id="2ff00-106">Existují dva přístupy k psaní to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazu opožděné způsobem.</span><span class="sxs-lookup"><span data-stu-id="2ff00-106">There are two approaches to writing this [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query in a lazy way.</span></span> <span data-ttu-id="2ff00-107">Můžete použít <xref:System.Linq.Enumerable.Skip%2A> a <xref:System.Linq.Enumerable.Take%2A> operátory, nebo můžete použít <xref:System.Linq.Enumerable.Where%2A> přetížení přebírající indexu.</span><span class="sxs-lookup"><span data-stu-id="2ff00-107">You can use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> operators, or you can use the <xref:System.Linq.Enumerable.Where%2A> overload that takes an index.</span></span> <span data-ttu-id="2ff00-108">Při použití <xref:System.Linq.Enumerable.Where%2A> přetížení, můžete použít výraz lambda, který přebírá dva argumenty.</span><span class="sxs-lookup"><span data-stu-id="2ff00-108">When you use the <xref:System.Linq.Enumerable.Where%2A> overload, you use a lambda expression that takes two arguments.</span></span> <span data-ttu-id="2ff00-109">Následující příklad ukazuje obě metody na základě pozice výběru.</span><span class="sxs-lookup"><span data-stu-id="2ff00-109">The following example shows both methods of selecting based on position.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ff00-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="2ff00-110">Example</span></span>  
 <span data-ttu-id="2ff00-111">Tento příklad vyhledá druhé až čtvrté `Test` elementu.</span><span class="sxs-lookup"><span data-stu-id="2ff00-111">This example finds the second through the fourth `Test` element.</span></span> <span data-ttu-id="2ff00-112">Výsledkem je kolekci elementů.</span><span class="sxs-lookup"><span data-stu-id="2ff00-112">The result is a collection of elements.</span></span>  
  
 <span data-ttu-id="2ff00-113">Tento příklad používá následujícího dokumentu XML: [ukázkový soubor XML: Konfigurace testu (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2ff00-113">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="2ff00-114">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="2ff00-114">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2ff00-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ff00-115">See Also</span></span>  
 [<span data-ttu-id="2ff00-116">LINQ to XML pro uživatele jazyka XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="2ff00-116">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
