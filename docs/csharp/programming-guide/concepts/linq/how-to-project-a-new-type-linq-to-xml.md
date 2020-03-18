---
title: Jak promítnout nový typ (LINQ na XML) (C#)
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: 5205a0c56651271dea0181ed96518c0e9d7f95f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168990"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a>Jak promítnout nový typ (LINQ na XML) (C#)

Další příklady v této části ukázaly dotazy, které `string`vracejí <xref:System.Collections.Generic.IEnumerable%601> `int`výsledky <xref:System.Collections.Generic.IEnumerable%601> od , <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> z , a . Jedná se o běžné typy výsledků, ale nejsou vhodné pro každý scénář. V mnoha případech budete chtít, aby <xref:System.Collections.Generic.IEnumerable%601> vaše dotazy vrátit jiný typ.

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak vytvořit instanci objektů v `select` klauzuli. Kód nejprve definuje novou třídu s konstruktorem a `select` poté upraví příkaz tak, aby výraz byl novou instancí nové třídy.

Tento příklad používá následující dokument XML: [Ukázkový soubor XML: Typický nákupní objednávka (LINQ to XML).](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)

```csharp
class NameQty
{
    public string name;
    public int qty;
    public NameQty(string n, int q)
    {
        name = n;
        qty = q;
    }
};

class Program {
    public static void Main()
    {
        XElement po = XElement.Load("PurchaseOrder.xml");
  
        IEnumerable<NameQty> nqList =
            from n in po.Descendants("Item")
            select new NameQty(
                    (string)n.Element("ProductName"),
                    (int)n.Element("Quantity")
                );
  
        foreach (NameQty n in nqList)
            Console.WriteLine(n.name + ":" + n.qty);
    }
}
```

Tento příklad <xref:System.Xml.Linq.XContainer.Element%2A> používá metodu, která byla zavedena v tématu [Jak načíst jeden podřízený prvek (LINQ do XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md). Používá také přetypování k načtení hodnot prvků, <xref:System.Xml.Linq.XContainer.Element%2A> které jsou vráceny metodou.  

Tento příklad vytváří následující výstup:

```output
Lawnmower:1
Baby Monitor:2
```
