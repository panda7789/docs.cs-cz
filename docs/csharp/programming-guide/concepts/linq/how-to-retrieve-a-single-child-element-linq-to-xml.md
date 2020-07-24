---
title: Jak načíst jeden podřízený element (LINQ to XML) (C#)
description: Naučte se, jak pomocí LINQ to XML načíst jeden podřízený prvek podle názvu. V tomto příkladu jazyka C# vrací metoda elementu první zadaný podřízený element.
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: c3a044f30cf2e411bdff52586c7a370b626f41bc
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103280"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a>Jak načíst jeden podřízený element (LINQ to XML) (C#)
Toto téma vysvětluje, jak načíst jeden podřízený prvek s názvem podřízeného prvku. Pokud znáte název podřízeného prvku a že existuje pouze jeden prvek, který má tento název, může být vhodné načíst pouze jeden prvek namísto kolekce.  
  
 <xref:System.Xml.Linq.XContainer.Element%2A>Metoda vrací první podřízenou položku <xref:System.Xml.Linq.XElement> se zadaným parametrem <xref:System.Xml.Linq.XName> .  
  
 Pokud chcete načíst jeden podřízený prvek v Visual Basic, společný přístup je použít vlastnost XML a poté načíst první prvek pomocí notace Array indexer.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití <xref:System.Xml.Linq.XContainer.Element%2A> metody. Tento příklad převezme strom XML s názvem `po` a vyhledá první prvek s názvem `Comment` .  
  
 Visual Basic příklad ukazuje použití notace indexeru pole k načtení jednoho prvku.  
  
 Tento příklad používá následující dokument XML: [vzorový soubor XML: typická nákupní objednávka (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
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
 Následující příklad ukazuje stejný kód pro XML, který je v oboru názvů. Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: typická nákupní objednávka v oboru názvů](./sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
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
  
## <a name="see-also"></a>Viz také

- [LINQ to XML osy (C#)](./linq-to-xml-axes-overview.md)
