---
title: 'Postupy: Načtení kolekce elementů (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: 42d1eaeb5e0ce43d27cd4675f634ab3dfca80a53
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485091"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a>Postupy: Načtení kolekce elementů (LINQ to XML) (C#)
Toto téma ukazuje, <xref:System.Xml.Linq.XContainer.Elements%2A> metody. Tato metoda načte kolekci podřízených elementů elementu.  
  
## <a name="example"></a>Příklad  
 Tento příklad provede iteraci podřízených elementů `purchaseOrder` elementu.  
  
 Tento příklad používá následujícího dokumentu XML: [Ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> childElements =  
    from el in po.Elements()  
    select el;  
foreach (XElement el in childElements)  
    Console.WriteLine("Name: " + el.Name);  
```  
  
 Tento příklad vytvoří následující výstup.  
  
```  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a>Viz také:

- [Osy LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)
