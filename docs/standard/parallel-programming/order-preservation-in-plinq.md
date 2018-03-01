---
title: "Zachování pořadí v PLINQ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, order preservation
ms.assetid: 10d202bc-19e1-4b5c-bbf1-9a977322a9ca
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 164dce7c58e1ce44972e0e390e4f0bf2be8de548
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="order-preservation-in-plinq"></a>Zachování pořadí v PLINQ
Cílem je v PLINQ, maximalizovat výkon při zachování správnosti. Dotaz by měl spustit co nejrychleji, ale stále správné výsledky. V některých případech správnost vyžaduje pořadí zdrojové sekvence dat; řazení však může být náročné. Proto ve výchozím nastavení, PLINQ nezachová pořadí zdrojové sekvence. V tomto ohledu PLINQ podobá [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)], ale na rozdíl od LINQ na objekty, které zachováváno.  
  
 Pokud chcete přepsat výchozí chování, můžete zapnout na zachování pořadí pomocí <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operátor na zdrojové sekvence. Zachování pořadí později v dotazu pak můžete vypnout pomocí <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> metoda. U obou metod zpracování dotazu se podle heuristiky určující, jestli se má provést dotaz jako paralelní nebo jako po sobě jdoucích. Další informace najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
 Následující příklad ukazuje neuspořádaný paralelní dotaz, který filtruje pro všechny prvky, které vyhovují podmínce, aniž by došlo k pokusu o řazení výsledků žádným způsobem.  
  
 [!code-csharp[PLINQ#8](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#8)]
 [!code-vb[PLINQ#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#8)]  
  
 Tento dotaz nevrátí nutně měst prvních 1000 ve zdrojové sekvence, které splňují podmínku, ale spíš některé sadu 1000 města, které splňují podmínku. Operátory dotazu PLINQ oddílu pořadí zdroje do více dílčích sekvencí, které jsou zpracovány jako souběžné úlohy. Pokud zachování pořadí není zadán, jsou výsledky z každý oddíl předáno do další fáze dotazu v libovolném pořadí. Oddíl může také yield podmnožinu své výsledky před nadále zpracovat zbývající elementy. Výsledné pořadí může být jiný pokaždé, když. Aplikace nelze určit, protože závisí na tom, jak operačního systému plánuje vláken.  
  
 Následující příklad přepisuje výchozí chování pomocí <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operátor na zdrojové sekvence. To zajistí, že <xref:System.Linq.ParallelEnumerable.Take%2A> metoda vrátí měst prvních 1000 v pořadí zdroje, které splňují podmínku.  
  
 [!code-csharp[PLINQ#9](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#9)]
 [!code-vb[PLINQ#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#9)]  
  
 Však tento dotaz pravděpodobně nejde spustit jako je neuspořádaného verze rychlého protože musí udržovat přehled o původním pořadí skrz oddíly a v době sloučení zajistěte, aby byl řazení konzistentní. Proto doporučujeme použít <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> jenom v případě, že je potřeba a pouze pro ty části dotazu, které je vyžadují. Při zachování pořadí se už nevyžaduje, použijte <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> ho vypnout. Následující příklad toho dosahuje pomocí vytvořením dvou dotazů.  
  
 [!code-csharp[PLINQ#6](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#6)]
 [!code-vb[PLINQ#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#6)]  
  
 Všimněte si, že PLINQ zachovává řazení pořadí vyprodukované operátorů pro zbytek dotazu. Jinými slovy, operátory, jako například <xref:System.Linq.ParallelEnumerable.OrderBy%2A> a <xref:System.Linq.ParallelEnumerable.ThenBy%2A> jsou zpracovány jako by byly dodrženy voláním <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>.  
  
## <a name="query-operators-and-ordering"></a>Operátory dotazu a řazení  
 Následující operátory dotazu zavádí zachování pořadí do všechny operace v dotazu, nebo dokud <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> se označuje jako:  
  
-   <xref:System.Linq.ParallelEnumerable.OrderBy%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.ThenBy%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>  
  
 V některých případech může následující operátory dotazu PLINQ vyžadovat pořadí seřazené zdroje pro správné výsledky:  
  
-   <xref:System.Linq.ParallelEnumerable.Reverse%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.TakeWhile%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.SkipWhile%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.Zip%2A>  
  
 Některé operátory dotazu PLINQ chovat jinak, v závislosti na tom, jestli jejich zdrojové sekvence uspořádaná nebo ne. Následující tabulka uvádí tyto operátory.  
  
|Operátor|Výsledek, když je seřazené zdrojové sekvence|Výsledek, když neuspořádaného zdrojové sekvence|  
|--------------|------------------------------------------------|--------------------------------------------------|  
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A>|Nedeterministická výstup neasociativní či nekomutativní operace|Nedeterministická výstup neasociativní či nekomutativní operace|  
|<xref:System.Linq.ParallelEnumerable.All%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.Any%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.Average%2A>|Nedeterministická výstup neasociativní či nekomutativní operace|Nedeterministická výstup neasociativní či nekomutativní operace|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Seřazené výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Seřazené výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Count%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.Distinct%2A>|Seřazené výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.ElementAt%2A>|Vrátí zadaný element|Libovolný element|  
|<xref:System.Linq.ParallelEnumerable.ElementAtOrDefault%2A>|Vrátí zadaný element|Libovolný element|  
|<xref:System.Linq.ParallelEnumerable.Except%2A>|Neuspořádané výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.First%2A>|Vrátí zadaný element|Libovolný element|  
|<xref:System.Linq.ParallelEnumerable.FirstOrDefault%2A>|Vrátí zadaný element|Libovolný element|  
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Nedeterministicky paralelně|Nedeterministicky paralelně|  
|<xref:System.Linq.ParallelEnumerable.GroupBy%2A>|Seřazené výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.GroupJoin%2A>|Seřazené výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Intersect%2A>|Seřazené výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Join%2A>|Seřazené výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Last%2A>|Vrátí zadaný element|Libovolný element|  
|<xref:System.Linq.ParallelEnumerable.LastOrDefault%2A>|Vrátí zadaný element|Libovolný element|  
|<xref:System.Linq.ParallelEnumerable.LongCount%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.Min%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.OrderBy%2A>|Změní pořadí|Nové spuštění řazení části|  
|<xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>|Změní pořadí|Nové spuštění řazení části|  
|<xref:System.Linq.ParallelEnumerable.Range%2A>|Není k dispozici (stejné jako výchozí <xref:System.Linq.ParallelEnumerable.AsParallel%2A> )|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.Repeat%2A>|Není k dispozici (stejné jako výchozí <xref:System.Linq.ParallelEnumerable.AsParallel%2A>)|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Obrátí|Neprovádí žádnou akci.|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Seřazené výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>(indexované)|Seřazené výsledky|Neuspořádané výsledky.|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Seřazené výsledky.|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>(indexované)|Seřazené výsledky.|Neuspořádané výsledky.|  
|<xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>|Seřazené porovnání|Neuspořádané porovnání|  
|<xref:System.Linq.ParallelEnumerable.Single%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.SingleOrDefault%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|Přeskočí první  *n*  elementy|Přeskočí žádné  *n*  elementy|  
|<xref:System.Linq.ParallelEnumerable.SkipWhile%2A>|Seřazené výsledky.|Nedeterministická. SkipWhile provádí aktuální pořadí|  
|<xref:System.Linq.ParallelEnumerable.Sum%2A>|Nedeterministická výstup neasociativní či nekomutativní operace|Nedeterministická výstup neasociativní či nekomutativní operace|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|Přebírá první `n` elementy|Přebírá všechny `n` elementy|  
|<xref:System.Linq.ParallelEnumerable.TakeWhile%2A>|Seřazené výsledky|Nedeterministická. TakeWhile provádí aktuální pořadí|  
|<xref:System.Linq.ParallelEnumerable.ThenBy%2A>|Doplňky`OrderBy`|Doplňky`OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>|Doplňky`OrderBy`|Doplňky`OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ToArray%2A>|Seřazené výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.ToDictionary%2A>|Nelze použít|Nelze použít|  
|<xref:System.Linq.ParallelEnumerable.ToList%2A>|Seřazené výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.ToLookup%2A>|Seřazené výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Union%2A>|Seřazené výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Seřazené výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>(indexované)|Seřazené výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Zip%2A>|Seřazené výsledky|Neuspořádané výsledky|  
  
 Neuspořádané výsledky nejsou aktivně nesprávním místě; jednoduše nemají žádné speciální řazení logiky na ně použity. V některých případech může uchovávat dotaz Neseřazený řazení zdrojové sekvence. Pro dotazy, které používají indexované vyberte operátor PLINQ zaručuje, že bude výstup elementy přijdete v pořadí podle zvyšující indexy, ale neposkytuje žádné záruky, o které indexy, které budou přiřazené pro prvky, které.  
  
## <a name="see-also"></a>Viz také  
 [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
