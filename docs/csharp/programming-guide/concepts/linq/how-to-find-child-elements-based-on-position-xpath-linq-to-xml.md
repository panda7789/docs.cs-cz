---
title: 'Postupy: Najde podřízené elementy na základě pozice (XPath-LINQ to XML) (C#).'
ms.date: 07/20/2015
ms.assetid: e35bb269-ec86-4c96-8321-12491a0eb2c3
ms.openlocfilehash: b55e2df5a97446da9d02fd3979f5d8d584228ba2
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593500"
---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-c"></a><span data-ttu-id="9b20f-102">Postupy: Najde podřízené elementy na základě pozice (XPath-LINQ to XML) (C#).</span><span class="sxs-lookup"><span data-stu-id="9b20f-102">How to: Find Child Elements Based on Position (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="9b20f-103">Někdy chcete najít prvky na základě jejich pozice.</span><span class="sxs-lookup"><span data-stu-id="9b20f-103">Sometimes you want to find elements based on their position.</span></span> <span data-ttu-id="9b20f-104">Je možné, že budete chtít najít druhý prvek nebo můžete chtít najít třetí prostřednictvím pátého prvku.</span><span class="sxs-lookup"><span data-stu-id="9b20f-104">You might want to find the second element, or you might want to find the third through the fifth element.</span></span>  
  
 <span data-ttu-id="9b20f-105">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="9b20f-105">The XPath expression is:</span></span>  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 <span data-ttu-id="9b20f-106">Existují dva přístupy k zápisu tohoto [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazu opožděným způsobem.</span><span class="sxs-lookup"><span data-stu-id="9b20f-106">There are two approaches to writing this [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query in a lazy way.</span></span> <span data-ttu-id="9b20f-107">Můžete použít <xref:System.Linq.Enumerable.Skip%2A> operátory a <xref:System.Linq.Enumerable.Take%2A> , <xref:System.Linq.Enumerable.Where%2A> nebo můžete použít přetížení, které přijímá index.</span><span class="sxs-lookup"><span data-stu-id="9b20f-107">You can use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> operators, or you can use the <xref:System.Linq.Enumerable.Where%2A> overload that takes an index.</span></span> <span data-ttu-id="9b20f-108">Při použití <xref:System.Linq.Enumerable.Where%2A> přetížení použijte lambda výraz, který přijímá dva argumenty.</span><span class="sxs-lookup"><span data-stu-id="9b20f-108">When you use the <xref:System.Linq.Enumerable.Where%2A> overload, you use a lambda expression that takes two arguments.</span></span> <span data-ttu-id="9b20f-109">Následující příklad ukazuje obě metody výběru na základě pozice.</span><span class="sxs-lookup"><span data-stu-id="9b20f-109">The following example shows both methods of selecting based on position.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b20f-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="9b20f-110">Example</span></span>  
 <span data-ttu-id="9b20f-111">Tento příklad najde druhý prostřednictvím čtvrtého `Test` prvku.</span><span class="sxs-lookup"><span data-stu-id="9b20f-111">This example finds the second through the fourth `Test` element.</span></span> <span data-ttu-id="9b20f-112">Výsledkem je kolekce prvků.</span><span class="sxs-lookup"><span data-stu-id="9b20f-112">The result is a collection of elements.</span></span>  
  
 <span data-ttu-id="9b20f-113">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Konfigurace testu (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9b20f-113">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="9b20f-114">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="9b20f-114">This example produces the following output:</span></span>  
  
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
