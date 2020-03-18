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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75632360"
---
# <a name="introduction-to-plinq"></a>Úvod do PLINQ

## <a name="what-is-a-parallel-query"></a>Co je paralelní dotaz?

Jazykově integrovaný dotaz (LINQ) byl zaveden v rozhraní .NET Framework 3.5. Obsahuje jednotný model pro dotazování libovolného <xref:System.Collections.IEnumerable?displayProperty=nameWithType> zdroje nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> zdroje dat způsobem, který je bezpečný pro daný typ. LINQ to Objects je název pro dotazy LINQ, které jsou <xref:System.Collections.Generic.List%601> spuštěny proti in-memory kolekce, jako jsou pole. Tento článek předpokládá, že máte základní znalosti LINQ. Další informace naleznete v [tématu Jazyk integrovaný dotaz (LINQ) - C#](../../csharp/programming-guide/concepts/linq/index.md) nebo [jazykintegrovaný dotaz (LINQ) - Visual Basic](../../visual-basic/programming-guide/concepts/linq/index.md).

Paralelní LINQ (PLINQ) je paralelní implementace vzoru LINQ. Dotaz PLINQ v mnoha ohledech se podobá non paralelní LINQ na objekty dotazu. PLINQ dotazy, stejně jako sekvenční LINQ <xref:System.Collections.IEnumerable> dotazy, pracovat na libovolné v paměti nebo <xref:System.Collections.Generic.IEnumerable%601> zdroj dat a mají odložené spuštění, což znamená, že nezačnou provádění, dokud není uveden výčet dotazu. Hlavním rozdílem je, že PLINQ se snaží plně využít všech procesorů v systému. Provede to rozdělením zdroje dat do segmentů a následným spuštěním dotazu v každém segmentu v samostatných pracovních vláknech paralelně na více procesorech. V mnoha případech paralelní spuštění znamená, že dotaz běží výrazně rychleji.

Prostřednictvím paralelního provádění MŮŽE PLINQ dosáhnout významné zlepšení výkonu oproti staršímu <xref:System.Linq.ParallelEnumerable.AsParallel%2A> kódu pro určité druhy dotazů, často pouhým přidáním operace dotazu do zdroje dat. Paralelismus však můžete zavést své vlastní složitosti a ne všechny operace dotazu spustit rychleji v PLINQ. Ve skutečnosti paralelizace ve skutečnosti zpomaluje určité dotazy. Proto byste měli pochopit, jak problémy, jako je řazení ovlivnit paralelní dotazy. Další informace naleznete [v tématu Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).

> [!NOTE]
> Tato dokumentace používá lambda výrazy definovat delegáty v PLINQ. Pokud nejste obeznámeni s lambda výrazy v jazyce C# nebo Visual Basic, naleznete [lambda výrazy v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

Zbývající část tohoto článku poskytuje přehled hlavní plinq třídy a popisuje, jak vytvořit plinq dotazy. Každá část obsahuje odkazy na podrobnější informace a příklady kódu.

## <a name="the-parallelenumerable-class"></a>The ParallelEnumerable Class

Třída <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> zveřejňuje téměř všechny funkce PLINQ. Je a ostatní <xref:System.Linq?displayProperty=nameWithType> typy oboru názvů jsou zkompilovány do sestavení System.Core.dll. Výchozí projekty jazyka C# a Visual Basic v sadě Visual Studio odkazují na sestavení a importují obor názvů.

<xref:System.Linq.ParallelEnumerable>zahrnuje implementace všech operátorů standardní dotaz, který podporuje LINQ na objekty, i když se nepokouší paralelizovat každý z nich. Pokud nejste obeznámeni s LINQ, naleznete [v tématu Úvod do LINQ (C#)](../../csharp/programming-guide/concepts/linq/index.md) a [Úvod do LINQ (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md).

Kromě standardních operátorů dotazu <xref:System.Linq.ParallelEnumerable> obsahuje třída sadu metod, které umožňují chování specifické pro paralelní spuštění. Tyto metody specifické pro PLINQ jsou uvedeny v následující tabulce.

|Operátor ParallelEnumerable|Popis|
|---------------------------------|-----------------|
|<xref:System.Linq.ParallelEnumerable.AsParallel%2A>|Vstupní bod pro PLINQ. Určuje, že zbytek dotazu by měl být paralelizován, pokud je to možné.|
|<xref:System.Linq.ParallelEnumerable.AsSequential%2A>|Určuje, že zbytek dotazu by měl být spuštěn postupně jako dotaz LINQ bez paralelního.|
|<xref:System.Linq.ParallelEnumerable.AsOrdered%2A>|Určuje, že PLINQ by měl zachovat pořadí zdrojové sekvence pro zbytek dotazu nebo dokud pořadí se změní, například pomocí orderby (Order By v jazyce Visual Basic).|
|<xref:System.Linq.ParallelEnumerable.AsUnordered%2A>|Určuje, že PLINQ pro zbytek dotazu není nutné zachovat pořadí zdrojové sekvence.|
|<xref:System.Linq.ParallelEnumerable.WithCancellation%2A>|Určuje, že plinq by měl pravidelně sledovat stav zadaný token zrušení a zrušit provádění, pokud je požadováno.|
|<xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A>|Určuje maximální počet procesorů, které by měl PLINQ použít k paralelizaci dotazu.|
|<xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A>|Poskytuje nápovědu o tom, jak PLINQ by měl, pokud je to možné, sloučit paralelní výsledky zpět do pouze jednu sekvenci na náročné vlákno.|
|<xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A>|Určuje, zda má funkce PLINQ paralelizovat dotaz i v případě, že by výchozí chování bylo jeho postupné spuštění.|
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Metoda vícevláknového výčtu, která na rozdíl od iterace nad výsledky dotazu umožňuje paralelní zpracování výsledků bez předchozího sloučení zpět do vlákna příjemce.|
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A>Přetížení|Přetížení, které je jedinečné pro PLINQ a umožňuje zprostředkující agregaci přes místní oddíly podprocesu, plus konečné agregace funkce kombinovat výsledky všech oddílů.|

## <a name="the-opt-in-model"></a>The Opt-in Model

Při psaní dotazu se přihlaste k plinq <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> vyvoláním metody rozšíření ve zdroji dat, jak je znázorněno v následujícím příkladu.

[!code-csharp[PLINQ#1](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#1)]
[!code-vb[PLINQ#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#1)]

Metoda <xref:System.Linq.ParallelEnumerable.AsParallel%2A> rozšíření váže následné operátory dotazu, `where` `select`v tomto <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> případě a , implementace.

## <a name="execution-modes"></a>Režimy provádění

Ve výchozím nastavení je PLINQ konzervativní. Za běhu infrastruktury PLINQ analyzuje celkovou strukturu dotazu. Pokud dotaz je pravděpodobné, že výnos zrychlení paralelizace, PLINQ oddíly zdrojové sekvence do úlohy, které lze spustit souběžně. Pokud není bezpečné paralelizovat dotaz, PLINQ pouze spustí dotaz postupně. Pokud PLINQ má na výběr mezi potenciálně nákladné paralelní algoritmus nebo levný sekvenční algoritmus, zvolí sekvenční algoritmus ve výchozím nastavení. Můžete použít <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> metodu <xref:System.Linq.ParallelExecutionMode?displayProperty=nameWithType> a výčet pokyn PLINQ vybrat paralelní algoritmus. To je užitečné, když víte, testování a měření, že konkrétní dotaz se spouští rychleji paralelně. Další informace naleznete v [tématu How to: Specify the Execution Mode in PLINQ](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md).

## <a name="degree-of-parallelism"></a>Stupeň paralelismu

Ve výchozím nastavení používá funkce PLINQ všechny procesory v hostitelském počítači. Pomocí <xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A> metody můžete dát pokyn PLINQ, aby používal maximálně zadaný počet procesorů. To je užitečné, pokud chcete zajistit, aby ostatní procesy spuštěné v počítači obdržely určité množství času procesoru. Následující úryvek omezuje dotaz na využití maximálně dvou procesorů.

[!code-csharp[PLINQ#5](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#5)]
[!code-vb[PLINQ#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#5)]

V případech, kdy dotaz provádí značné množství práce bez výpočetnívázané práce, jako je například vstupně-výstupních řízení souborů, může být užitečné určit stupeň paralelismu větší než počet jader v počítači.

## <a name="ordered-versus-unordered-parallel-queries"></a>Objednané versus neuspořádané paralelní dotazy

V některých dotazech musí operátor dotazu vytvořit výsledky, které zachovávají pořadí zdrojové sekvence. PLINQ poskytuje <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operátorpro tento účel. <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>se liší <xref:System.Linq.ParallelEnumerable.AsSequential%2A>od . Sekvence <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> je stále zpracována paralelně, ale její výsledky jsou uloženy do vyrovnávací paměti a seřazeny do vyrovnávací paměti. Vzhledem k tomu, že <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> zachování pořadí obvykle zahrnuje další <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> práci, sekvence může být zpracována pomaleji než výchozí sekvence. Zda konkrétní objednané paralelní operace je rychlejší než sekvenční verze operace závisí na mnoha faktorech.

Následující příklad kódu ukazuje, jak se přihlásit k uchování objednávek.

[!code-csharp[PLINQ#3](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#3)]
[!code-vb[PLINQ#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#3)]

Další informace naleznete [v tématu Order Preservation in PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).

## <a name="parallel-vs-sequential-queries"></a>Paralelní a sekvenční dotazy

Některé operace vyžadují, aby zdrojová data byla doručována sekvenčním způsobem. Operátory <xref:System.Linq.ParallelEnumerable> dotazů se automaticky vrátí do sekvenčního režimu, když je to požadováno. Pro uživatelem definované operátory dotazů a delegáty uživatelů, které vyžadují sekvenční provádění, plinq poskytuje metodu. <xref:System.Linq.ParallelEnumerable.AsSequential%2A> Při použití <xref:System.Linq.ParallelEnumerable.AsSequential%2A>jsou všechny následné operátory v dotazu spouštěny postupně, dokud <xref:System.Linq.ParallelEnumerable.AsParallel%2A> není znovu volána. Další informace naleznete v [tématu Postup: Kombinování paralelních a sekvenčních dotazů LINQ](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md).

## <a name="options-for-merging-query-results"></a>Možnosti pro sloučení výsledků dotazu

Při spuštění dotazu PLINQ paralelně, jeho výsledky z každého pracovního vlákna musí `foreach` být`For Each` sloučeny zpět do hlavního vlákna pro spotřebu smyčkou (v jazyce Visual Basic) nebo vložením do seznamu nebo pole. V některých případech může být užitečné určit určitý druh operace sloučení, například začít vytvářet výsledky rychleji. Pro tento účel PLINQ <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> podporuje metodu <xref:System.Linq.ParallelMergeOptions> a výčet. Další informace naleznete [v tématu Merge Options in PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).

## <a name="the-forall-operator"></a>Operátor Forall

V sekvenčních dotazech LINQ je spuštění odloženo, `foreach` dokud`For Each` není dotaz uveden ve smyčce ( v <xref:System.Linq.ParallelEnumerable.ToList%2A> <xref:System.Linq.ParallelEnumerable.ToArray%2A> jazyce <xref:System.Linq.ParallelEnumerable.ToDictionary%2A>Visual Basic nebo vyvoláním metody, například , , nebo . V PLINQ můžete také `foreach` použít ke spuštění dotazu a iterovat prostřednictvím výsledků. Sama `foreach` o sobě však neběží paralelně, a proto vyžaduje, aby výstup ze všech paralelních úloh být sloučeny zpět do vlákna, na kterém je spuštěna smyčka. V PLINQ můžete `foreach` použít, když je nutné zachovat konečné pořadí výsledků dotazu a také vždy, když zpracováváte `Console.WriteLine` výsledky sériovým způsobem, například při volání pro každý prvek. Pro rychlejší spuštění dotazu při zachování objednávky není vyžadováno a při <xref:System.Linq.ParallelEnumerable.ForAll%2A> samotném zpracování výsledků použijte metodu ke spuštění dotazu PLINQ. <xref:System.Linq.ParallelEnumerable.ForAll%2A>neprovede tento poslední krok sloučení. Následující příklad kódu ukazuje, <xref:System.Linq.ParallelEnumerable.ForAll%2A> jak použít metodu. <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>používá se zde, protože je optimalizován pro více vláken přidání současně bez pokusu o odebrání všech položek.

[!code-csharp[PLINQ#4](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#4)]
[!code-vb[PLINQ#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#4)]

Následující obrázek znázorňuje rozdíl mezi `foreach` a <xref:System.Linq.ParallelEnumerable.ForAll%2A> s ohledem na provádění dotazu.

![ForAll vs ForEach](../../../docs/standard/parallel-programming/media/vs-isvnt-allvseach.png "VS_ISVNT_ALLvsEACH")

## <a name="cancellation"></a>Zrušení

PLINQ je integrován s typy zrušení v rozhraní .NET Framework 4. (Další informace naleznete [v tématu Zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md).) Proto na rozdíl od sekvenční LINQ na objekty dotazy PLINQ dotazy mohou být zrušeny. Chcete-li vytvořit zrušitelný dotaz PLINQ, použijte <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> operátor <xref:System.Threading.CancellationToken> na dotazu a zadejte instanci jako argument. Když <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> je vlastnost na tokenu nastavena na hodnotu true, PLINQ si <xref:System.OperationCanceledException>toho všimne, zastaví zpracování ve všech vláknech a vyvolá .

Je možné, že dotaz PLINQ může pokračovat ve zpracování některých prvků po nastavení tokenu zrušení.

Pro větší odezvu můžete také reagovat na požadavky na zrušení v dlouho běžících uživatelských delegátech. Další informace naleznete v [tématu Jak zrušit dotaz PLINQ](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md).

## <a name="exceptions"></a>Výjimky

Při spuštění dotazu PLINQ, může být vyvoláno více výjimek z různých vláken současně. Také kód pro zpracování výjimky může být v jiném vlákně než kód, který vyvolal výjimku. PLINQ používá <xref:System.AggregateException> typ zapouzdřit všechny výjimky, které byly vyvolány dotazem a zařazování těchto výjimek zpět do volajícího vlákna. Ve volajícím vlákně je vyžadován pouze jeden blok try-catch. Můžete však iterate prostřednictvím všech výjimek, které jsou <xref:System.AggregateException> zapouzdřeny v a zachytit všechny, které můžete bezpečně obnovit z. Ve výjimečných případech mohou být vyvolány některé výjimky, které nejsou zabaleny v <xref:System.AggregateException>, a <xref:System.Threading.ThreadAbortException>s také nejsou zabaleny.

Pokud jsou povoleny výjimky bubliny zpět do spojovacího vlákna, pak je možné, že dotaz může pokračovat ve zpracování některých položek po vyvolání výjimky.

Další informace naleznete v [tématu How to: Handle Exceptions in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md).

## <a name="custom-partitioners"></a>Vlastní šmeječky

V některých případech můžete zlepšit výkon dotazu napsáním vlastní rozdělovač, který využívá některé charakteristiky zdrojových dat. V dotazu vlastní partitioner sám je výčet objektu, který je dotazován.

[!code-csharp[PLINQ#2](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#2)]
[!code-vb[PLINQ#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq3.vb#2)]

PLINQ podporuje pevný počet oddílů (i když data mohou být dynamicky přeřazeny k těmto oddílům za běhu pro vyrovnávání zatížení.). <xref:System.Threading.Tasks.Parallel.For%2A>a <xref:System.Threading.Tasks.Parallel.ForEach%2A> podporují pouze dynamické dělení, což znamená, že počet oddílů se mění za běhu. Další informace naleznete [v tématu Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).

## <a name="measuring-plinq-performance"></a>Měření výkonu PLINQ

V mnoha případech může být dotaz paralelizován, ale režie nastavení paralelního dotazu převažuje nad získanou výhodou výkonu. Pokud dotaz neprovádí mnoho výpočtů nebo pokud je malý zdroj dat, může být dotaz PLINQ pomalejší než sekvenční dotaz LINQ to Objects. Paralelní analyzátor výkonu v aplikaci Visual Studio Team Server můžete použít k porovnání výkonu různých dotazů, k vyhledání kritických míst zpracování a k určení, zda je dotaz spuštěn paralelně nebo postupně. Další informace naleznete v [tématu Vizualizér souběžnosti](/visualstudio/profiling/concurrency-visualizer) a [postup: Měření výkonu dotazu PLINQ](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).

## <a name="see-also"></a>Viz také

- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)
