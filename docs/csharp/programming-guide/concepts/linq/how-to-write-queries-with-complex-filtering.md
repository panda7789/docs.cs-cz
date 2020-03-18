---
title: Jak psát dotazy se složitým filtrováním (C#)
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: bc85d7f1e5c5305407ad22f3ada908523313d964
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168515"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a>Jak psát dotazy se složitým filtrováním (C#)
Někdy chcete zapsat LINQ do dotazů XML se složitými filtry. Například budete muset najít všechny prvky, které mají podřízený prvek s určitým názvem a hodnotou. Toto téma uvádí příklad psaní dotazu se složitým filtrováním.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, `PurchaseOrder` jak najít všechny `Address` prvky, `Type` které mají podřízený prvek, který má atribut rovný "Doprava" a podřízený `State` prvek rovnající se "NY". Používá vnořený dotaz `Where` v klauzuli a `Any` operátor vrátí, `true` pokud kolekce má nějaké prvky v něm. Informace o použití syntaxe dotazu založeného na metodách naleznete [v tématu Syntaxe dotazu a syntaxe metody v LINQ](./query-syntax-and-method-syntax-in-linq.md).  
  
 Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Více nákupních objednávek (LINQ to XML).](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)  
  
 Další informace o `Any` operátoru naleznete v tématu [Kvantifikátor operace (C#)](./quantifier-operations.md).  
  
```csharp  
XElement root = XElement.Load("PurchaseOrders.xml");  
IEnumerable<XElement> purchaseOrders =  
    from el in root.Elements("PurchaseOrder")  
    where
        (from add in el.Elements("Address")  
        where  
            (string)add.Attribute("Type") == "Shipping" &&  
            (string)add.Element("State") == "NY"  
        select add)  
        .Any()  
    select el;  
foreach (XElement el in purchaseOrders)  
    Console.WriteLine((string)el.Attribute("PurchaseOrderNumber"));  
```  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```output  
99505  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejný dotaz pro jazyk XML, který je v oboru názvů. Další informace naleznete [v tématu Přehled oborů názvů (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
 Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Více nákupních objednávek v oboru názvů](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
```csharp  
XElement root = XElement.Load("PurchaseOrdersInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> purchaseOrders =  
    from el in root.Elements(aw + "PurchaseOrder")  
    where  
        (from add in el.Elements(aw + "Address")  
         where  
             (string)add.Attribute(aw + "Type") == "Shipping" &&  
             (string)add.Element(aw + "State") == "NY"  
         select add)  
        .Any()  
    select el;  
foreach (XElement el in purchaseOrders)  
    Console.WriteLine((string)el.Attribute(aw + "PurchaseOrderNumber"));  
```  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```output  
99505  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Projekční operace (C#)](./projection-operations.md)
- [Operace kvantifikátoru (C#)](./quantifier-operations.md)
