---
title: Výkon zřetězených dotazů (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: 7deff9205e6535877efabd85257baa5b3906f41a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253125"
---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a>Výkon zřetězených dotazů (LINQ to XML) (C#)

Jednou z nejdůležitějších výhod LINQ (a LINQ to XML) je to, že zřetězené dotazy můžou provádět i jeden větší a složitější dotaz.

Zřetězený dotaz je dotaz, který jako svůj zdroj používá jiný dotaz. Například v následujícím jednoduchém kódu `query2` má `query1` jako svůj zdroj:

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

Tento příklad vytvoří následující výstup:

```output
4
```

Tento řetězový dotaz poskytuje stejný profil výkonu jako iterace prostřednictvím propojeného seznamu.

- <xref:System.Xml.Linq.XContainer.Elements%2A> Osa má v podstatě stejný výkon jako iterace prostřednictvím propojeného seznamu. <xref:System.Xml.Linq.XContainer.Elements%2A>je implementován jako iterátor s odloženým vykonání. To znamená, že kromě iterace v propojeném seznamu funguje i několik práce, jako je například přidělení objektu iterátoru a udržování přehledu o stavu provádění. Tato práce může být rozdělena do dvou kategorií: práce, která se provádí v okamžiku nastavení iterátoru, a práce, která se provádí během každé iterace. Nastavení práce je malé, pevné množství práce a práce prováděná během každé iterace je úměrná počtu položek ve zdrojové kolekci.

- V `query1` `where` klauzuli klauzule způsobí, <xref:System.Linq.Enumerable.Where%2A> že dotaz volá metodu. Tato metoda je také implementována jako iterátor. Nastavení práce se skládá z vytváření instancí delegáta, který bude odkazovat na výraz lambda, a také na normální nastavení iterátoru. Při každé iteraci se volá delegát, který spustí predikát. Nastavení práce a práce provedené během každé iterace jsou podobné práci, kterou jste provedli při iteraci přes osu.

- V `query1`klauzuli select způsobí, že dotaz <xref:System.Linq.Enumerable.Select%2A> vyvolá metodu. Tato metoda má stejný profil výkonu jako <xref:System.Linq.Enumerable.Where%2A> metoda.

- V `query2`systémumá `query1`klauzule i klauzule stejný profil výkonu jako v. `select` `where`

Iterace prostřednictvím `query2` je proto přímo úměrná počtu položek ve zdroji prvního dotazu, jinými slovy, lineárním časem. Odpovídající příklad Visual Basic by měl stejný profil výkonu.

Další informace o iterátorech najdete v tématu [yield](../../../language-reference/keywords/yield.md).

Podrobnější kurz o zřetězení dotazů společně najdete v [kurzu: Zřetězení dotazů dohromady](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).
