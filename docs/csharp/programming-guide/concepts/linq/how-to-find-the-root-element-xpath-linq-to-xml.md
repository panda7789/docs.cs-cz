---
title: 'Postupy: Vyhledání kořenového elementu (XPath – LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: a0197a34f2e9d1b42a71d3c8cb1a4281ba495c4f
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2018
ms.locfileid: "46710985"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a><span data-ttu-id="2e71a-102">Postupy: Vyhledání kořenového elementu (XPath – LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2e71a-102">How to: Find the Root Element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="2e71a-103">Toto téma ukazuje, jak získat kořenový element, jejichž výraz XPath a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e71a-103">This topic shows how to get the root element with XPath and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="2e71a-104">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="2e71a-104">The XPath expression is:</span></span>  
  
 `/PurchaseOrders`  
  
## <a name="example"></a><span data-ttu-id="2e71a-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="2e71a-105">Example</span></span>  
 <span data-ttu-id="2e71a-106">Tento příklad vyhledá kořenový element.</span><span class="sxs-lookup"><span data-stu-id="2e71a-106">This example finds the root element.</span></span>  
  
 <span data-ttu-id="2e71a-107">Tento příklad používá následujícího dokumentu XML: [ukázkový soubor XML: více nákupních objednávek (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2e71a-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
// LINQ to XML query  
XElement el1 = po.Root;  
  
// XPath expression  
XElement el2 = po.XPathSelectElement("/PurchaseOrders");  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1.Name);  
```  
  
 <span data-ttu-id="2e71a-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="2e71a-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
PurchaseOrders  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e71a-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e71a-109">See Also</span></span>

- [<span data-ttu-id="2e71a-110">LINQ to XML pro uživatele jazyka XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="2e71a-110">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
