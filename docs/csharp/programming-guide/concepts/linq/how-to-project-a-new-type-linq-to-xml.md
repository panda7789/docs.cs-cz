---
title: Jak projektovat nový typ (LINQ to XML) (C#)
description: Naučte se vytvářet dotazy v LINQ to XML v jazyce C#, které vracejí IEnumerable <T> typů kromě XElement, String nebo int, které jsou popsány v jiných příkladech.
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: 013ea852a64b77c04ac583b4d9b71e8006cd4976
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104645"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a>Jak projektovat nový typ (LINQ to XML) (C#)

Další příklady v této části obsahují dotazy, které vracejí výsledky od <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> z `string` a do <xref:System.Collections.Generic.IEnumerable%601> `int` . Jedná se o běžné typy výsledků, ale nejsou vhodné pro všechny scénáře. V mnoha případech budete chtít, aby dotazy vracely <xref:System.Collections.Generic.IEnumerable%601> nějaký jiný typ.

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak vytvořit instanci objektů v `select` klauzuli. Kód nejprve definuje novou třídu s konstruktorem a poté upraví `select` příkaz tak, aby výraz byl novou instancí nové třídy.

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

Tento příklad používá <xref:System.Xml.Linq.XContainer.Element%2A> metodu, která byla představena v tématu [jak načíst jeden podřízený prvek (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md). Používá také přetypování k načtení hodnot prvků, které jsou vráceny <xref:System.Xml.Linq.XContainer.Element%2A> metodou.  

Tento příklad vytvoří následující výstup:

```output
Lawnmower:1
Baby Monitor:2
```
