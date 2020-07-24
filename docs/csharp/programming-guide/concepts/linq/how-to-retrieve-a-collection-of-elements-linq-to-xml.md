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
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a>Jak načíst kolekci elementů (LINQ to XML) (C#)
Toto téma ukazuje <xref:System.Xml.Linq.XContainer.Elements%2A> metodu. Tato metoda načte kolekci podřízených elementů elementu.  
  
## <a name="example"></a>Příklad  
 Tento příklad prochází podřízené prvky `purchaseOrder` elementu.  
  
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
  
## <a name="see-also"></a>Viz také

- [LINQ to XML osy (C#)](./linq-to-xml-axes-overview.md)
