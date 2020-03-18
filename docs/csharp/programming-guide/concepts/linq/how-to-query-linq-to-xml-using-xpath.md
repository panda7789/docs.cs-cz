---
title: Jak dotaz LINQ na XML pomocí XPath (C#)
ms.date: 07/20/2015
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
ms.openlocfilehash: 61878febd9b4880872b7bc58e4de04b37cff96f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344808"
---
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a><span data-ttu-id="4629a-102">Jak dotaz LINQ na XML pomocí XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="4629a-102">How to query LINQ to XML using XPath (C#)</span></span>
<span data-ttu-id="4629a-103">Toto téma představuje metody rozšíření, které umožňují dotaz na strom XML pomocí XPath.</span><span class="sxs-lookup"><span data-stu-id="4629a-103">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="4629a-104">Podrobné informace o použití těchto <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>metod rozšíření naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="4629a-104">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="4629a-105">Pokud nemáte velmi specifický důvod pro dotazování pomocí XPath, jako je například rozsáhlé použití staršího kódu, nedoporučujeme používat XPath s LINQ na XML.</span><span class="sxs-lookup"><span data-stu-id="4629a-105">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="4629a-106">Dotazy XPath nebudou fungovat tak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dobře jako dotazy.</span><span class="sxs-lookup"><span data-stu-id="4629a-106">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4629a-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="4629a-107">Example</span></span>  
 <span data-ttu-id="4629a-108">Následující příklad vytvoří malý strom <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> XML a použije se k výběru sady prvků.</span><span class="sxs-lookup"><span data-stu-id="4629a-108">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
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
  
 <span data-ttu-id="4629a-109">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="4629a-109">This example produces the following output:</span></span>  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  