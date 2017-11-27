---
title: "Postupy: vyhledání Následnickým elementům (XPath-technologie LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: b318da39-bb8b-4c56-a019-e13b12b01831
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d3551054b345d9ec1d18b33f697cf5c139bfab6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-descendant-elements-xpath-linq-to-xml-c"></a><span data-ttu-id="e7b33-102">Postupy: vyhledání Následnickým elementům (XPath-technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e7b33-102">How to: Find Descendant Elements (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="e7b33-103">Toto téma ukazuje, jak získat následnickým elementům s konkrétním názvem.</span><span class="sxs-lookup"><span data-stu-id="e7b33-103">This topic shows how to get the descendant elements with a particular name.</span></span>  
  
 <span data-ttu-id="e7b33-104">Výraz XPath je `//Name`.</span><span class="sxs-lookup"><span data-stu-id="e7b33-104">The XPath expression is `//Name`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7b33-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="e7b33-105">Example</span></span>  
 <span data-ttu-id="e7b33-106">Tento příklad vyhledá všech potomků s názvem `Name`.</span><span class="sxs-lookup"><span data-stu-id="e7b33-106">This example finds all descendants named `Name`.</span></span>  
  
 <span data-ttu-id="e7b33-107">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: více nákupních objednávek (technologie LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e7b33-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 = po.Root.Descendants("Name");  
  
// XPath expression  
IEnumerable<XElement> list2 = po.XPathSelectElements("//Name");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="e7b33-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="e7b33-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7b33-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="e7b33-109">See Also</span></span>  
 [<span data-ttu-id="e7b33-110">Technologie LINQ to XML pro uživatele XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="e7b33-110">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
