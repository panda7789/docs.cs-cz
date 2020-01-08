---
title: Jak načíst kolekci elementů (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: 89799b17115fb56a93bda5fbc144b21b334a6974
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345010"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a>Jak načíst kolekci elementů (LINQ to XML) (C#)
Toto téma ukazuje metodu <xref:System.Xml.Linq.XContainer.Elements%2A>. Tato metoda načte kolekci podřízených elementů elementu.  
  
## <a name="example"></a>Příklad  
 Tento příklad projde podřízenými prvky elementu `purchaseOrder`.  
  
 Tento příklad používá následující dokument XML: [vzorový soubor XML: typická nákupní objednávka (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> childElements =  
    from el in po.Elements()  
    select el;  
foreach (XElement el in childElements)  
    Console.WriteLine("Name: " + el.Name);  
```  
  
 Tento příklad vytvoří následující výstup.  
  
```output  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a>Viz také:

- [LINQ to XML osy (C#)](./linq-to-xml-axes-overview.md)
