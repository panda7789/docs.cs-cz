---
title: Výkon zřetězených dotazů (LINQ na XML) (C#)
ms.date: 07/20/2015
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: 7deff9205e6535877efabd85257baa5b3906f41a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253125"
---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a>Výkon zřetězených dotazů (LINQ na XML) (C#)

Jednou z nejdůležitějších výhod LINQ (a LINQ na XML) je, že zřetězené dotazy lze provádět, stejně jako jeden větší, složitější dotaz.

Zřetězený dotaz je dotaz, který používá jiný dotaz jako jeho zdroj. Například v následujícím jednoduchém `query2` `query1` kódu má jako svůj zdroj:

```csharp
XElement root = new XElement("Root",
    new XElement("Child", 1),
    new XElement("Child", 2),
    new XElement("Child", 3),
    new XElement("Child", 4)
);

var query1 = from x in root.Elements("Child")
             where (int)x >= 3
             select x;

var query2 = from e in query1
             where (int)e % 2 == 0
             select e;

foreach (var i in query2)
    Console.WriteLine("{0}", (int)i);
```

Tento příklad vytváří následující výstup:

```output
4
```

Tento zřetězený dotaz poskytuje stejný profil výkonu jako iterace prostřednictvím propojeného seznamu.

- Osa <xref:System.Xml.Linq.XContainer.Elements%2A> má v podstatě stejný výkon jako iterace prostřednictvím propojeného seznamu. <xref:System.Xml.Linq.XContainer.Elements%2A>implementována jako iterátor s odloženým prováděním. To znamená, že provádí některé práce kromě iterace prostřednictvím propojeného seznamu, jako je například přidělení objektu iterátoru a sledování stavu spuštění. Tato práce může být rozdělena do dvou kategorií: práce, která se provádí v době, kdy je nastaven iterátor a práce, která se provádí během každé iterace. Instalační práce je malé, pevné množství práce a práce vykonaná během každé iterace je úměrná počtu položek ve zdrojové kolekci.

- V `query1`aplikaci klauzule `where` způsobí, <xref:System.Linq.Enumerable.Where%2A> že dotaz volá metodu. Tato metoda je také implementována jako iterátor. Instalační práce se skládá z vytvoření instance delegáta, který bude odkazovat na výraz lambda, plus normální nastavení pro iterátor. S každou iterací delegát je volána ke spuštění predikátu. Práce na nastavení a práce vykonaná během každé iterace je podobná práci vykonanou při iteraci přes osu.

- V `query1`aplikaci klauzule select způsobí, že dotaz zavolá metodu. <xref:System.Linq.Enumerable.Select%2A> Tato metoda má stejný profil <xref:System.Linq.Enumerable.Where%2A> výkonu jako metoda.

- V `query2`oblasti `where` mají klauzule i klauzule `select` stejný `query1`profil výkonnosti jako v .

Iterace `query2` prostřednictvím je tedy přímo úměrná počtu položek ve zdroji prvního dotazu, jinými slovy lineární čas. Odpovídající příklad jazyka visual basic by mít stejný profil výkonu.

Další informace o iterátorech naleznete v tématu [yield](../../../language-reference/keywords/yield.md).

Podrobnější návod na řetězení dotazů společně naleznete v [tématu Výuka: Řetězení dotazů společně](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).
