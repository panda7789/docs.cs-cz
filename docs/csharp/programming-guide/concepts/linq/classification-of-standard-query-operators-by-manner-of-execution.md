---
title: Klasifikace standardních operátorů dotazu podle způsobu spuštění (C#)
description: 'Přečtěte si o způsobech provádění standardního operátoru dotazu v jazyce C# pro LINQ to Objects: okamžité, odložené streamování a odložené vysílání bez datových proudů.'
ms.date: 07/20/2015
ms.assetid: b9435ce5-a7cf-4182-9f01-f3468a5533dc
ms.openlocfilehash: dd496e232de2c7ed10a8aaa7cec84f8136495cce
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105502"
---
# <a name="classification-of-standard-query-operators-by-manner-of-execution-c"></a>Klasifikace standardních operátorů dotazu podle způsobu spuštění (C#)
LINQ to Objects implementace standardních metod operátoru dotazu se spouštějí jedním ze dvou hlavních způsobů: Immediate nebo odloženo. Operátory dotazů, které používají odložené provádění, lze dále rozdělit do dvou kategorií: streaming a non-stream. Pokud víte, jak se spouštějí různé operátory dotazu, může vám porozumět výsledkům, které získáte z daného dotazu. To platí zejména v případě, že se změnil zdroj dat nebo pokud vytváříte dotaz nad jiným dotazem. Toto téma klasifikuje standardní operátory dotazu podle jejich způsobu provádění.  
  
## <a name="manners-of-execution"></a>Způsoby spuštění  
  
### <a name="immediate"></a>Projev  
 Okamžité provedení znamená, že zdroj dat je čten a operace je provedena v místě v kódu, kde je dotaz deklarován. Všechny standardní operátory dotazu, které vracejí jeden nevyčíslitelné výsledek, se spustí okamžitě.  
  
### <a name="deferred"></a>Odložené  
 Odložené spuštění znamená, že operace není provedena v místě v kódu, kde je dotaz deklarován. Operace se provádí pouze v případě, že je proměnná dotazu vyhodnocena, například pomocí `foreach` příkazu. To znamená, že výsledky spuštění dotazu závisí na obsahu zdroje dat při spuštění dotazu, nikoli při definování dotazu. Pokud je proměnná dotazu vyčíslovaná víckrát, výsledky se můžou pokaždé lišit. Skoro všechny standardní operátory dotazu, jejichž návratový typ je <xref:System.Collections.Generic.IEnumerable%601> nebo se má <xref:System.Linq.IOrderedEnumerable%601> provést odvoditelné způsobem.  
  
 Operátory dotazů, které používají odložené provádění, se dají klasifikovat taky jako streamování nebo nestreamování.  
  
#### <a name="streaming"></a>Streamování  
 Operátoři streamování nemusí číst všechna zdrojová data před tím, než budou vracet prvky. V době spuštění operátor streamování provede svoji operaci na každém zdrojovém prvku, protože je čten a v případě potřeby vytvoří prvek. Operátor streamování bude nadále číst zdrojové prvky, dokud nebude možné vytvořit element výsledku. To znamená, že je možné načíst více než jeden zdrojový prvek pro získání jednoho prvku výsledku.  
  
#### <a name="non-streaming"></a>Bez streamování  
 Nestreamované operátory musí číst všechna zdrojová data předtím, než mohou získat výsledný element. Do této kategorie patří operace, jako je řazení nebo seskupování. V době spuštění nestreamující operátory dotazů čtou všechna zdrojová data, umístí je do struktury dat, provede operaci a vrátí výsledné prvky.  
  
## <a name="classification-table"></a>Klasifikační tabulka  
 Následující tabulka klasifikuje jednotlivé standardní metody operátoru dotazu podle jeho metody provádění.  
  
> [!NOTE]
> Pokud je operátor označený ve dvou sloupcích, jsou v operaci zapojeny dvě vstupní sekvence a každá sekvence je vyhodnocena jinak. V těchto případech je vždy první posloupnost v seznamu parametrů, která je vyhodnocena způsobem, který je vyhodnocen jako odvoditelné streamování.  
  
|Standardní operátor dotazu|Návratový typ|Okamžité provedení|Provádění odloženého streamování|Odložené provádění bez streamování|  
|-----------------------------|-----------------|-------------------------|----------------------------------|---------------------------------------|  
|<xref:System.Linq.Enumerable.Aggregate%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.All%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.Any%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.AsEnumerable%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Average%2A>|Jedna číselná hodnota|X|||  
|<xref:System.Linq.Enumerable.Cast%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Concat%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Contains%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.Count%2A>|<xref:System.Int32>|X|||  
|<xref:System.Linq.Enumerable.DefaultIfEmpty%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Distinct%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.ElementAt%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.Empty%2A>|<xref:System.Collections.Generic.IEnumerable%601>|X|||  
|<xref:System.Linq.Enumerable.Except%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.First%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.FirstOrDefault%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.GroupBy%2A>|<xref:System.Collections.Generic.IEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.GroupJoin%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
<xref:System.Linq.Enumerable.Intersect%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.Join%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.Last%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.LastOrDefault%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.LongCount%2A>|<xref:System.Int64>|X|||  
|<xref:System.Linq.Enumerable.Max%2A>|Jedna číselná hodnota, TSource nebo TResult|X|||  
|<xref:System.Linq.Enumerable.Min%2A>|Jedna číselná hodnota, TSource nebo TResult|X|||  
|<xref:System.Linq.Enumerable.OfType%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.OrderBy%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.OrderByDescending%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.Range%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Repeat%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Reverse%2A>|<xref:System.Collections.Generic.IEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.Select%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.SelectMany%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.SequenceEqual%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.Single%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.SingleOrDefault%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.Skip%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.SkipWhile%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Sum%2A>|Jedna číselná hodnota|X|||  
|<xref:System.Linq.Enumerable.Take%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
<xref:System.Linq.Enumerable.TakeWhile%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.ThenBy%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.ThenByDescending%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.ToArray%2A>|TSource pole|X|||  
|<xref:System.Linq.Enumerable.ToDictionary%2A>|<xref:System.Collections.Generic.Dictionary%602>|X|||  
|<xref:System.Linq.Enumerable.ToList%2A>|<xref:System.Collections.Generic.IList%601>|X|||  
|<xref:System.Linq.Enumerable.ToLookup%2A>|<xref:System.Linq.ILookup%602>|X|||  
|<xref:System.Linq.Enumerable.Union%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Where%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq.Enumerable>
- [Přehled standardních operátorů dotazů (C#)](./standard-query-operators-overview.md)
- [Syntaxe výrazu dotazu pro standardní operátory dotazu (C#)](./query-expression-syntax-for-standard-query-operators.md)
- [LINQ to Objects (C#)](./linq-to-objects.md)
