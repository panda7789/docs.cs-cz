---
title: Jak najít podřízený prvek (XPath-LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 4fa6182d-6196-4ed1-9c9e-82949ff89c71
ms.openlocfilehash: 37ce6c9d91d4edf2576ccddabd1d7f14a96b0a33
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141233"
---
# <a name="how-to-find-a-child-element-xpath-linq-to-xml-c"></a><span data-ttu-id="3bf2c-102">Jak najít podřízený prvek (XPath-LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="3bf2c-102">How to find a child element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="3bf2c-103">Toto téma porovnává osu podřízeného prvku XPath s [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> metodou.</span><span class="sxs-lookup"><span data-stu-id="3bf2c-103">This topic compares the XPath child element axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  
  
 <span data-ttu-id="3bf2c-104">Výraz XPath `DeliveryNotes`je .</span><span class="sxs-lookup"><span data-stu-id="3bf2c-104">The XPath expression is `DeliveryNotes`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3bf2c-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="3bf2c-105">Example</span></span>  
 <span data-ttu-id="3bf2c-106">Tento příklad vyhledá `DeliveryNotes`podřízený prvek .</span><span class="sxs-lookup"><span data-stu-id="3bf2c-106">This example finds the child element `DeliveryNotes`.</span></span>  
  
 <span data-ttu-id="3bf2c-107">Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Více nákupních objednávek (LINQ to XML).](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="3bf2c-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument cpo = XDocument.Load("PurchaseOrders.xml");  
XElement po = cpo.Root.Element("PurchaseOrder");  
  
// LINQ to XML query  
XElement el1 = po.Element("DeliveryNotes");  
  
// XPath expression  
XElement el2 = po.XPathSelectElement("DeliveryNotes");  
// same as "child::DeliveryNotes"  
// same as "./DeliveryNotes"  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1);  
```  
  
 <span data-ttu-id="3bf2c-108">Tento příklad vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3bf2c-108">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  