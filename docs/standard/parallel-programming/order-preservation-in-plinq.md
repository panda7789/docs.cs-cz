---
title: Zachování pořadí v PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, order preservation
ms.assetid: 10d202bc-19e1-4b5c-bbf1-9a977322a9ca
ms.openlocfilehash: 5b067fa277816e6105d37047c6c4996a4cbb9b5a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138224"
---
# <a name="order-preservation-in-plinq"></a>Zachování pořadí v PLINQ
V PLINQ je cílem maximalizovat výkon a přitom zachovat správnost. Dotaz by měl běžet co nejrychleji, ale stále vytváří správné výsledky. V některých případech správnost vyžaduje, aby bylo zachováno pořadí zdrojové sekvence; řazení se ale dá vyvýpočetně nákladný. Proto ve výchozím nastavení PLINQ nezachovává pořadí zdrojové sekvence. V tomto ohledu se PLINQ podobá [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)], ale je na rozdíl od LINQ to Objects, která zachovává řazení.  
  
 Chcete-li přepsat výchozí chování, můžete zapnout zachování pořadí pomocí operátoru <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> na zdrojové sekvenci. Zachování pořadí pak můžete vypnout později v dotazu pomocí metody <xref:System.Linq.ParallelEnumerable.AsUnordered%2A>. U obou metod je dotaz zpracován na základě heuristiky, které určují, zda má být dotaz spuštěn paralelně nebo jako sekvenční. Další informace naleznete v tématu [Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
 Následující příklad ukazuje neuspořádaný paralelní dotaz, který filtruje všechny prvky, které odpovídají podmínce, bez pokusu o řazení výsledků jakýmkoli způsobem.  
  
 [!code-csharp[PLINQ#8](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#8)]
 [!code-vb[PLINQ#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#8)]  
  
 Tento dotaz nutně nevytvoří první 1000 města ve zdrojové sekvenci, která splňuje podmínku, ale místo některé sady 1000 měst, které splňují podmínku. Operátory dotazů PLINQ rozdělí zdrojovou sekvenci do několika dílčích sekvencí, které jsou zpracovávány jako souběžné úlohy. Pokud není zadané zachování pořadí, výsledky z každého oddílu se předají do další fáze dotazu v libovolném pořadí. Oddíl také může vracet podmnožinu výsledků před tím, než bude pokračovat ve zpracování zbývajících prvků. Výsledné pořadí může být kdykoli jiné. Vaše aplikace nemůže řídit tuto skutečnost, protože závisí na tom, jak operační systém naplánuje vlákna.  
  
 Následující příklad přepisuje výchozí chování pomocí operátoru <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> na zdrojové sekvenci. Tím se zajistí, že metoda <xref:System.Linq.ParallelEnumerable.Take%2A> vrátí první 1000 města ve zdrojové sekvenci, která splňuje podmínku.  
  
 [!code-csharp[PLINQ#9](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#9)]
 [!code-vb[PLINQ#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#9)]  
  
 Tento dotaz se ale pravděpodobně nespustí tak rychle jako neuspořádaná verze, protože musí sledovat původní pořadí v celém oddílu a čas sloučení, aby bylo řazení konzistentní. Proto doporučujeme použít <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> jenom v případě, že je to nutné a jenom pro ty části dotazu, které to vyžadují. Pokud se už nepožaduje zachování pořadí, použijte <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> k jeho vypnutí. Následující příklad dosahuje sestavením dvou dotazů.  
  
 [!code-csharp[PLINQ#6](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#6)]
 [!code-vb[PLINQ#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#6)]  
  
 Všimněte si, že PLINQ zachovává pořadí sekvence vytvářené operátory pro uložení pořadí pro zbytek dotazu. Jinými slovy, operátory, jako <xref:System.Linq.ParallelEnumerable.OrderBy%2A> a <xref:System.Linq.ParallelEnumerable.ThenBy%2A>, se považují za, jako kdyby byly následovány volání <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>.  
  
## <a name="query-operators-and-ordering"></a>Operátory a řazení dotazů  
 Následující operátory dotazů zavádí zachování pořadí do všech následných operací v dotazu nebo dokud se nevolá <xref:System.Linq.ParallelEnumerable.AsUnordered%2A>:  
  
- <xref:System.Linq.ParallelEnumerable.OrderBy%2A>  
  
- <xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>  
  
- <xref:System.Linq.ParallelEnumerable.ThenBy%2A>  
  
- <xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>  
  
 Následující operátory dotazů PLINQ můžou v některých případech vyžadovat správné výsledky pro seřazené zdrojové sekvence:  
  
- <xref:System.Linq.ParallelEnumerable.Reverse%2A>  
  
- <xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>  
  
- <xref:System.Linq.ParallelEnumerable.TakeWhile%2A>  
  
- <xref:System.Linq.ParallelEnumerable.SkipWhile%2A>  
  
- <xref:System.Linq.ParallelEnumerable.Zip%2A>  
  
 Některé operátory dotazů PLINQ se chovají odlišně v závislosti na tom, zda je jejich zdrojová sekvence uspořádána nebo neuspořádaná. Následující tabulka uvádí tyto operátory.  
  
|Operátor|Výsledek při objednání zdrojové sekvence|Výsledek v případě neuspořádané zdrojové sekvence|  
|--------------|------------------------------------------------|--------------------------------------------------|  
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A>|Nedeterministický výstup pro neasociativní nebo noncommutative operace|Nedeterministický výstup pro neasociativní nebo noncommutative operace|  
|<xref:System.Linq.ParallelEnumerable.All%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.Any%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.Average%2A>|Nedeterministický výstup pro neasociativní nebo noncommutative operace|Nedeterministický výstup pro neasociativní nebo noncommutative operace|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Seřazené výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Seřazené výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Count%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.Distinct%2A>|Seřazené výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.ElementAt%2A>|Vrátit zadaný element|Libovolný element|  
|<xref:System.Linq.ParallelEnumerable.ElementAtOrDefault%2A>|Vrátit zadaný element|Libovolný element|  
|<xref:System.Linq.ParallelEnumerable.Except%2A>|Neuspořádané výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.First%2A>|Vrátit zadaný element|Libovolný element|  
|<xref:System.Linq.ParallelEnumerable.FirstOrDefault%2A>|Vrátit zadaný element|Libovolný element|  
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Provede nedeterministické paralelní zpracování.|Provede nedeterministické paralelní zpracování.|  
|<xref:System.Linq.ParallelEnumerable.GroupBy%2A>|Seřazené výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.GroupJoin%2A>|Seřazené výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Intersect%2A>|Seřazené výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Join%2A>|Seřazené výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Last%2A>|Vrátit zadaný element|Libovolný element|  
|<xref:System.Linq.ParallelEnumerable.LastOrDefault%2A>|Vrátit zadaný element|Libovolný element|  
|<xref:System.Linq.ParallelEnumerable.LongCount%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.Min%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.OrderBy%2A>|Změna pořadí sekvence|Spustí novou seřazenou sekci.|  
|<xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>|Změna pořadí sekvence|Spustí novou seřazenou sekci.|  
|<xref:System.Linq.ParallelEnumerable.Range%2A>|Nelze použít (stejné výchozí nastavení jako <xref:System.Linq.ParallelEnumerable.AsParallel%2A>)|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.Repeat%2A>|Nelze použít (stejné výchozí nastavení jako <xref:System.Linq.ParallelEnumerable.AsParallel%2A>)|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Obrátí|Neprovádí žádnou akci.|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Seřazené výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Select%2A> (indexované)|Seřazené výsledky|Neuspořádané výsledky.|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Seřazené výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A> (indexované)|Seřazené výsledky|Neuspořádané výsledky.|  
|<xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>|Seřazené porovnání|Neuspořádané porovnání|  
|<xref:System.Linq.ParallelEnumerable.Single%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.SingleOrDefault%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|Přeskočí prvních *n* prvků.|Přeskočí všechny elementy *n* .|  
|<xref:System.Linq.ParallelEnumerable.SkipWhile%2A>|Seřazené výsledky|Nedeterministická. Provede SkipWhile – v aktuálním libovolném pořadí.|  
|<xref:System.Linq.ParallelEnumerable.Sum%2A>|Nedeterministický výstup pro neasociativní nebo noncommutative operace|Nedeterministický výstup pro neasociativní nebo noncommutative operace|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|Přebírá první `n` prvky|Přebírá libovolné `n` prvky.|  
|<xref:System.Linq.ParallelEnumerable.TakeWhile%2A>|Seřazené výsledky|Nedeterministická. Provede TakeWhile – v aktuálním libovolném pořadí.|  
|<xref:System.Linq.ParallelEnumerable.ThenBy%2A>|Doplňky `OrderBy`|Doplňky `OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>|Doplňky `OrderBy`|Doplňky `OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ToArray%2A>|Seřazené výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.ToDictionary%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.ToList%2A>|Seřazené výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.ToLookup%2A>|Seřazené výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Union%2A>|Seřazené výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Seřazené výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Where%2A> (indexované)|Seřazené výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Zip%2A>|Seřazené výsledky|Neuspořádané výsledky|  
  
 Neuspořádané výsledky nejsou aktivně přemísené; jednoduše na ně neplatí žádná speciální logika řazení. V některých případech může neuspořádaný dotaz zachovat řazení zdrojové sekvence. U dotazů, které používají operátor indexovaného výběru, PLINQ garantuje, že výstupní prvky budou v pořadí rostoucích indexů vycházet, ale neposkytuje žádné záruky, které indexy budou přiřazeny k prvkům.  
  
## <a name="see-also"></a>Viz také:

- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
