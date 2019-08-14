---
title: 'Postupy: Projekt a nový typ (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: 2bb521d1445dcecdad8b9c7b28bed90e1e38c8e8
ms.sourcegitcommit: d98fdb087d9c8aba7d2cb93fe4b4ee35a2308cee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2019
ms.locfileid: "69012930"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a>Postupy: Projekt a nový typ (LINQ to XML) (C#)

Další příklady v této části obsahují dotazy, které vracejí <xref:System.Collections.Generic.IEnumerable%601> výsledky `int` <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> od, z `string`a do <xref:System.Collections.Generic.IEnumerable%601> . Jedná se o běžné typy výsledků, ale nejsou vhodné pro všechny scénáře. V mnoha případech budete chtít, aby dotazy vracely <xref:System.Collections.Generic.IEnumerable%601> nějaký jiný typ.

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak vytvořit instanci objektů v `select` klauzuli. Kód nejprve definuje novou třídu s konstruktorem a poté upraví `select` příkaz tak, aby výraz byl novou instancí nové třídy.

V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).

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

Tento příklad používá <xref:System.Xml.Linq.XContainer.Element%2A> metodu, která byla představena v tématu [postupy: Načtení jednoho podřízeného elementu (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md). Používá také přetypování k načtení hodnot prvků, které jsou vráceny <xref:System.Xml.Linq.XContainer.Element%2A> metodou.  

Tento příklad vytvoří následující výstup:

```console
Lawnmower:1
Baby Monitor:2
```
