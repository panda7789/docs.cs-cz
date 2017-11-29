---
title: "Postupy: hledání prvku podřízené (XPath-technologie LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 4fa6182d-6196-4ed1-9c9e-82949ff89c71
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f66866ea938bf5f10ed4369b3728621ee2f87fec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-a-child-element-xpath-linq-to-xml-c"></a><span data-ttu-id="88a2d-102">Postupy: hledání prvku podřízené (XPath-technologie LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="88a2d-102">How to: Find a Child Element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="88a2d-103">Toto téma porovnává ose XPath podřízený element na [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="88a2d-103">This topic compares the XPath child element axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  
  
 <span data-ttu-id="88a2d-104">Výraz XPath je `DeliveryNotes`.</span><span class="sxs-lookup"><span data-stu-id="88a2d-104">The XPath expression is `DeliveryNotes`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88a2d-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="88a2d-105">Example</span></span>  
 <span data-ttu-id="88a2d-106">Tento příklad vyhledá podřízený element `DeliveryNotes`.</span><span class="sxs-lookup"><span data-stu-id="88a2d-106">This example finds the child element `DeliveryNotes`.</span></span>  
  
 <span data-ttu-id="88a2d-107">Tento příklad používá následující dokumentu XML: [ukázkový soubor XML: více nákupních objednávek (technologie LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="88a2d-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="88a2d-108">Tento příklad vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="88a2d-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="88a2d-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="88a2d-109">See Also</span></span>  
 [<span data-ttu-id="88a2d-110">Technologie LINQ to XML pro uživatele XPath (C#)</span><span class="sxs-lookup"><span data-stu-id="88a2d-110">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
