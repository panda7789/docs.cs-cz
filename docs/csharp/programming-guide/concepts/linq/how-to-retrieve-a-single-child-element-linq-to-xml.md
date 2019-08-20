---
title: 'Postupy: Načtení jednoho podřízeného elementu (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: 5f2f675f5ce4914124f62981a2591441260b6976
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592626"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a>Postupy: Načtení jednoho podřízeného elementu (LINQ to XML) (C#)
Toto téma vysvětluje, jak načíst jeden podřízený prvek s názvem podřízeného prvku. Pokud znáte název podřízeného prvku a že existuje pouze jeden prvek, který má tento název, může být vhodné načíst pouze jeden prvek namísto kolekce.  
  
 Metoda vrací první podřízenou položku <xref:System.Xml.Linq.XElement> se zadaným parametrem <xref:System.Xml.Linq.XName>. <xref:System.Xml.Linq.XContainer.Element%2A>  
  
 Pokud chcete načíst jeden podřízený prvek v Visual Basic, společný přístup je použít vlastnost XML a poté načíst první prvek pomocí notace Array indexer.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití <xref:System.Xml.Linq.XContainer.Element%2A> metody. Tento příklad převezme strom XML s `po` názvem a vyhledá první prvek `Comment`s názvem.  
  
 Visual Basic příklad ukazuje použití notace indexeru pole k načtení jednoho prvku.  
  
 V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
XElement e = po.Element("DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejný kód pro XML, který je v oboru názvů. Další informace najdete v tématu [obory názvů Overview (LINQ to XMLC#) ()](namespaces-overview-linq-to-xml.md).  
  
 V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Typická nákupní objednávka v oboru názvů](./sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
```csharp  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement e = po.Element(aw + "DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 Tento příklad vytvoří následující výstup:  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a>Viz také:

- [LINQ to XML osy (C#)](./linq-to-xml-axes-overview.md)
