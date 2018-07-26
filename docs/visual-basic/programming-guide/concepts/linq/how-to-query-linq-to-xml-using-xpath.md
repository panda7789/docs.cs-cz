---
title: 'Postupy: dotazování na LINQ to XML pomocí jazyka XPath (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: e1f69a20-1efa-452d-9089-c472fa84b3d5
ms.openlocfilehash: d8f23bd8417c3f59377e5e677b08e403ecc1122d
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244345"
---
# <a name="how-to-query-linq-to-xml-using-xpath-visual-basic"></a><span data-ttu-id="3a944-102">Postupy: dotazování na LINQ to XML pomocí jazyka XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a944-102">How to: Query LINQ to XML Using XPath (Visual Basic)</span></span>
<span data-ttu-id="3a944-103">Toto téma představuje rozšiřující metody, které vám umožní dotazovat stromu XML pomocí XPath.</span><span class="sxs-lookup"><span data-stu-id="3a944-103">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="3a944-104">Podrobné informace o použití těchto metod rozšíření najdete v tématu <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3a944-104">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="3a944-105">Pokud nemáte velmi konkrétní důvod pro dotazování pomocí XPath, jako je například příliš často používá starší verzi kódu s LINQ to XML pomocí jazyka XPath se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="3a944-105">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="3a944-106">Nebude provádět dotazy XPath a jednak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="3a944-106">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a944-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="3a944-107">Example</span></span>  
 <span data-ttu-id="3a944-108">Následující příklad vytvoří malý stromu XML a používá <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> vybrat sadu elementů.</span><span class="sxs-lookup"><span data-stu-id="3a944-108">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
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
  
 <span data-ttu-id="3a944-109">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3a944-109">This example produces the following output:</span></span>  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3a944-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a944-110">See Also</span></span>  
 [<span data-ttu-id="3a944-111">Pokročilé techniky dotazování (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a944-111">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
