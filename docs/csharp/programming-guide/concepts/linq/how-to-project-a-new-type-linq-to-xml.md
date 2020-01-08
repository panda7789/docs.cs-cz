---
title: Jak projektovat nový typ (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: 3a54677fa0fa2845dd635f89ddb7ed1c5c279e03
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345723"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a>Jak projektovat nový typ (LINQ to XML) (C#)

Další příklady v této části obsahují dotazy, které vracejí výsledky jako <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> `string`a <xref:System.Collections.Generic.IEnumerable%601> `int`. Jedná se o běžné typy výsledků, ale nejsou vhodné pro všechny scénáře. V mnoha případech budete chtít, aby dotazy vracely <xref:System.Collections.Generic.IEnumerable%601> nějakého jiného typu.

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak vytvořit instanci objektů v klauzuli `select`. Kód nejprve definuje novou třídu s konstruktorem a poté upraví příkaz `select` tak, aby výraz byl novou instancí nové třídy.

Tento příklad používá následující dokument XML: [vzorový soubor XML: typická nákupní objednávka (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).

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

Tento příklad používá metodu <xref:System.Xml.Linq.XContainer.Element%2A>, která byla představena v tématu [jak načíst jeden podřízený prvek (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md). Používá také přetypování k načtení hodnot prvků, které jsou vráceny metodou <xref:System.Xml.Linq.XContainer.Element%2A>.  

Tento příklad vytvoří následující výstup:

```output
Lawnmower:1
Baby Monitor:2
```
