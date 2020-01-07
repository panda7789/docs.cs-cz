---
title: Úvod do PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, introduction to
ms.assetid: eaa720d8-8999-4eb7-8df5-3c19ca61cad0
ms.openlocfilehash: ed1b2df57c118a0ebb6b5ffa4326b3e2eac81dec
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75632360"
---
# <a name="introduction-to-plinq"></a>Úvod do PLINQ

## <a name="what-is-a-parallel-query"></a>Co je paralelní dotaz?

LINQ (Language-Integrated Query) byl představen v .NET Framework 3,5. Nabízí jednotný model pro dotazování libovolného <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> zdroje dat bezpečným způsobem. LINQ to Objects je název pro dotazy LINQ, které jsou spouštěny proti kolekcím v paměti, jako jsou <xref:System.Collections.Generic.List%601> a pole. V tomto článku se předpokládá, že máte základní znalosti jazyka LINQ. Další informace naleznete v tématu [LINQ (Language-Integrated Query) C# ](../../csharp/programming-guide/concepts/linq/index.md) nebo [LINQ (Language-Integrated Query)-Visual Basic](../../visual-basic/programming-guide/concepts/linq/index.md).

Paralelní LINQ (PLINQ) je paralelní implementace vzoru LINQ. Dotaz PLINQ v mnoha způsobech připomíná neparalelní LINQ to Objects dotaz. PLINQ dotazy, stejně jako sekvenční dotazy LINQ, pracují na jakémkoli v paměti <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601> zdroji dat a mají odložené provádění, což znamená, že se nespustí, dokud se dotaz nevytvoří. Hlavním rozdílem je, že PLINQ se pokouší plně využívat všechny procesory systému. Provádí to rozdělením zdroje dat na segmenty a následným spuštěním dotazu na každém segmentu v samostatných pracovních vláknech paralelně na více procesorech. V mnoha případech paralelní spouštění dotazu funguje výrazně rychleji.

Pomocí paralelního provádění PLINQ může dosáhnout výrazného zlepšení výkonu oproti staršímu kódu pro určité typy dotazů, často pouze přidáním operace <xref:System.Linq.ParallelEnumerable.AsParallel%2A> dotazování do zdroje dat. Paralelismus však může zavádět své vlastní složitosti a ne všechny operace dotazů se v PLINQ rychleji spouštět. Ve skutečnosti paralelně zpomaluje některé dotazy. Proto byste měli pochopit, jak problémy, jako je řazení, ovlivňují paralelní dotazy. Další informace naleznete v tématu [Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).

> [!NOTE]
> Tato dokumentace používá lambda výrazy k definování delegátů v PLINQ. Pokud nejste obeznámeni s lambda výrazy v C# nebo Visual Basic, přečtěte si téma [lambda výrazy v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

Zbývající část tohoto článku poskytuje přehled hlavních tříd PLINQ a popisuje, jak vytvářet dotazy PLINQ. Každý oddíl obsahuje odkazy na podrobnější informace a příklady kódu.

## <a name="the-parallelenumerable-class"></a>Třída ParallelEnumerable

Třída <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> zpřístupňuje téměř všechny funkce PLINQ. Do sestavení System. Core. dll se zkompiluje a zbývající typy <xref:System.Linq?displayProperty=nameWithType> oboru názvů. Výchozí C# a Visual Basic projekty v aplikaci Visual Studio odkazují na sestavení a importují obor názvů.

<xref:System.Linq.ParallelEnumerable> zahrnuje implementace všech standardních operátorů dotazu, které LINQ to Objects podporuje, i když se o ně nepokusí paralelizovat každé z nich. Pokud neznáte LINQ, přečtěte si téma [Úvod do LINQC#()](../../csharp/programming-guide/concepts/linq/index.md) a [Úvod do LINQ (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md).

Kromě standardních operátorů dotazu obsahuje Třída <xref:System.Linq.ParallelEnumerable> sadu metod, které povolují chování specifické pro paralelní spuštění. Tyto metody specifické pro PLINQ jsou uvedeny v následující tabulce.

|ParallelEnumerable – operátor|Popis|
|---------------------------------|-----------------|
|<xref:System.Linq.ParallelEnumerable.AsParallel%2A>|Vstupní bod pro PLINQ. Určuje, že zbytek dotazu by měl být paralelní, pokud je to možné.|
|<xref:System.Linq.ParallelEnumerable.AsSequential%2A>|Určuje, že zbytek dotazu by měl být spuštěn sekvenčně, jako neparalelní dotaz LINQ.|
|<xref:System.Linq.ParallelEnumerable.AsOrdered%2A>|Určuje, že PLINQ by měl zachovat pořadí zdrojové sekvence pro zbytek dotazu nebo dokud se nezmění řazení, například použitím klauzule orderby (ORDER by in Visual Basic).|
|<xref:System.Linq.ParallelEnumerable.AsUnordered%2A>|Určuje, že PLINQ pro zbytek dotazu není vyžadován k zachování pořadí zdrojové sekvence.|
|<xref:System.Linq.ParallelEnumerable.WithCancellation%2A>|Určuje, že PLINQ by měl pravidelně monitorovat stav poskytnutého tokenu zrušení a zrušit provádění, pokud je požadován.|
|<xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A>|Určuje maximální počet procesorů, které by měl PLINQ použít k paralelizovat dotazu.|
|<xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A>|Poskytuje nápovědu ke způsobu, jakým by měl PLINQ, pokud je to možné, sloučit paralelní výsledky zpět do jediné sekvence v náročném vlákně.|
|<xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A>|Určuje, zda by měl PLINQ paralelizovat dotaz i v případě, že výchozí chování by bylo spuštěno sekvenčně.|
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Vícevláknová metoda výčtu, která na rozdíl od iterace na základě výsledků dotazu umožňuje souběžné zpracování výsledků bez předchozího sloučení zpět do vlákna příjemce.|
|přetížení <xref:System.Linq.ParallelEnumerable.Aggregate%2A>|Přetížení, které je jedinečné pro PLINQ a umožňuje mezilehlou agregaci přes místní segmenty vlákna a také konečnou agregační funkci pro kombinování výsledků všech oddílů.|

## <a name="the-opt-in-model"></a>Model výslovných přihlášení

Při psaní dotazu Přihlaste se k PLINQ vyvoláním metody rozšíření <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> ve zdroji dat, jak je znázorněno v následujícím příkladu.

[!code-csharp[PLINQ#1](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#1)]
[!code-vb[PLINQ#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#1)]

Metoda rozšíření <xref:System.Linq.ParallelEnumerable.AsParallel%2A> váže následující operátory pro dotazování, v tomto případě `where` a `select`, do <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> implementace.

## <a name="execution-modes"></a>Režimy spuštění

Ve výchozím nastavení je PLINQ konzervativní. V době spuštění PLINQ infrastruktura analyzuje celkovou strukturu dotazu. Pokud je dotaz pravděpodobně výsledkem urychlení paralelismus, PLINQ rozdělí zdrojovou sekvenci na úlohy, které lze spustit souběžně. Pokud není bezpečné paralelizovat dotaz, PLINQ pouze spustí dotaz sekvenčně. Pokud má PLINQ možnost volby mezi potenciálně nákladným paralelním algoritmem nebo levným sekvenčním algoritmem, zvolí sekvenční algoritmus ve výchozím nastavení. Můžete použít metodu <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> a výčet <xref:System.Linq.ParallelExecutionMode?displayProperty=nameWithType> k tomu, aby mohl PLINQ vybrat paralelní algoritmus. To je užitečné, když znáte testování a měření, že se konkrétní dotaz spouští paralelně. Další informace naleznete v tématu [How to: určení režimu spouštění v PLINQ](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md).

## <a name="degree-of-parallelism"></a>Stupeň paralelismu

Ve výchozím nastavení PLINQ používá všechny procesory v hostitelském počítači. Můžete určit, aby PLINQ používal maximálně zadaný počet procesorů pomocí metody <xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A>. To je užitečné, když chcete zajistit, aby ostatní procesy spuštěné v počítači dostaly určité množství času procesoru. Následující fragment kódu omezuje dotaz na využití maximálně dvou procesorů.

[!code-csharp[PLINQ#5](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#5)]
[!code-vb[PLINQ#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#5)]

V případech, kdy dotaz provádí značné množství práce vázané na nevýpočetní prostředí, jako je vstupně-výstupní operace se soubory, může být výhodné zadat stupeň paralelismu větší než počet jader v počítači.

## <a name="ordered-versus-unordered-parallel-queries"></a>Seřazené versus neuspořádané paralelní dotazy

V některých dotazech musí operátor dotazu vytvořit výsledky, které zachovávají pořadí zdrojové sekvence. PLINQ poskytuje operátor <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> pro tento účel. <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> se liší od <xref:System.Linq.ParallelEnumerable.AsSequential%2A>. Sekvence <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> je stále zpracovávána paralelně, ale její výsledky jsou uloženy do vyrovnávací paměti a seřazeny. Vzhledem k tomu, že zachování pořadí obvykle zahrnuje další práci, <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> sekvence může být zpracována pomaleji než výchozí sekvence <xref:System.Linq.ParallelEnumerable.AsUnordered%2A>. Zda je konkrétní objednaná paralelní operace rychlejší než sekvenční verze operace závisí na mnoha faktorech.

Následující příklad kódu ukazuje, jak se vyjádřit, abyste mohli seřadit zachování.

[!code-csharp[PLINQ#3](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#3)]
[!code-vb[PLINQ#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#3)]

Další informace naleznete v tématu [pořadí zachování v PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).

## <a name="parallel-vs-sequential-queries"></a>Paralelní vs. sekvenční dotazy

Některé operace vyžadují, aby se zdrojová data doručila sekvenčním způsobem. Operátory dotazu <xref:System.Linq.ParallelEnumerable> se v případě potřeby vrátí do sekvenčního režimu automaticky. Pro uživatelsky definované operátory dotazů a delegáty uživatelů, kteří vyžadují sekvenční provádění, PLINQ poskytuje metodu <xref:System.Linq.ParallelEnumerable.AsSequential%2A>. Když použijete <xref:System.Linq.ParallelEnumerable.AsSequential%2A>, všechny následné operátory v dotazu se spustí postupně, dokud <xref:System.Linq.ParallelEnumerable.AsParallel%2A> znovu zavoláte. Další informace naleznete v tématu [How to: Kombinování paralelních a sekvenčních dotazů LINQ](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md).

## <a name="options-for-merging-query-results"></a>Možnosti pro sloučení výsledků dotazu

Když je PLINQ dotaz spuštěn paralelně, jeho výsledky z každého pracovního vlákna musí být sloučeny zpátky do hlavního vlákna, aby je bylo možné spotřebovat pomocí `foreach` smyčky (`For Each` v Visual Basic), nebo vložením do seznamu nebo pole. V některých případech může být výhodné zadat konkrétní druh operace sloučení, například pro rychlejší zahájení výroby výsledků. Pro účely tohoto účelu PLINQ podporuje metodu <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> a výčet <xref:System.Linq.ParallelMergeOptions>. Další informace naleznete v tématu [možnosti sloučení v PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).

## <a name="the-forall-operator"></a>Operátor ForAll

V sekvenčních dotazech LINQ je provádění odloženo, dokud se dotaz nevytvoří ve smyčce `foreach` (`For Each` ve Visual Basic) nebo vyvoláním metody, jako je <xref:System.Linq.ParallelEnumerable.ToList%2A>, <xref:System.Linq.ParallelEnumerable.ToArray%2A> nebo <xref:System.Linq.ParallelEnumerable.ToDictionary%2A>. V PLINQ můžete také použít `foreach` k provedení dotazu a iterování výsledků. `foreach` sám o sobě ale neběží paralelně. proto je potřeba, aby se výstup ze všech paralelních úloh sloučil zpátky do vlákna, na kterém je smyčka spuštěná. V PLINQ můžete použít `foreach`, pokud je třeba zachovat konečné řazení výsledků dotazu, a také pokaždé, když zpracováváte výsledky sériovým způsobem, například při volání `Console.WriteLine` pro každý prvek. Pro rychlejší provádění dotazů, pokud není potřeba pořadí řazení, a kdy se zpracování výsledků může provádět paralelně, použijte metodu <xref:System.Linq.ParallelEnumerable.ForAll%2A> pro spuštění PLINQ dotazu. <xref:System.Linq.ParallelEnumerable.ForAll%2A> neprovádí tento finální krok sloučení. Následující příklad kódu ukazuje, jak použít metodu <xref:System.Linq.ParallelEnumerable.ForAll%2A>. Tady se používá <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>, protože je optimalizovaný pro více vláken, která se přidávají souběžně, aniž by se musely odebírat žádné položky.

[!code-csharp[PLINQ#4](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#4)]
[!code-vb[PLINQ#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#4)]

Následující ilustrace znázorňuje rozdíl mezi `foreach` a <xref:System.Linq.ParallelEnumerable.ForAll%2A> s ohledem na provádění dotazu.

![ForAll vs. ForEach](../../../docs/standard/parallel-programming/media/vs-isvnt-allvseach.png "VS_ISVNT_ALLvsEACH")

## <a name="cancellation"></a>Zrušení

PLINQ je integrován s typy zrušení v .NET Framework 4. (Další informace naleznete v tématu [zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md).) Proto lze na rozdíl od sekvenčních dotazů LINQ to Objects zrušit dotazy PLINQ. Chcete-li vytvořit PLINQ dotaz, který lze zrušit, použijte pro dotaz operátor <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> a jako argument zadejte instanci <xref:System.Threading.CancellationToken>. Je-li vlastnost <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> na tokenu nastavena na hodnotu true, PLINQ si ho upozorní, zastaví zpracování na všech vláknech a vyvolá <xref:System.OperationCanceledException>.

Je možné, že PLINQ dotaz může pokračovat ve zpracování některých prvků po nastavení tokenu zrušení.

Pro větší rychlost odezvy můžete také reagovat na žádosti o zrušení v dlouhotrvajících uživatelských delegátech. Další informace naleznete v tématu [How to: Cancel a PLINQ Query](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md).

## <a name="exceptions"></a>Výjimky

Při spuštění dotazu PLINQ může být více výjimek vyvoláno z různých vláken současně. Také kód pro zpracování výjimky může být v jiném vlákně než kód, který výjimku vyvolal. PLINQ používá typ <xref:System.AggregateException> k zapouzdření všech výjimek vyvolaných dotazem a k zařazení těchto výjimek zpět do volajícího vlákna. Ve volajícím vlákně je vyžadován pouze jeden blok try-catch. Můžete však iterovat všemi výjimkami, které jsou zapouzdřeny v <xref:System.AggregateException>, a zachytit všechny, které lze bezpečně obnovit z. Ve výjimečných případech mohou být vyvolány některé výjimky, které nejsou zabaleny do <xref:System.AggregateException>a <xref:System.Threading.ThreadAbortException>s nejsou zabaleny také.

Pokud jsou výjimky povoleny k bublinám zpět do spojovacího vlákna, pak je možné, že dotaz může pokračovat ve zpracování některých položek poté, co je vyvolána výjimka.

Další informace naleznete v tématu [How to: Handle Exceptions in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md).

## <a name="custom-partitioners"></a>Vlastní dělicí metody

V některých případech můžete zlepšit výkon dotazů vytvořením vlastního rozdělovače, který využívá některé charakteristické vlastnosti zdrojových dat. V dotazu vlastní rozdělovač sám o sobě vyčíslitelnému objektu, na který se dotazuje.

[!code-csharp[PLINQ#2](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#2)]
[!code-vb[PLINQ#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq3.vb#2)]

PLINQ podporuje pevný počet oddílů (Přestože data mohou být dynamicky přiřazena k těmto oddílům za běhu pro vyrovnávání zatížení). <xref:System.Threading.Tasks.Parallel.For%2A> a <xref:System.Threading.Tasks.Parallel.ForEach%2A> podporují pouze dynamické dělení, což znamená, že počet oddílů se v době běhu mění. Další informace najdete v tématu [vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).

## <a name="measuring-plinq-performance"></a>Měření výkonu PLINQ

V mnoha případech může být dotaz paralelní, ale režie nastavení paralelního dotazu převažuje nad nabytým výkonem. Pokud dotaz neprovádí mnoho výpočtů nebo pokud je zdroj dat malý, může PLINQ dotaz být pomalejší než sekvenční LINQ to Objects dotaz. Můžete použít paralelní Analyzátor výkonu v aplikaci Visual Studio Team Server k porovnání výkonu různých dotazů, k vyhledání problémových míst zpracování a určení, zda je dotaz spuštěn paralelně nebo sekvenčně. Další informace naleznete v tématech [Vizualizér souběžnosti](/visualstudio/profiling/concurrency-visualizer) a [Postupy: měření výkonu dotazu PLINQ](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).

## <a name="see-also"></a>Viz také:

- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)
