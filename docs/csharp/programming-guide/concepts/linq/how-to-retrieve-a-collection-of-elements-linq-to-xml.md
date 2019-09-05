---
title: 'Postupy: Načíst kolekci elementů (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: fef12745bd608622f071f72049f242405d17ed7d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253423"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a><span data-ttu-id="94e94-102">Postupy: Načíst kolekci elementů (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="94e94-102">How to: Retrieve a Collection of Elements (LINQ to XML) (C#)</span></span>
<span data-ttu-id="94e94-103">Toto téma ukazuje <xref:System.Xml.Linq.XContainer.Elements%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="94e94-103">This topic demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span> <span data-ttu-id="94e94-104">Tato metoda načte kolekci podřízených elementů elementu.</span><span class="sxs-lookup"><span data-stu-id="94e94-104">This method retrieves a collection of the child elements of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94e94-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="94e94-105">Example</span></span>  
 <span data-ttu-id="94e94-106">Tento příklad prochází podřízené prvky `purchaseOrder` elementu.</span><span class="sxs-lookup"><span data-stu-id="94e94-106">This example iterates through the child elements of the `purchaseOrder` element.</span></span>  
  
 <span data-ttu-id="94e94-107">V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="94e94-107">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> childElements =  
    from el in po.Elements()  
    select el;  
foreach (XElement el in childElements)  
    Console.WriteLine("Name: " + el.Name);  
```  
  
 <span data-ttu-id="94e94-108">Tento příklad vytvoří následující výstup.</span><span class="sxs-lookup"><span data-stu-id="94e94-108">This example produces the following output.</span></span>  
  
```output  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a><span data-ttu-id="94e94-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94e94-109">See also</span></span>

- [<span data-ttu-id="94e94-110">LINQ to XML osy (C#)</span><span class="sxs-lookup"><span data-stu-id="94e94-110">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
