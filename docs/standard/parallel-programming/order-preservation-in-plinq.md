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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138224"
---
# <a name="order-preservation-in-plinq"></a>Zachování pořadí v PLINQ
V PLINQ, cílem je maximalizovat výkon při zachování správnosti. Dotaz by měl běžet co nejrychleji, ale stále vytvářet správné výsledky. V některých případech správnost vyžaduje, aby bylo zachováno pořadí zdrojové sekvence; však řazení může být výpočtově nákladné. Proto ve výchozím nastavení PLINQ nezachová pořadí zdrojové sekvence. V tomto ohledu PLINQ [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)]podobá , ale je na rozdíl od LINQ na objekty, které zachovávají řazení.  
  
 Chcete-li přepsat výchozí chování, můžete zapnout zachování <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> objednávky pomocí operátoru ve zdrojové sekvenci. Potom můžete vypnout zachování objednávky později <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> v dotazu pomocí metody. S oběma metodami je dotaz zpracován na základě heuristiky, které určují, zda má být dotaz spuštěn jako paralelní nebo sekvenční. Další informace naleznete [v tématu Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
 Následující příklad ukazuje neuspořádaný paralelní dotaz, který filtruje všechny prvky, které odpovídají podmínce, aniž by se pokoušeli jakýmkoli způsobem se řadit výsledky.  
  
 [!code-csharp[PLINQ#8](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#8)]
 [!code-vb[PLINQ#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#8)]  
  
 Tento dotaz nemusí nutně vytvořit první 1000 měst ve zdrojové sekvenci, které splňují podmínku, ale spíše některé sady 1000 měst, které splňují podmínku. Plinq operátory dotazu rozdělit zdrojové sekvence do více dílčích sekvencí, které jsou zpracovány jako souběžné úkoly. Pokud není zadáno zachování objednávky, výsledky z každého oddílu jsou předány do další fáze dotazu v libovolném pořadí. Oddíl může také přinést podmnožinu jeho výsledků před pokračováním zpracování zbývajících prvků. Výsledné pořadí se může pokaždé lišit. Aplikace to nemůže řídit, protože závisí na tom, jak operační systém naplánuje podprocesy.  
  
 Následující příklad přepíše výchozí chování <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> pomocí operátoru ve zdrojové sekvenci. Tím je zajištěno, že <xref:System.Linq.ParallelEnumerable.Take%2A> metoda vrátí prvních 1000 měst ve zdrojové sekvenci, které splňují podmínku.  
  
 [!code-csharp[PLINQ#9](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#9)]
 [!code-vb[PLINQ#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#9)]  
  
 Tento dotaz však pravděpodobně nespustí tak rychle jako neuspořádané verze, protože musí sledovat původní řazení v rámci oddílů a v době sloučení zajistit, že řazení je konzistentní. Proto doporučujeme použít <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> pouze v případě, že je požadováno a pouze pro ty části dotazu, které to vyžadují. Pokud již není nutné uchování objednávky, použijte <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> jej vypněte. Následující příklad dosahuje tím, že skládá dva dotazy.  
  
 [!code-csharp[PLINQ#6](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#6)]
 [!code-vb[PLINQ#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#6)]  
  
 Všimněte si, že PLINQ zachovává pořadí sekvence vyrobené operátory uložení objednávky pro zbytek dotazu. Jinými slovy, operátory, jako <xref:System.Linq.ParallelEnumerable.OrderBy%2A> jsou a <xref:System.Linq.ParallelEnumerable.ThenBy%2A> jsou považovány <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>za by byly následovány voláním .  
  
## <a name="query-operators-and-ordering"></a>Operátory dotazů a řazení  
 Následující operátory dotazu zavádějí uchování objednávek <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> do všech následných operací v dotazu nebo dokud není volána:  
  
- <xref:System.Linq.ParallelEnumerable.OrderBy%2A>  
  
- <xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>  
  
- <xref:System.Linq.ParallelEnumerable.ThenBy%2A>  
  
- <xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>  
  
 Následující operátory dotazů PLINQ mohou v některých případech vyžadovat uspořádané zdrojové sekvence, aby byly k dosažení správných výsledků:  
  
- <xref:System.Linq.ParallelEnumerable.Reverse%2A>  
  
- <xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>  
  
- <xref:System.Linq.ParallelEnumerable.TakeWhile%2A>  
  
- <xref:System.Linq.ParallelEnumerable.SkipWhile%2A>  
  
- <xref:System.Linq.ParallelEnumerable.Zip%2A>  
  
 Některé operátory dotazů PLINQ se chovají odlišně, v závislosti na tom, zda je jejich zdrojová sekvence uspořádaná nebo neuspořádaná. V následující tabulce jsou uvedeny tyto operátory.  
  
|Operátor|Výsledek při seřazené zdrojové sekvenci|Výsledek při neuspořádané zdrojové sekvenci|  
|--------------|------------------------------------------------|--------------------------------------------------|  
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A>|Nedeterministický výstup pro neasociativní nebo nekommutační operace|Nedeterministický výstup pro neasociativní nebo nekommutační operace|  
|<xref:System.Linq.ParallelEnumerable.All%2A>|Neuvedeno|Neuvedeno|  
|<xref:System.Linq.ParallelEnumerable.Any%2A>|Neuvedeno|Neuvedeno|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Neuvedeno|Neuvedeno|  
|<xref:System.Linq.ParallelEnumerable.Average%2A>|Nedeterministický výstup pro neasociativní nebo nekommutační operace|Nedeterministický výstup pro neasociativní nebo nekommutační operace|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Objednané výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Objednané výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Count%2A>|Neuvedeno|Neuvedeno|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Neuvedeno|Neuvedeno|  
|<xref:System.Linq.ParallelEnumerable.Distinct%2A>|Objednané výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.ElementAt%2A>|Vrátit zadaný prvek|Libovolný prvek|  
|<xref:System.Linq.ParallelEnumerable.ElementAtOrDefault%2A>|Vrátit zadaný prvek|Libovolný prvek|  
|<xref:System.Linq.ParallelEnumerable.Except%2A>|Neuspořádané výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.First%2A>|Vrátit zadaný prvek|Libovolný prvek|  
|<xref:System.Linq.ParallelEnumerable.FirstOrDefault%2A>|Vrátit zadaný prvek|Libovolný prvek|  
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Provádí nedeterministicky paralelně|Provádí nedeterministicky paralelně|  
|<xref:System.Linq.ParallelEnumerable.GroupBy%2A>|Objednané výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.GroupJoin%2A>|Objednané výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Intersect%2A>|Objednané výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Join%2A>|Objednané výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Last%2A>|Vrátit zadaný prvek|Libovolný prvek|  
|<xref:System.Linq.ParallelEnumerable.LastOrDefault%2A>|Vrátit zadaný prvek|Libovolný prvek|  
|<xref:System.Linq.ParallelEnumerable.LongCount%2A>|Neuvedeno|Neuvedeno|  
|<xref:System.Linq.ParallelEnumerable.Min%2A>|Neuvedeno|Neuvedeno|  
|<xref:System.Linq.ParallelEnumerable.OrderBy%2A>|Přeřazování pořadí|Spustí nový objednaný oddíl.|  
|<xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>|Přeřazování pořadí|Spustí nový objednaný oddíl.|  
|<xref:System.Linq.ParallelEnumerable.Range%2A>|Nepoužije se (stejné výchozí nastavení jako <xref:System.Linq.ParallelEnumerable.AsParallel%2A> )|Neuvedeno|  
|<xref:System.Linq.ParallelEnumerable.Repeat%2A>|Nepoužije se (stejné výchozí nastavení jako <xref:System.Linq.ParallelEnumerable.AsParallel%2A>)|Neuvedeno|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Obrátí|Neprovádí žádnou akci.|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Objednané výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>(indexováno)|Objednané výsledky|Neuspořádané výsledky.|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Seřazené výsledky.|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>(indexováno)|Seřazené výsledky.|Neuspořádané výsledky.|  
|<xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>|Objednané porovnání|Neuspořádané porovnání|  
|<xref:System.Linq.ParallelEnumerable.Single%2A>|Neuvedeno|Neuvedeno|  
|<xref:System.Linq.ParallelEnumerable.SingleOrDefault%2A>|Neuvedeno|Neuvedeno|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|Přeskočí první *n* prvků|Přeskočí všechny *n* prvky|  
|<xref:System.Linq.ParallelEnumerable.SkipWhile%2A>|Seřazené výsledky.|Nedeterministické. Provádí SkipWhile v aktuálním libovolném pořadí|  
|<xref:System.Linq.ParallelEnumerable.Sum%2A>|Nedeterministický výstup pro neasociativní nebo nekommutační operace|Nedeterministický výstup pro neasociativní nebo nekommutační operace|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|Bere `n` první prvky|Bere `n` všechny prvky|  
|<xref:System.Linq.ParallelEnumerable.TakeWhile%2A>|Objednané výsledky|Nedeterministické. Provádí TakeWhile v aktuálním libovolném pořadí|  
|<xref:System.Linq.ParallelEnumerable.ThenBy%2A>|Doplňky`OrderBy`|Doplňky`OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>|Doplňky`OrderBy`|Doplňky`OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ToArray%2A>|Objednané výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.ToDictionary%2A>|Neuvedeno|Neuvedeno|  
|<xref:System.Linq.ParallelEnumerable.ToList%2A>|Objednané výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.ToLookup%2A>|Objednané výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Union%2A>|Objednané výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Objednané výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>(indexováno)|Objednané výsledky|Neuspořádané výsledky|  
|<xref:System.Linq.ParallelEnumerable.Zip%2A>|Objednané výsledky|Neuspořádané výsledky|  
  
 Neuspořádané výsledky nejsou aktivně zamíchány; jednoduše nemají žádnou zvláštní logiku objednávání. V některých případech neuspořádaný dotaz může zachovat řazení zdrojové sekvence. U dotazů, které používají indexovaný operátor Select, PLINQ zaručuje, že výstupní prvky budou vycházet v pořadí rostoucích indexů, ale neposkytuje žádné záruky, o kterých indexech budou přiřazeny které prvky.  
  
## <a name="see-also"></a>Viz také

- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
