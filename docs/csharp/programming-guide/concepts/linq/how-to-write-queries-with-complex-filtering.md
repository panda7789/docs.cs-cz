---
title: 'Postupy: Zápis dotazů s komplexním filtrováním (C#)'
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: 7759a02c1b9ef0ae0c1af4bfb2600543b21cdf0f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253193"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a>Postupy: Zápis dotazů s komplexním filtrováním (C#)
Někdy budete chtít zapisovat LINQ to XML dotazy se složitými filtry. Například může být nutné najít všechny prvky, které mají podřízený element s určitým názvem a hodnotou. Toto téma poskytuje příklad zápisu dotazu se složitým filtrováním.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak najít všechny `PurchaseOrder` prvky, které mají podřízený `Address` element, který má `Type` atribut se rovná "dodávání" a `State` podřízený element se rovná "ny". Používá vnořený dotaz v `Where` klauzuli `Any` a operátor vrátí `true` , pokud má kolekce nějaké prvky. Informace o použití syntaxe dotazů založených na metodách naleznete [v tématu Syntaxe dotazu a syntaxe metody v jazyce LINQ](./query-syntax-and-method-syntax-in-linq.md).  
  
 V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Více nákupních objednávek (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
 Další informace o `Any` operátoru najdete v tématu [operace kvantifikátoru (C#)](./quantifier-operations.md).  
  
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
  
 Tento kód generuje následující výstup:  
  
```output  
99505  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejný dotaz pro XML, který je v oboru názvů. Další informace najdete v tématu [obory názvů Overview (LINQ to XMLC#) ()](namespaces-overview-linq-to-xml.md).  
  
 V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Několik nákupních objednávek v oboru názvů](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
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
  
 Tento kód generuje následující výstup:  
  
```output  
99505  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Operace projekce (C#)](./projection-operations.md)
- [Operace kvantifikátoru (C#)](./quantifier-operations.md)
