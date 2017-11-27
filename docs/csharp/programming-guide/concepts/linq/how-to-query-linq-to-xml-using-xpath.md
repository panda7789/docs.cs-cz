---
title: "Postupy: dotazování technologie LINQ to XML s použitím XPath (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1cb47b5b4b85536feeb5006fe6dd31580ca651b3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a><span data-ttu-id="42082-102">Postupy: dotazování technologie LINQ to XML s použitím XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="42082-102">How to: Query LINQ to XML Using XPath (C#)</span></span>
<span data-ttu-id="42082-103">Toto téma představuje rozšiřující metody, které vám umožní zadat dotaz strom XML s použitím XPath.</span><span class="sxs-lookup"><span data-stu-id="42082-103">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="42082-104">Podrobné informace o použití těchto metod rozšíření najdete v tématu <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="42082-104">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="42082-105">Pokud nemáte velmi konkrétní důvod, proč pro dotazování pomocí jazyka XPath, jako je například rozsáhlé používání starší verze kódu, pomocí technologie LINQ to XML XPath se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="42082-105">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="42082-106">Nebude provádět dotazy XPath a také [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="42082-106">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42082-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="42082-107">Example</span></span>  
 <span data-ttu-id="42082-108">Následující příklad vytvoří malé stromu XML a používá <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> pro výběr sady elementů.</span><span class="sxs-lookup"><span data-stu-id="42082-108">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
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
  
 <span data-ttu-id="42082-109">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="42082-109">This example produces the following output:</span></span>  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a><span data-ttu-id="42082-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="42082-110">See Also</span></span>  
 [<span data-ttu-id="42082-111">Pokročilé techniky dotazu (technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="42082-111">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
