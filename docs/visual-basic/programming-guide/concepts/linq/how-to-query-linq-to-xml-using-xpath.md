---
title: 'Postupy: Dotazování na LINQ to XML pomocí jazyka XPath'
ms.date: 07/20/2015
ms.assetid: e1f69a20-1efa-452d-9089-c472fa84b3d5
ms.openlocfilehash: d95e5a82d146c357f52d03375119474b042d49f6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397918"
---
# <a name="how-to-query-linq-to-xml-using-xpath-visual-basic"></a><span data-ttu-id="bb069-102">Postupy: dotazování LINQ to XML pomocí XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb069-102">How to: Query LINQ to XML Using XPath (Visual Basic)</span></span>
<span data-ttu-id="bb069-103">Toto téma představuje rozšiřující metody, které umožňují dotazování stromu XML pomocí XPath.</span><span class="sxs-lookup"><span data-stu-id="bb069-103">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="bb069-104">Podrobné informace o použití těchto rozšiřujících metod naleznete v tématu <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="bb069-104">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="bb069-105">Pokud nemáte konkrétní důvod pro dotazování pomocí XPath, jako je například rozsáhlé použití starší verze kódu, použití XPath s LINQ to XML se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="bb069-105">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="bb069-106">Dotazy XPath nebudou provádět ani [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="bb069-106">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb069-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="bb069-107">Example</span></span>  
 <span data-ttu-id="bb069-108">Následující příklad vytvoří malý strom XML a používá <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> se k výběru sady prvků.</span><span class="sxs-lookup"><span data-stu-id="bb069-108">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>1</Child1>  
        <Child1>2</Child1>  
        <Child1>3</Child1>  
        <Child2>4</Child2>  
        <Child2>5</Child2>  
        <Child2>6</Child2>  
    </Root>  
  
Dim list As IEnumerable(Of XElement) = root.XPathSelectElements("./Child2")  
For Each el As XElement In list  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="bb069-109">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="bb069-109">This example produces the following output:</span></span>  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bb069-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb069-110">See also</span></span>

- [<span data-ttu-id="bb069-111">Pokročilé techniky dotazů (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb069-111">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](advanced-query-techniques-linq-to-xml.md)
