---
title: "Klasifikace standardních operátorů dotazu podle metody provedení (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: b9435ce5-a7cf-4182-9f01-f3468a5533dc
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ad1ad72526b7293cd81528bf1880b2326289f177
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="classification-of-standard-query-operators-by-manner-of-execution-c"></a>Klasifikace standardních operátorů dotazu podle metody provedení (C#)
LINQ na objekty implementace metod operátor standardní dotaz spustit v jednom ze dvou způsobů hlavní: okamžitou nebo odloženě. Operátory dotazu, které používají odložené provedení lze dále rozdělit do dvou kategorií: streamování a bez vysílání datového proudu. Pokud víte, jak provést operátory různých dotazu, se vám mohou pomoci porozumět výsledky, které můžete získat z daný dotaz. To platí hlavně pokud zdroj dat se mění, nebo pokud vytváříte dotazu nad další dotaz. Toto téma klasifikuje standardních operátorů dotazu podle metody jejich provedení.  
  
## <a name="manners-of-execution"></a>Způsobů spuštění  
  
### <a name="immediate"></a>Okamžitou  
 Okamžité spuštění znamená, že zdroj dat je pro čtení a operace proběhne v bodě v kódu, kde je deklarovaná dotazu. Všechny operátory standardní dotazu, které vrácení výsledku jeden, vyčíslitelná spustit okamžitě.  
  
### <a name="deferred"></a>Odložené  
 Odložené provedení znamená, že operaci není provést v bodě v kódu, kde je deklarovaná dotaz. Operaci se provádí pouze v případě, že proměnná dotazu uvedené, například pomocí `foreach` příkaz. To znamená, že výsledky zpracování dotazu závisí na obsahu zdroje dat, když je místo, když je definována dotaz spustit dotaz. Pokud proměnná dotazu je výčet vícekrát, výsledky mohou lišit pokaždé, když. Téměř všechny standardní operátory dotazu s návratovým typem <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Linq.IOrderedEnumerable%601> provést odložené způsobem.  
  
 Operátory dotazu, které používají odložené provedení můžete dále jsou klasifikovány jako streamování nebo jiných datových proudů.  
  
#### <a name="streaming"></a>streamování  
 Streamování operátory nemusíte před jejich získání prvků si přečtěte všechna zdrojová data. V době spuštění operátor streamování provede jeho operace pro každý zdroj element tak, jak je pro čtení a vypočítá prvku podle potřeby. Operátor streamování pokračovat ve čtení zdrojové elementy, dokud je možné vytvořit element výsledek. To znamená, že může být více než jeden element source pro vytvoření jeden element výsledek ke čtení.  
  
#### <a name="non-streaming"></a>Streamování  
 Non-operátory pro datový proud musí čtení všechna zdrojová data, před dávají element výsledek. Do této kategorie patří operací, jako je řazení nebo seskupování. V době spuštění-streamování operátory dotazu číst všechna zdrojová data, umístí jej do datová struktura, operaci provést a získání výsledné prvků.  
  
## <a name="classification-table"></a>Tabulka klasifikace  
 V následující tabulce klasifikuje každá metoda operátor standardní dotaz podle jeho metoda spuštění.  
  
> [!NOTE]
>  Pokud operátor je označen ve dvou sloupcích, dvou vstupních sekvencí jsou součástí operaci a každé pořadí je vyhodnocovány jinak. V těchto případech je vždy první pořadí v seznamu parametrů, který se vyhodnotí v odložené, streamování způsobem.  
  
|Operátor standardní dotazu|Návratový typ|Okamžité provedení|Odložené provedení streamování|Odložení bez streamování provádění|  
|-----------------------------|-----------------|-------------------------|----------------------------------|---------------------------------------|  
|<xref:System.Linq.Enumerable.Aggregate%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.All%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.Any%2A>|<xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.AsEnumerable%2A>|<xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Average%2A>|Jeden číselná hodnota|X|||  
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
|<xref:System.Linq.Enumerable.Max%2A>|Jednu číselnou hodnotu, TSource nebo TResult|X|||  
|<xref:System.Linq.Enumerable.Min%2A>|Jednu číselnou hodnotu, TSource nebo TResult|X|||  
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
|<xref:System.Linq.Enumerable.Sum%2A>|Jeden číselná hodnota|X|||  
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
 <xref:System.Linq.Enumerable>  
 [Přehled standardních operátorů dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Syntaxe výrazu dotazu pro standardní operátory dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)  
 [LINQ na objekty (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
