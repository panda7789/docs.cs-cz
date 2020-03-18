---
title: Jak načíst kolekci prvků (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: 89799b17115fb56a93bda5fbc144b21b334a6974
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345010"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a>Jak načíst kolekci prvků (LINQ do XML) (C#)
Toto téma <xref:System.Xml.Linq.XContainer.Elements%2A> ukazuje metodu. Tato metoda načte kolekci podřízených prvků prvku.  
  
## <a name="example"></a>Příklad  
 Tento příklad iterates prostřednictvím `purchaseOrder` podřízených prvků prvku.  
  
 Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Typický nákupní objednávka (LINQ to XML).](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> childElements =  
    from el in po.Elements()  
    select el;  
foreach (XElement el in childElements)  
    Console.WriteLine("Name: " + el.Name);  
```  
  
 Tento příklad vytváří následující výstup.  
  
```output  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a>Viz také

- [LINQ na osy XML (C#)](./linq-to-xml-axes-overview.md)
