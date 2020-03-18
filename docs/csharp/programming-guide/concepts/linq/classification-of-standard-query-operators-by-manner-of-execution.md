---
title: Klasifikace operátorů standardních dotazů podle způsobu spuštění (C#)
ms.date: 07/20/2015
ms.assetid: b9435ce5-a7cf-4182-9f01-f3468a5533dc
ms.openlocfilehash: ccf8fced5c92ceaaf84f9240e235da0e2b56ac1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69924282"
---
# <a name="classification-of-standard-query-operators-by-manner-of-execution-c"></a>Klasifikace operátorů standardních dotazů podle způsobu spuštění (C#)
Linq to Objects implementace metody operátoru standardní dotaz spustit jedním ze dvou hlavních způsobů: okamžité nebo odložené. Operátory dotazu, které používají odložené spuštění lze dodatečně rozdělit do dvou kategorií: streamování a bez streamování. Pokud víte, jak se spouštějí různé operátory dotazů, může vám pomoci pochopit výsledky, které získáte z daného dotazu. To platí zejména v případě, že se mění zdroj dat nebo pokud vytváříte dotaz nad jiným dotazem. Toto téma klasifikuje standardní operátory dotazů podle jejich způsobu provádění.  
  
## <a name="manners-of-execution"></a>Způsoby provedení  
  
### <a name="immediate"></a>Okamžité  
 Okamžité spuštění znamená, že zdroj dat je číst a operace se provádí v bodě v kódu, kde je deklarován dotaz. Všechny standardní operátory dotazu, které vrátí jeden, nevýčíslitelný výsledek spustit okamžitě.  
  
### <a name="deferred"></a>Odložené  
 Odložené spuštění znamená, že operace není provedena v bodě v kódu, kde je deklarován dotaz. Operace se provádí pouze v případě, že je proměnná `foreach` dotazu uvedena, například pomocí příkazu. To znamená, že výsledky spuštění dotazu závisí na obsahu zdroje dat při spuštění dotazu, nikoli při definování dotazu. Pokud je proměnná dotazu výčtu vícekrát, výsledky se mohou lišit pokaždé. Téměř všechny standardní operátory dotazu, jejichž návratový typ je <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IOrderedEnumerable%601> spustit odložené způsobem.  
  
 Operátory dotazů, které používají odložené spuštění lze navíc klasifikovat jako streamování nebo jiné datové proudy.  
  
#### <a name="streaming"></a>Streamování  
 Operátory streamování nemusí číst všechna zdrojová data před tím, než poskytují prvky. V době spuštění operátor streamování provádí svou operaci na každý zdrojový prvek při čtení a dává prvek v případě potřeby. Operátor streamování pokračuje ve čtení zdrojových prvků, dokud nelze vytvořit prvek výsledku. To znamená, že více než jeden zdrojový prvek může být přečten a vytvořit jeden prvek výsledku.  
  
#### <a name="non-streaming"></a>Nedatové přenosy  
 Operátory bez streamování musí číst všechna zdrojová data, než mohou přinést prvek výsledku. Operace, jako je řazení nebo seskupení spadají do této kategorie. V době spuštění operátory dotazů bez streamování číst všechna zdrojová data, dát do datové struktury, provést operaci a výnos výsledné prvky.  
  
## <a name="classification-table"></a>Klasifikační tabulka  
 Následující tabulka klasifikuje každou metodu operátoru standardního dotazu podle její metody provádění.  
  
> [!NOTE]
> Pokud operátor je označen ve dvou sloupcích, dvě vstupní sekvence jsou zapojeny do operace a každá sekvence je vyhodnocena odlišně. V těchto případech je vždy první sekvence v seznamu parametrů, který je vyhodnocen v odložené, streamování způsobem.  
  
|Standardní operátor dotazu|Návratový typ|Okamžité provedení|Odložené spuštění streamování|Odložené spuštění nestreamování|  
|-----------------------------|-----------------|-------------------------|----------------------------------|---------------------------------------|  
|<xref:System.Linq.Enumerable.Aggregate%2A>|Tsource|×|||  
|<xref:System.Linq.Enumerable.All%2A>|<xref:System.Boolean>|×|||  
|<xref:System.Linq.Enumerable.Any%2A>|<xref:System.Boolean>|×|||  
|<xref:System.Linq.Enumerable.AsEnumerable%2A>|<xref:System.Collections.Generic.IEnumerable%601>||×||  
|<xref:System.Linq.Enumerable.Average%2A>|Jedna číselná hodnota|×|||  
|<xref:System.Linq.Enumerable.Cast%2A>|<xref:System.Collections.Generic.IEnumerable%601>||×||  
|<xref:System.Linq.Enumerable.Concat%2A>|<xref:System.Collections.Generic.IEnumerable%601>||×||  
|<xref:System.Linq.Enumerable.Contains%2A>|<xref:System.Boolean>|×|||  
|<xref:System.Linq.Enumerable.Count%2A>|<xref:System.Int32>|×|||  
|<xref:System.Linq.Enumerable.DefaultIfEmpty%2A>|<xref:System.Collections.Generic.IEnumerable%601>||×||  
|<xref:System.Linq.Enumerable.Distinct%2A>|<xref:System.Collections.Generic.IEnumerable%601>||×||  
|<xref:System.Linq.Enumerable.ElementAt%2A>|Tsource|×|||  
|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A>|Tsource|×|||  
|<xref:System.Linq.Enumerable.Empty%2A>|<xref:System.Collections.Generic.IEnumerable%601>|×|||  
|<xref:System.Linq.Enumerable.Except%2A>|<xref:System.Collections.Generic.IEnumerable%601>||×|×|  
|<xref:System.Linq.Enumerable.First%2A>|Tsource|×|||  
|<xref:System.Linq.Enumerable.FirstOrDefault%2A>|Tsource|×|||  
|<xref:System.Linq.Enumerable.GroupBy%2A>|<xref:System.Collections.Generic.IEnumerable%601>|||×|  
|<xref:System.Linq.Enumerable.GroupJoin%2A>|<xref:System.Collections.Generic.IEnumerable%601>||×|×|  
<xref:System.Linq.Enumerable.Intersect%2A>|<xref:System.Collections.Generic.IEnumerable%601>||×|×|  
|<xref:System.Linq.Enumerable.Join%2A>|<xref:System.Collections.Generic.IEnumerable%601>||×|×|  
|<xref:System.Linq.Enumerable.Last%2A>|Tsource|×|||  
|<xref:System.Linq.Enumerable.LastOrDefault%2A>|Tsource|×|||  
|<xref:System.Linq.Enumerable.LongCount%2A>|<xref:System.Int64>|×|||  
|<xref:System.Linq.Enumerable.Max%2A>|Jedna číselná hodnota, TSource nebo TResult|×|||  
|<xref:System.Linq.Enumerable.Min%2A>|Jedna číselná hodnota, TSource nebo TResult|×|||  
|<xref:System.Linq.Enumerable.OfType%2A>|<xref:System.Collections.Generic.IEnumerable%601>||×||  
|<xref:System.Linq.Enumerable.OrderBy%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||×|  
|<xref:System.Linq.Enumerable.OrderByDescending%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||×|  
|<xref:System.Linq.Enumerable.Range%2A>|<xref:System.Collections.Generic.IEnumerable%601>||×||  
|<xref:System.Linq.Enumerable.Repeat%2A>|<xref:System.Collections.Generic.IEnumerable%601>||×||  
|<xref:System.Linq.Enumerable.Reverse%2A>|<xref:System.Collections.Generic.IEnumerable%601>|||×|  
|<xref:System.Linq.Enumerable.Select%2A>|<xref:System.Collections.Generic.IEnumerable%601>||×||  
|<xref:System.Linq.Enumerable.SelectMany%2A>|<xref:System.Collections.Generic.IEnumerable%601>||×||  
|<xref:System.Linq.Enumerable.SequenceEqual%2A>|<xref:System.Boolean>|×|||  
|<xref:System.Linq.Enumerable.Single%2A>|Tsource|×|||  
|<xref:System.Linq.Enumerable.SingleOrDefault%2A>|Tsource|×|||  
|<xref:System.Linq.Enumerable.Skip%2A>|<xref:System.Collections.Generic.IEnumerable%601>||×||  
|<xref:System.Linq.Enumerable.SkipWhile%2A>|<xref:System.Collections.Generic.IEnumerable%601>||×||  
|<xref:System.Linq.Enumerable.Sum%2A>|Jedna číselná hodnota|×|||  
|<xref:System.Linq.Enumerable.Take%2A>|<xref:System.Collections.Generic.IEnumerable%601>||×||  
<xref:System.Linq.Enumerable.TakeWhile%2A>|<xref:System.Collections.Generic.IEnumerable%601>||×||  
|<xref:System.Linq.Enumerable.ThenBy%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||×|  
|<xref:System.Linq.Enumerable.ThenByDescending%2A>|<xref:System.Linq.IOrderedEnumerable%601>|||×|  
|<xref:System.Linq.Enumerable.ToArray%2A>|Pole TSource|×|||  
|<xref:System.Linq.Enumerable.ToDictionary%2A>|<xref:System.Collections.Generic.Dictionary%602>|×|||  
|<xref:System.Linq.Enumerable.ToList%2A>|<xref:System.Collections.Generic.IList%601>|×|||  
|<xref:System.Linq.Enumerable.ToLookup%2A>|<xref:System.Linq.ILookup%602>|×|||  
|<xref:System.Linq.Enumerable.Union%2A>|<xref:System.Collections.Generic.IEnumerable%601>||×||  
|<xref:System.Linq.Enumerable.Where%2A>|<xref:System.Collections.Generic.IEnumerable%601>||×||  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq.Enumerable>
- [Standardní operátory dotazů – přehled (C#)](./standard-query-operators-overview.md)
- [Syntaxe výrazu dotazu pro standardní operátory dotazů (C#)](./query-expression-syntax-for-standard-query-operators.md)
- [LINQ na objekty (C#)](./linq-to-objects.md)
