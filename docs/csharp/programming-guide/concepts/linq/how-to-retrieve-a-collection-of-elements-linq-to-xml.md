---
title: Jak načíst kolekci elementů (LINQ to XML) (C#)
description: Metoda elementů v jazyce C# načítá kolekci podřízených prvků prvku. Tento LINQ to XML příklad opakuje podřízené prvky elementu.
ms.date: 07/20/2015
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: 4f9b6ae4713af9ce1a4eeb5257f57cd9724f68b2
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103361"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a><span data-ttu-id="76350-104">Jak načíst kolekci elementů (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="76350-104">How to retrieve a collection of elements (LINQ to XML) (C#)</span></span>
<span data-ttu-id="76350-105">Toto téma ukazuje <xref:System.Xml.Linq.XContainer.Elements%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="76350-105">This topic demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span> <span data-ttu-id="76350-106">Tato metoda načte kolekci podřízených elementů elementu.</span><span class="sxs-lookup"><span data-stu-id="76350-106">This method retrieves a collection of the child elements of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76350-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="76350-107">Example</span></span>  
 <span data-ttu-id="76350-108">Tento příklad prochází podřízené prvky `purchaseOrder` elementu.</span><span class="sxs-lookup"><span data-stu-id="76350-108">This example iterates through the child elements of the `purchaseOrder` element.</span></span>  
  
 <span data-ttu-id="76350-109">Tento příklad používá následující dokument XML: [vzorový soubor XML: typická nákupní objednávka (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="76350-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> childElements =  
    from el in po.Elements()  
    select el;  
foreach (XElement el in childElements)  
    Console.WriteLine("Name: " + el.Name);  
```  
  
 <span data-ttu-id="76350-110">Tento příklad vytvoří následující výstup.</span><span class="sxs-lookup"><span data-stu-id="76350-110">This example produces the following output.</span></span>  
  
```output  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a><span data-ttu-id="76350-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="76350-111">See also</span></span>

- [<span data-ttu-id="76350-112">LINQ to XML osy (C#)</span><span class="sxs-lookup"><span data-stu-id="76350-112">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
