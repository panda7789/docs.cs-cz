---
title: 'Postupy: Projekt a nový typ (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: bec4e7c7d87dffb90b49b76aa00a5de093d68436
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593044"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a>Postupy: Projekt a nový typ (LINQ to XML) (C#)

Další příklady v této části obsahují dotazy, které vracejí <xref:System.Collections.Generic.IEnumerable%601> výsledky `int` <xref:System.Xml.Linq.XElement> <xref:System.Collections.Generic.IEnumerable%601> od, z `string`a do <xref:System.Collections.Generic.IEnumerable%601> . Jedná se o běžné typy výsledků, ale nejsou vhodné pro všechny scénáře. V mnoha případech budete chtít, aby dotazy vracely <xref:System.Collections.Generic.IEnumerable%601> nějaký jiný typ.

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak vytvořit instanci objektů v `select` klauzuli. Kód nejprve definuje novou třídu s konstruktorem a poté upraví `select` příkaz tak, aby výraz byl novou instancí nové třídy.

V tomto příkladu se používá následující dokument XML: [Ukázkový soubor XML: Typická nákupní objednávka (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).

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
