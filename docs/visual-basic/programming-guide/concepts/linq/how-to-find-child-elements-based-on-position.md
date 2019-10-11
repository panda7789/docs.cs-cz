---
title: 'Postupy: hledání podřízených elementů na základě pozice (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 6831e1db-5e97-444f-a7a1-d0a87104b005
ms.openlocfilehash: 11a9fdd7ed8565c38b0527d266af75b8fb611a20
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/10/2019
ms.locfileid: "72249694"
---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="8d78c-102">Postupy: hledání podřízených elementů na základě pozice (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d78c-102">How to: Find Child Elements Based on Position (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="8d78c-103">Někdy chcete najít prvky na základě jejich pozice.</span><span class="sxs-lookup"><span data-stu-id="8d78c-103">Sometimes you want to find elements based on their position.</span></span> <span data-ttu-id="8d78c-104">Je možné, že budete chtít najít druhý prvek nebo můžete chtít najít třetí prostřednictvím pátého prvku.</span><span class="sxs-lookup"><span data-stu-id="8d78c-104">You might want to find the second element, or you might want to find the third through the fifth element.</span></span>  
  
 <span data-ttu-id="8d78c-105">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="8d78c-105">The XPath expression is:</span></span>  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 <span data-ttu-id="8d78c-106">Existují dva přístupy k psaní tohoto fulltextového dotazu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] opožděným způsobem.</span><span class="sxs-lookup"><span data-stu-id="8d78c-106">There are two approaches to writing this [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query in a lazy way.</span></span> <span data-ttu-id="8d78c-107">Můžete použít operátory <xref:System.Linq.Enumerable.Skip%2A> a <xref:System.Linq.Enumerable.Take%2A> nebo můžete použít přetížení <xref:System.Linq.Enumerable.Where%2A>, které přijímá index.</span><span class="sxs-lookup"><span data-stu-id="8d78c-107">You can use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> operators, or you can use the <xref:System.Linq.Enumerable.Where%2A> overload that takes an index.</span></span> <span data-ttu-id="8d78c-108">Při použití přetížení <xref:System.Linq.Enumerable.Where%2A> použijete výraz lambda, který přijímá dva argumenty.</span><span class="sxs-lookup"><span data-stu-id="8d78c-108">When you use the <xref:System.Linq.Enumerable.Where%2A> overload, you use a lambda expression that takes two arguments.</span></span> <span data-ttu-id="8d78c-109">Následující příklad ukazuje obě metody výběru na základě pozice.</span><span class="sxs-lookup"><span data-stu-id="8d78c-109">The following example shows both methods of selecting based on position.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d78c-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="8d78c-110">Example</span></span>  
 <span data-ttu-id="8d78c-111">Tento příklad najde druhý prostřednictvím čtvrtého elementu `Test`.</span><span class="sxs-lookup"><span data-stu-id="8d78c-111">This example finds the second through the fourth `Test` element.</span></span> <span data-ttu-id="8d78c-112">Výsledkem je kolekce prvků.</span><span class="sxs-lookup"><span data-stu-id="8d78c-112">The result is a collection of elements.</span></span>  
  
 <span data-ttu-id="8d78c-113">Tento příklad používá následující dokument XML: [ukázkový soubor XML: testovací konfigurace (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8d78c-113">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="8d78c-114">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="8d78c-114">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8d78c-115">Související témata</span><span class="sxs-lookup"><span data-stu-id="8d78c-115">See also</span></span>

- [<span data-ttu-id="8d78c-116">LINQ to XML pro uživatele XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d78c-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
