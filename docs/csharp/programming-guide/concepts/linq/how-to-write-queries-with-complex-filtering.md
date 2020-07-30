---
title: Zápis dotazů se složitým filtrováním (C#)
description: Naučte se psát LINQ to XML dotazy pomocí složitých filtrů. Podívejte se na příklady kódu a zobrazte další prostředky.
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: 5d2c1aafc210b35d4d6b1f1b2d74b11966d90c80
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303423"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a>Zápis dotazů se složitým filtrováním (C#)
Někdy budete chtít zapisovat LINQ to XML dotazy se složitými filtry. Například může být nutné najít všechny prvky, které mají podřízený element s určitým názvem a hodnotou. Toto téma poskytuje příklad zápisu dotazu se složitým filtrováním.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak najít všechny `PurchaseOrder` prvky, které mají podřízený `Address` element, který má `Type` atribut se rovná "dodávání" a podřízený `State` element se rovná "ny". Používá vnořený dotaz v `Where` klauzuli a `Any` operátor vrátí, `true` Pokud má kolekce nějaké prvky. Informace o použití syntaxe dotazů založených na metodách naleznete [v tématu Syntaxe dotazu a syntaxe metody v jazyce LINQ](./query-syntax-and-method-syntax-in-linq.md).  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: více nákupních objednávek (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
 Další informace o `Any` operátoru naleznete v tématu [operace kvantifikátoru (C#)](./quantifier-operations.md).  
  
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
 Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů. Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
 Tento příklad používá následující dokument XML: [ukázkový soubor XML: více nákupních objednávek v oboru názvů](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Operace projekce (C#)](./projection-operations.md)
- [Operace kvantifikátoru (C#)](./quantifier-operations.md)
