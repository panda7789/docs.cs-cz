---
title: 'Postupy: Najít kořenový element (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: 1fea4cc630dd708a86a0f0595ac727f8b8fa40af
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593378"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a><span data-ttu-id="2a875-102">Postupy: Najít kořenový element (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2a875-102">How to: Find the Root Element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="2a875-103">Toto téma ukazuje, jak získat kořenový prvek pomocí XPath a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2a875-103">This topic shows how to get the root element with XPath and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="2a875-104">Výraz XPath je:</span><span class="sxs-lookup"><span data-stu-id="2a875-104">The XPath expression is:</span></span>  
  
 `/PurchaseOrders`  
  
## <a name="example"></a><span data-ttu-id="2a875-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="2a875-105">Example</span></span>  
 <span data-ttu-id="2a875-106">Tento příklad najde kořenový element.</span><span class="sxs-lookup"><span data-stu-id="2a875-106">This example finds the root element.</span></span>  
  
 <span data-ttu-id="2a875-107">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Více nákupních objednávek (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2a875-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="2a875-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="2a875-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
PurchaseOrders  
```  
