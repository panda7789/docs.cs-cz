---
title: 'Postupy: Najít podřízený element (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 4fa6182d-6196-4ed1-9c9e-82949ff89c71
ms.openlocfilehash: 315cf782aa886bba484eb1fb06a4c4dbcf3cb4df
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593718"
---
# <a name="how-to-find-a-child-element-xpath-linq-to-xml-c"></a><span data-ttu-id="c5501-102">Postupy: Najít podřízený element (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c5501-102">How to: Find a Child Element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="c5501-103">Toto téma porovnává podřízenou osu elementu XPath s [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> metodou.</span><span class="sxs-lookup"><span data-stu-id="c5501-103">This topic compares the XPath child element axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  
  
 <span data-ttu-id="c5501-104">Výraz XPath je `DeliveryNotes`.</span><span class="sxs-lookup"><span data-stu-id="c5501-104">The XPath expression is `DeliveryNotes`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5501-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="c5501-105">Example</span></span>  
 <span data-ttu-id="c5501-106">Tento příklad najde podřízený element `DeliveryNotes`.</span><span class="sxs-lookup"><span data-stu-id="c5501-106">This example finds the child element `DeliveryNotes`.</span></span>  
  
 <span data-ttu-id="c5501-107">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Více nákupních objednávek (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c5501-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="c5501-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c5501-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  