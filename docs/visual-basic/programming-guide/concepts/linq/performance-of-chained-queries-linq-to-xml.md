---
title: Výkon zřetězených dotazů (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
ms.openlocfilehash: 6b87f2744f663ebd45dceb036dcaac71b80765fc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396386"
---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a>Výkon zřetězených dotazů (LINQ to XML) (Visual Basic)

Jednou z nejdůležitějších výhod LINQ (a LINQ to XML) je to, že zřetězené dotazy můžou provádět i jeden větší a složitější dotaz.

Zřetězený dotaz je dotaz, který jako svůj zdroj používá jiný dotaz. Například v následujícím jednoduchém kódu `query2` má `query1` jako svůj zdroj:

```vb
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))

Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x

Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e

For Each i As var In query2
    Console.WriteLine("{0}", CInt(i))
Next
```

Tento příklad vytvoří následující výstup:

```console
4
```

Tento řetězový dotaz poskytuje stejný profil výkonu jako iterace prostřednictvím propojeného seznamu.

- <xref:System.Xml.Linq.XContainer.Elements%2A>Osa má v podstatě stejný výkon jako iterace prostřednictvím propojeného seznamu. <xref:System.Xml.Linq.XContainer.Elements%2A>je implementován jako iterátor s odloženým vykonání. To znamená, že kromě iterace v propojeném seznamu funguje i několik práce, jako je například přidělení objektu iterátoru a udržování přehledu o stavu provádění. Tato práce může být rozdělena do dvou kategorií: práce, která se provádí v okamžiku nastavení iterátoru, a práce, která se provádí během každé iterace. Nastavení práce je malé, pevné množství práce a práce prováděná během každé iterace je úměrná počtu položek ve zdrojové kolekci.

- V `query1` `Where` klauzuli klauzule způsobí, že dotaz volá <xref:System.Linq.Enumerable.Where%2A> metodu. Tato metoda je také implementována jako iterátor. Nastavení práce se skládá z vytváření instancí delegáta, který bude odkazovat na výraz lambda, a také na normální nastavení iterátoru. Při každé iteraci se volá delegát, který spustí predikát. Nastavení práce a práce provedené během každé iterace jsou podobné práci, kterou jste provedli při iteraci přes osu.

- V `query1` klauzuli select způsobí, že dotaz vyvolá <xref:System.Linq.Enumerable.Select%2A> metodu. Tato metoda má stejný profil výkonu jako <xref:System.Linq.Enumerable.Where%2A> metoda.

- V systému `query2` `Where` má klauzule i `Select` klauzule stejný profil výkonu jako v `query1` .

 Iterace prostřednictvím `query2` je proto přímo úměrná počtu položek ve zdroji prvního dotazu, jinými slovy, lineárním časem.

## <a name="see-also"></a>Viz také

- [Výkon (LINQ to XML) (Visual Basic)](performance-linq-to-xml.md)
