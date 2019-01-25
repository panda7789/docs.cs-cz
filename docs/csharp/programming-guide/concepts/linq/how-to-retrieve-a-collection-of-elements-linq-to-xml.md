---
title: 'Postupy: Načtení kolekce elementů (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: 8d01c0499f031ae22fd6383dd77b36e444704c46
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674999"
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

- [Osy LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
