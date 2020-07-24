---
title: Postup dotazování LINQ to XML pomocí XPath (C#)
description: Můžete použít rozšiřující metody v jazyce C# k dotazování stromu XML pomocí XPath. Obecně nedoporučujeme používat XPath s LINQ to XML.
ms.date: 07/20/2015
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
ms.openlocfilehash: fff45a93380b5af85aa640fc690783cc95e6298b
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104346"
---
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a><span data-ttu-id="8638d-104">Postup dotazování LINQ to XML pomocí XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="8638d-104">How to query LINQ to XML using XPath (C#)</span></span>
<span data-ttu-id="8638d-105">Toto téma představuje rozšiřující metody, které umožňují dotazování stromu XML pomocí XPath.</span><span class="sxs-lookup"><span data-stu-id="8638d-105">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="8638d-106">Podrobné informace o použití těchto rozšiřujících metod naleznete v tématu <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8638d-106">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="8638d-107">Pokud nemáte konkrétní důvod pro dotazování pomocí XPath, jako je například rozsáhlé použití starší verze kódu, použití XPath s LINQ to XML se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="8638d-107">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="8638d-108">Dotazy XPath nebudou provádět ani [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="8638d-108">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8638d-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="8638d-109">Example</span></span>  
 <span data-ttu-id="8638d-110">Následující příklad vytvoří malý strom XML a používá <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> se k výběru sady prvků.</span><span class="sxs-lookup"><span data-stu-id="8638d-110">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
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
  
 <span data-ttu-id="8638d-111">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="8638d-111">This example produces the following output:</span></span>  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  