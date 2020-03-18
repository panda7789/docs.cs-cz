---
title: Jak najít kořenový prvek (XPath-LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: 1c5526f436b5b9d88ca359ef7e0fc04c5c3cf43c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345952"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a><span data-ttu-id="d5a3e-102">Jak najít kořenový prvek (XPath-LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d5a3e-102">How to find the root element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="d5a3e-103">Toto téma ukazuje, jak získat kořenový prvek s XPath a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d5a3e-103">This topic shows how to get the root element with XPath and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="d5a3e-104">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="d5a3e-104">The XPath expression is:</span></span>  
  
 `/PurchaseOrders`  
  
## <a name="example"></a><span data-ttu-id="d5a3e-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="d5a3e-105">Example</span></span>  
 <span data-ttu-id="d5a3e-106">Tento příklad najde kořenový prvek.</span><span class="sxs-lookup"><span data-stu-id="d5a3e-106">This example finds the root element.</span></span>  
  
 <span data-ttu-id="d5a3e-107">Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Více nákupních objednávek (LINQ to XML).](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="d5a3e-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="d5a3e-108">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="d5a3e-108">This example produces the following output:</span></span>  
  
```output  
Results are identical  
PurchaseOrders  
```  
