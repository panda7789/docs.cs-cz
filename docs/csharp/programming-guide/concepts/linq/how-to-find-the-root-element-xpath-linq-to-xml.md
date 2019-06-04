---
title: 'Postupy: Vyhledání kořenového elementu (XPath – LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: 59696e6f3487bbb09135ba413a173c32dffa0c9b
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485422"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a><span data-ttu-id="60173-102">Postupy: Vyhledání kořenového elementu (XPath – LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="60173-102">How to: Find the Root Element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="60173-103">Toto téma ukazuje, jak získat kořenový element, jejichž výraz XPath a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="60173-103">This topic shows how to get the root element with XPath and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="60173-104">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="60173-104">The XPath expression is:</span></span>  
  
 `/PurchaseOrders`  
  
## <a name="example"></a><span data-ttu-id="60173-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="60173-105">Example</span></span>  
 <span data-ttu-id="60173-106">Tento příklad vyhledá kořenový element.</span><span class="sxs-lookup"><span data-stu-id="60173-106">This example finds the root element.</span></span>  
  
 <span data-ttu-id="60173-107">Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Více nákupních objednávek (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="60173-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="60173-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="60173-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
PurchaseOrders  
```  
