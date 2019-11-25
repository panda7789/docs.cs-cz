---
title: 'How to: Find Child Elements Based on Position (XPath-LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 6831e1db-5e97-444f-a7a1-d0a87104b005
ms.openlocfilehash: c3062963c6144dfafed8b49410208f480c273ec9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349087"
---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="e1d64-102">How to: Find Child Elements Based on Position (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1d64-102">How to: Find Child Elements Based on Position (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="e1d64-103">Sometimes you want to find elements based on their position.</span><span class="sxs-lookup"><span data-stu-id="e1d64-103">Sometimes you want to find elements based on their position.</span></span> <span data-ttu-id="e1d64-104">You might want to find the second element, or you might want to find the third through the fifth element.</span><span class="sxs-lookup"><span data-stu-id="e1d64-104">You might want to find the second element, or you might want to find the third through the fifth element.</span></span>  
  
 <span data-ttu-id="e1d64-105">The XPath expression is:</span><span class="sxs-lookup"><span data-stu-id="e1d64-105">The XPath expression is:</span></span>  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 <span data-ttu-id="e1d64-106">There are two approaches to writing this [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query in a lazy way.</span><span class="sxs-lookup"><span data-stu-id="e1d64-106">There are two approaches to writing this [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query in a lazy way.</span></span> <span data-ttu-id="e1d64-107">You can use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> operators, or you can use the <xref:System.Linq.Enumerable.Where%2A> overload that takes an index.</span><span class="sxs-lookup"><span data-stu-id="e1d64-107">You can use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> operators, or you can use the <xref:System.Linq.Enumerable.Where%2A> overload that takes an index.</span></span> <span data-ttu-id="e1d64-108">When you use the <xref:System.Linq.Enumerable.Where%2A> overload, you use a lambda expression that takes two arguments.</span><span class="sxs-lookup"><span data-stu-id="e1d64-108">When you use the <xref:System.Linq.Enumerable.Where%2A> overload, you use a lambda expression that takes two arguments.</span></span> <span data-ttu-id="e1d64-109">The following example shows both methods of selecting based on position.</span><span class="sxs-lookup"><span data-stu-id="e1d64-109">The following example shows both methods of selecting based on position.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1d64-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="e1d64-110">Example</span></span>  
 <span data-ttu-id="e1d64-111">This example finds the second through the fourth `Test` element.</span><span class="sxs-lookup"><span data-stu-id="e1d64-111">This example finds the second through the fourth `Test` element.</span></span> <span data-ttu-id="e1d64-112">The result is a collection of elements.</span><span class="sxs-lookup"><span data-stu-id="e1d64-112">The result is a collection of elements.</span></span>  
  
 <span data-ttu-id="e1d64-113">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e1d64-113">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="e1d64-114">This example produces the following output:</span><span class="sxs-lookup"><span data-stu-id="e1d64-114">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e1d64-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e1d64-115">See also</span></span>

- [<span data-ttu-id="e1d64-116">LINQ to XML for XPath Users (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1d64-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
