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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1587b2c4d19833c615c5a10a2fe0d6b28e854aca
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45698325"
---
# <a name="order-preservation-in-plinq"></a>Zachování pořadí v PLINQ
V PLINQ je cílem pro zajištění maximálního výkonu při zachování správnosti. Dotaz by měl, poběží stejně rychle, ale stále správné výsledky. V některých případech vyžaduje správnosti pořadí zdrojové sekvence zachování; řazení však může být výpočetně náročné. Ve výchozím nastavení, proto PLINQ Nezachovávat hodnotu pořadí zdrojové sekvence. V tomto ohledu PLINQ podobá [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)], ale na rozdíl od LINQ to Objects, která zachovávají řazení.  
  
 Pokud chcete přepsat výchozí chování, můžete zapnout zachování pořadí pomocí <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operátoru u zdrojové sekvence. Zachování pořadí v dotazu později pak můžete vypnout pomocí <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> metody. U obou metod zpracování dotazu se podle heuristickými metodami, které určují, jestli se má spustit dotaz paralelně nebo jako sekvenční. Další informace najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
 Následující příklad ukazuje neuspořádané paralelní dotaz, který filtruje pro všechny prvky, které odpovídají podmínce, bez pokusu o řazení výsledků žádným způsobem.  
  
 [!code-csharp[PLINQ#8](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#8)]
 [!code-vb[PLINQ#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#8)]  
  
 Tento dotaz nevrátí nutně prvních 1 000 města ze zdrojové sekvence, které splňují podmínku, ale místo toho některé sadu 1000 města, které splňují podmínku. Operátory dotazu PLINQ oddílů zdrojové sekvence do více dílčích sekvencí, které jsou zpracovány jako souběžných úloh. Pokud zachování pořadí není zadán, jsou výsledky z každého oddílu předat do další fáze dotazu v libovolném pořadí. Oddíl také může přinést podmnožinu jeho výsledky před pokračováním zpracovat zbývající prvky. Výsledné pořadí může být jiný pokaždé, když. Aplikaci nelze určit, protože závisí na způsobu operačního systému plánuje vlákna.  
  
 Následující příklad přepisuje výchozí chování pomocí <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operátoru u zdrojové sekvence. To zajistí, že <xref:System.Linq.ParallelEnumerable.Take%2A> metoda vrátí prvních 1 000 města ze zdrojové sekvence, které splňují podmínku.  
  
 [!code-csharp[PLINQ#9](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#9)]
 [!code-vb[PLINQ#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#9)]  
  
 Ale tento dotaz pravděpodobně nejde spustit stejně rychle jako neuspořádaná verze protože musí udržovat přehled o původní pořadí v rámci oddíly a v době sloučení Ujistěte se, že řazení konzistentní vzhledem k aplikacím. Proto doporučujeme použít <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> pouze v případě potřeby a pouze pro ty části dotazu, které je vyžadují. Při zachování pořadí se už nevyžaduje, použijte <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> ho chcete vypnout. Následující příklad toho dosahuje vytvořením dvou dotazů.  
  
 [!code-csharp[PLINQ#6](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#6)]
 [!code-vb[PLINQ#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#6)]  
  
 Všimněte si, že PLINQ zachová řazení sekvence vytvářených operátorů pro zbývající část dotazu. Jinými slovy, operátory, jako například <xref:System.Linq.ParallelEnumerable.OrderBy%2A> a <xref:System.Linq.ParallelEnumerable.ThenBy%2A> zacházeno, jako kdyby byly následovány voláním <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>.  
  
## <a name="query-operators-and-ordering"></a>Operátory pro dotazování a řazení  
 Následující operátory dotazu zavést zachování pořadí na všechny následné operace v dotazu nebo dokud <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> se volá:  
  
-   <xref:System.Linq.ParallelEnumerable.OrderBy%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.ThenBy%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>  
  
 Následující operátory dotazu PLINQ může v některých případech vyžadovat seřazených zdrojových posloupností pro správné výsledky:  
  
-   <xref:System.Linq.ParallelEnumerable.Reverse%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.TakeWhile%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.SkipWhile%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.Zip%2A>  
  
 Některé operátory dotazu PLINQ chovat jinak, v závislosti na tom, jestli je jejich zdrojové sekvence uspořádaná nebo ne. V následující tabulce jsou uvedeny tyto operátory.  
  
|Operátor|Výsledek při řazení zdrojové sekvence|Výsledek po Neseřazený zdrojové sekvence|  
|--------------|------------------------------------------------|--------------------------------------------------|  
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A>|Nedeterministická výstupu neasociativní či nekomutativní operace|Nedeterministická výstupu neasociativní či nekomutativní operace|  
|<xref:System.Linq.ParallelEnumerable.All%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.Any%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.Average%2A>|Nedeterministická výstupu neasociativní či nekomutativní operace|Nedeterministická výstupu neasociativní či nekomutativní operace|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Seřazených výsledků|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Seřazených výsledků|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Count%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.Distinct%2A>|Seřazených výsledků|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.ElementAt%2A>|Vrátí zadaný element|Libovolný element|  
|<xref:System.Linq.ParallelEnumerable.ElementAtOrDefault%2A>|Vrátí zadaný element|Libovolný element|  
|<xref:System.Linq.ParallelEnumerable.Except%2A>|Neuspořádané výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.First%2A>|Vrátí zadaný element|Libovolný element|  
|<xref:System.Linq.ParallelEnumerable.FirstOrDefault%2A>|Vrátí zadaný element|Libovolný element|  
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Nedeterministicky paralelně|Nedeterministicky paralelně|  
|<xref:System.Linq.ParallelEnumerable.GroupBy%2A>|Seřazených výsledků|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.GroupJoin%2A>|Seřazených výsledků|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Intersect%2A>|Seřazených výsledků|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Join%2A>|Seřazených výsledků|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Last%2A>|Vrátí zadaný element|Libovolný element|  
|<xref:System.Linq.ParallelEnumerable.LastOrDefault%2A>|Vrátí zadaný element|Libovolný element|  
|<xref:System.Linq.ParallelEnumerable.LongCount%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.Min%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.OrderBy%2A>|Znovu uspořádá sekvenci|Spustí novou uspořádanou oddílu|  
|<xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>|Znovu uspořádá sekvenci|Spustí novou uspořádanou oddílu|  
|<xref:System.Linq.ParallelEnumerable.Range%2A>|Není k dispozici (stejné jako výchozí <xref:System.Linq.ParallelEnumerable.AsParallel%2A> )|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.Repeat%2A>|Není k dispozici (stejné jako výchozí <xref:System.Linq.ParallelEnumerable.AsParallel%2A>)|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Obrátí|Neprovádí žádnou akci.|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Seřazených výsledků|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Select%2A> (indexované)|Seřazených výsledků|Neuspořádané výsledky.|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Seřazené výsledky.|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A> (indexované)|Seřazené výsledky.|Neuspořádané výsledky.|  
|<xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>|Seřazený porovnání|Neuspořádané porovnání|  
|<xref:System.Linq.ParallelEnumerable.Single%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.SingleOrDefault%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|Přeskočí první *n* elementy|Přeskočí všechny *n* elementy|  
|<xref:System.Linq.ParallelEnumerable.SkipWhile%2A>|Seřazené výsledky.|Nedeterministická. SkipWhile – provádí na aktuální pořadí|  
|<xref:System.Linq.ParallelEnumerable.Sum%2A>|Nedeterministická výstupu neasociativní či nekomutativní operace|Nedeterministická výstupu neasociativní či nekomutativní operace|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|Přijímá první `n` elementy|Přijímá libovolné `n` elementy|  
|<xref:System.Linq.ParallelEnumerable.TakeWhile%2A>|Seřazených výsledků|Nedeterministická. TakeWhile – provádí na aktuální pořadí|  
|<xref:System.Linq.ParallelEnumerable.ThenBy%2A>|Doplňky `OrderBy`|Doplňky `OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>|Doplňky `OrderBy`|Doplňky `OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ToArray%2A>|Seřazených výsledků|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.ToDictionary%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.ToList%2A>|Seřazených výsledků|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.ToLookup%2A>|Seřazených výsledků|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Union%2A>|Seřazených výsledků|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Seřazených výsledků|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Where%2A> (indexované)|Seřazených výsledků|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Zip%2A>|Seřazených výsledků|Neuspořádané výsledky|  
  
 Neuspořádané výsledky nejsou které se náhodně pomíchají aktivně; jednoduše nemají nějakou zvláštní logiku pořadí, které jsou použity k nim. V některých případech může Neseřazený dotazu zachovat řazení zdrojové sekvence. Pro dotazy, které používají indexované vyberte operátor PLINQ zaručuje, že je v pořadí rostoucí indexů, ale neposkytuje žádné záruky v indexy, které se přiřadí prvky, které přijde výstup elementy.  
  
## <a name="see-also"></a>Viz také:

- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
