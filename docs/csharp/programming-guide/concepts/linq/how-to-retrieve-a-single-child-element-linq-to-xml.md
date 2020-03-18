---
title: Jak načíst jeden podřízený prvek (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: 0e10cf230a73e6419f2d9c663766f9a24a0930af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347478"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a>Jak načíst jeden podřízený prvek (LINQ do XML) (C#)
Toto téma vysvětluje, jak načíst jeden podřízený prvek, zadaný název podřízeného prvku. Pokud znáte název podřízeného prvku a že existuje pouze jeden prvek, který má tento název, může být vhodné načíst pouze jeden prvek, namísto kolekce.  
  
 Metoda <xref:System.Xml.Linq.XContainer.Element%2A> vrátí první <xref:System.Xml.Linq.XElement> podřízenou <xref:System.Xml.Linq.XName>položku se zadaným .  
  
 Pokud chcete načíst jeden podřízený prvek v jazyce Visual Basic, běžným přístupem je použití vlastnosti XML a potom načíst první prvek pomocí zápisu indexeru pole.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití <xref:System.Xml.Linq.XContainer.Element%2A> metody. Tento příklad přebírá strom `po` XML s názvem `Comment`a vyhledá první pojmenovanou prvek .  
  
 Příklad jazyka ukazuje pomocí zápisu indexeru pole k načtení jednoho prvku.  
  
 Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Typický nákupní objednávka (LINQ to XML).](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
XElement e = po.Element("DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejný kód pro JAZYK XML, který je v oboru názvů. Další informace naleznete [v tématu Přehled oborů názvů (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
 Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Typická nákupní objednávka v oboru názvů](./sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
```csharp  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement e = po.Element(aw + "DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 Tento příklad vytváří následující výstup:  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a>Viz také

- [LINQ na osy XML (C#)](./linq-to-xml-axes-overview.md)
