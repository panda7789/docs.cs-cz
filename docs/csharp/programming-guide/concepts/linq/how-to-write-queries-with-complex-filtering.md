---
title: 'Postupy: vytváření dotazů s komplexním filtrováním (C#)'
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: 2f8eef2f75e45212b3493aa1b6f813c52beb7665
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508830"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a>Postupy: vytváření dotazů s komplexním filtrováním (C#)
Někdy budete chtít napsat LINQ dotazy XML se složitějšími filtry. Například budete muset najít všechny elementy, které mají podřízený element s určitým názvem a hodnotou. V tomto tématu poskytuje příklad zápisu dotazů s komplexním filtrováním.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak najít všechny `PurchaseOrder` prvky, které mají podřízený `Address` element, který má `Type` atribut rovná "Přesouvání" a podřízená `State` prvek s hodnotou "USA". Používá vnořené dotaz v `Where` klauzule a `Any` operátor vrátí `true` Pokud kolekce obsahuje všechny prvky v ní. Informace o použití syntaxe dotazů založených na volání metody, naleznete v tématu [syntaxi dotazů a syntaxe využívající metody v jazyce LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
 Tento příklad používá následujícího dokumentu XML: [ukázkový soubor XML: více nákupních objednávek (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
 Další informace o `Any` operátoru, naleznete v tématu [operace kvantifikátoru (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md).  
  
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
  
 Tento kód vytvoří následující výstup:  
  
```  
99505  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje stejný dotaz pro soubor XML, který je v oboru názvů. Další informace najdete v tématu [práce s názvovými prostory XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 Tento příklad používá následujícího dokumentu XML: [ukázkový soubor XML: více nákupních objednávek v Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
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
  
 Tento kód vytvoří následující výstup:  
  
```  
99505  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.Linq.XElement.Attribute%2A>  
- <xref:System.Xml.Linq.XContainer.Elements%2A>  
- [Základní dotazy (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)  
- [Operace projekce (C#)](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)  
- [Operace kvantifikátoru (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)
