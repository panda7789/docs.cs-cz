---
title: 'Postupy: Dotazování na LINQ to XML pomocí jazyka XPath (C#)'
ms.date: 07/20/2015
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
ms.openlocfilehash: a3e9cb29b9ba027cfc70eeb0cd163b24834dff83
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564104"
---
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a><span data-ttu-id="e5032-102">Postupy: Dotazování na LINQ to XML pomocí jazyka XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="e5032-102">How to: Query LINQ to XML Using XPath (C#)</span></span>
<span data-ttu-id="e5032-103">Toto téma představuje rozšiřující metody, které vám umožní dotazovat stromu XML pomocí XPath.</span><span class="sxs-lookup"><span data-stu-id="e5032-103">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="e5032-104">Podrobné informace o použití těchto metod rozšíření najdete v tématu <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e5032-104">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="e5032-105">Pokud nemáte velmi konkrétní důvod pro dotazování pomocí XPath, jako je například příliš často používá starší verzi kódu s LINQ to XML pomocí jazyka XPath se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="e5032-105">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="e5032-106">Nebude provádět dotazy XPath a jednak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="e5032-106">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5032-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="e5032-107">Example</span></span>  
 <span data-ttu-id="e5032-108">Následující příklad vytvoří malý stromu XML a používá <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> vybrat sadu elementů.</span><span class="sxs-lookup"><span data-stu-id="e5032-108">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", 1),  
    new XElement("Child1", 2),  
    new XElement("Child1", 3),  
    new XElement("Child2", 4),  
    new XElement("Child2", 5),  
    new XElement("Child2", 6)  
);  
IEnumerable<XElement> list = root.XPathSelectElements("./Child2");  
foreach (XElement el in list)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="e5032-109">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="e5032-109">This example produces the following output:</span></span>  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e5032-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5032-110">See also</span></span>

- [<span data-ttu-id="e5032-111">Pokročilé techniky dotazování (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e5032-111">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
