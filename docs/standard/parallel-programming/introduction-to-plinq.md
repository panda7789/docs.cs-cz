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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a1cf3ea782752f750f3545a28699a8bc325e4a5
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2019
ms.locfileid: "55903888"
---
# <a name="introduction-to-plinq"></a>Úvod do PLINQ
## <a name="what-is-a-parallel-query"></a>Co je paralelní dotaz?  
 Language Integrated Query (LINQ) byl zaveden v [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)].  Nabízí jednotný model pro dotazování libovolného <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> zdroj dat v podobě typově bezpečné. LINQ to Objects je název pro LINQ dotazy, které jsou spouštěny proti kolekci v paměť, jako <xref:System.Collections.Generic.List%601> a pole. Tento článek předpokládá, že máte základní znalosti o LINQ. Další informace najdete v tématu [Language-Integrated Query (LINQ) - C# ](../../csharp/programming-guide/concepts/linq/index.md) nebo [Language-Integrated Query (LINQ) - jazyka Visual Basic](../../visual-basic/programming-guide/concepts/linq/index.md).  
  
 Paralelní LINQ (PLINQ) je implementace LINQ vzoru. PLINQ dotaz ve spoustě ohledů podobá neparalelní LINQ to Objects dotazům. PLINQ dotazy, stejně jako sekvenční [!INCLUDE[vbteclinq](../../../includes/vbteclinq-md.md)] dotazy, pracují na všech paměťových <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601> datového zdroje a mají odložené spouštění, což znamená, že nezačíná dříve, než je vypočten dotaz. Hlavní rozdíl je, že PLINQ se pokouší plně využívat všechny procesory systému. Toto je realizováno rozdělením zdrojových dat do segmentů a spouštěním dotazu na všech segmentech v samostatných pracovních vláknech na více procesorů. V mnoha případech paralelní provádění znamená, že spuštění dotazu výrazně rychlejší.  
  
 Prostřednictvím paralelního spuštění, PLINQ může dosáhnout výrazné zlepšení výkonu než starší verzi kódu pro některé typy dotazů, často pouze přidáním <xref:System.Linq.ParallelEnumerable.AsParallel%2A> dotazové operace do zdroje dat. Ale paralelismu může zavádět vlastní složitosti a ne všechny dotazové operace běží rychleji v PLINQ. Ve skutečnosti paralelizace může zpomalit některé dotazy. Proto byste měli rozumět, jak například třídění ovlivní paralelní dotazy. Další informace najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
> [!NOTE]
>  Tato dokumentace používá lambda výrazy k definování delegátů v PLINQ. Pokud nejste obeznámeni s lambda výrazy v jazyce C# nebo Visual Basic, přečtěte si téma [výrazy Lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 Zbývající část tohoto článku poskytuje přehled o hlavních třídách PLINQ a popisuje, jak vytvořit dotazy v PLINQ. Každý oddíl obsahuje odkazy na podrobnější informace a praktické příklady.  
  
## <a name="the-parallelenumerable-class"></a>Třída ParallelEnumerable  
 <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> Třídy zpřístupňuje téměř všechny funkce PLINQ.  A zbytek <xref:System.Linq?displayProperty=nameWithType> obor názvů typů jsou kompilovány do sestavení System.Core.dll. Výchozí projekty jazyka C# a Visual Basic v sadě Visual Studio odkazují na toto sestavení a importují obor názvů.  
  
 <xref:System.Linq.ParallelEnumerable> zahrnuje implementaci všech standardních operátorů pro dotazování, které podporují LINQ to Objects, přestože se nepokouší paralelizovat každé z nich. Pokud nejste obeznámeni s [!INCLUDE[vbteclinq](../../../includes/vbteclinq-md.md)], naleznete v tématu [Úvod do LINQ](https://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e).  
  
 Kromě standardních operátorů pro dotazování <xref:System.Linq.ParallelEnumerable> třída obsahuje sadu metod, které umožňují specifické chování pro paralelní zpracování. Tyto metody specifické pro PLINQ jsou uvedeny v následující tabulce.  
  
|Operátor ParallelEnumerable|Popis|  
|---------------------------------|-----------------|  
|<xref:System.Linq.ParallelEnumerable.AsParallel%2A>|Vstupní bod pro PLINQ. Určuje, že by měla být paralelizována zbývající části dotazu, pokud je to možné.|  
|<xref:System.Linq.ParallelEnumerable.AsSequential%2A>|Určuje, zda zbývající část dotazu má být spuštěna sekvenčně, jako neparalelní LINQ dotaz.|  
|<xref:System.Linq.ParallelEnumerable.AsOrdered%2A>|Určuje, zda by PLINQ mělo zachovat řazení zdrojové sekvence pro zbytek dotazu nebo dokud není řazení změněno, například pomocí klauzule orderby (Order By Vlsual Basic).|  
|<xref:System.Linq.ParallelEnumerable.AsUnordered%2A>|Určuje, že PLINQ pro zbývající části dotazu vyžadovat zachovávaní řazení zdrojové sekvence.|  
|<xref:System.Linq.ParallelEnumerable.WithCancellation%2A>|Určuje, že by měl PLINQ pravidelně sledovat stav poskytnutého rušícího tokenu a zrušit spouštění, pokud je požadováno.|  
|<xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A>|Určuje maximální počet procesorů, které by měl PLINQ používat pro paralelizaci dotazů.|  
|<xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A>|Poskytuje informace o tom, jak by měl PLINQ, pokud je to možné, sloučit paralelní výsledek zpět do jediné sekvence v konzumním vlákně.|  
|<xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A>|Určuje, zda by měl PLINQ paralelizovat dotaz i v případě, že je výchozí chování spouští sekvenčně.|  
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Vícevláknová enumerační metoda, která na rozdíl od iterování celého výsledku dotazu umožňuje paralelní zpracování výsledku bez předchozího sloučení zpět do konzumního vlákna.|  
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A> přetížení|Přetížení, které jsou jedinečné pro PLINQ, umožňuje přechodnou agregaci přes lokální oddíly vlákna, plus finální agregační funkce k vytvoření výsledku pro všechny oddíly.|  
  
## <a name="the-opt-in-model"></a>Model přidání  
 Při psaní dotazu zvolíte předání do PLINQ vyvoláním <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> rozšiřující metody na zdroj dat, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[PLINQ#1](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#1)]
 [!code-vb[PLINQ#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#1)]  
  
 <xref:System.Linq.ParallelEnumerable.AsParallel%2A> – Metoda rozšíření váže následující operátory pro dotazování, v tomto případě `where` a `select`, možnosti <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> implementace.  
  
## <a name="execution-modes"></a>Režimy spuštění  
 Ve výchozím nastavení je PLINQ konzervativní. V době spuštění PLINQ infrastruktura analyzuje celkovou strukturu dotazu. Pokud je dotaz pravděpodobně zrychlen paralelizací, pak PLINQ rozdělí zdrojovou sekvenci na úlohy, které můžou běžet souběžně. Pokud není bezpečné paralelizovat dotaz, PLINQ spustí dotaz pouze postupně. Pokud se PLINQ rozhoduje mezi potencionálně nákladným paralelním algoritmem nebo levným sekvenčním algoritmem, zvolí ve výchozím nastavení sekvenční algoritmus. Můžete použít <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> metoda a <xref:System.Linq.ParallelExecutionMode?displayProperty=nameWithType> výčet k vynucení PLINQ paralelního algoritmu. To je užitečné, když víte, testování a měření, které speciální dotaz je vyhodnocen rychleji paralelně. Další informace najdete v tématu [jak: Určení režimu spouštění v PLINQ](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md).  
  
## <a name="degree-of-parallelism"></a>Stupeň paralelismu  
 Ve výchozím nastavení PLINQ používá všechny procesory v hostitelském počítači. Můžete dát pokyn, aby PLINQ používal maximálně určený počet procesorů pomocí <xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A> metody. To je užitečné, pokud chcete, abyste měli jistotu, že ostatní procesy spuštěné v počítači dostanou množství času procesoru. Následující úryvek omezuje dotaz k použití maximálně dvou procesorů.  
  
 [!code-csharp[PLINQ#5](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#5)]
 [!code-vb[PLINQ#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#5)]  
  
 V případech, kde dotaz vykonává značné množství práce bez výpočetní vazby například vstup a výstup souborů může být výhodnější zadat úhel paralelizace větší než počet jader v počítači.  
  
## <a name="ordered-versus-unordered-parallel-queries"></a>Uspořádané a neuspořádané paralelní dotazy  
 V některých dotazech – operátor dotazu pro dotazovaní musí předložit výsledky, které zachovávají řazení zdrojová sekvence. PLINQ poskytuje <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> pro tento účel operátor. <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> se liší od <xref:System.Linq.ParallelEnumerable.AsSequential%2A>. <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> Pořadí je stále zpracovávána paralelně, ale její výsledky jsou ukládány do vyrovnávací paměti a seřazeny. Protože zachování pořadí obvykle zahrnuje další práci <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> pořadí může být zpracována pomaleji než výchozí <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> pořadí. Zda je speciální paralelní operace řazení rychlejší než její sekvenční verze operace závislá na mnoha faktorech.  
  
 Následující příklad kódu ukazuje, jak přidat možnosti do zachování pořadí.  
  
 [!code-csharp[PLINQ#3](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#3)]
 [!code-vb[PLINQ#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#3)]  
  
 Další informace najdete v tématu [zachování pořadí v PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).  
  
## <a name="parallel-vs-sequential-queries"></a>Paralelní vs. Sekvenční dotazy  
 Některé operace vyžadují doručení zdrojových dat sekvenčním způsobem. <xref:System.Linq.ParallelEnumerable> Dotazů, operátory vrátí do sekvenčního režimu automaticky pokud je to požadováno. Uživateli definované operátory pro dotazování a uživatelské delegáty, které vyžadují sekvenční provádění, poskytuje PLINQ <xref:System.Linq.ParallelEnumerable.AsSequential%2A> metody. Při použití <xref:System.Linq.ParallelEnumerable.AsSequential%2A>, všechny následující operátory v dotazu jsou prováděny postupně až do <xref:System.Linq.ParallelEnumerable.AsParallel%2A> volána znovu. Další informace najdete v tématu [jak: Kombinování paralelních a sekvenčních LINQ dotazů](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md).  
  
## <a name="options-for-merging-query-results"></a>Možnosti pro slučování výsledků dotazů  
 Když je PLINQ dotaz spuštěn paralelně, jeho výsledky z každého pracovního vlákna musí být sloučeny zpět do hlavního vlákna pro spotřebu `foreach` smyčky (`For Each` v jazyce Visual Basic), nebo pro vložení do seznamu nebo pole. V některých případech může být výhodné například určit konkrétní druh operace sloučení, k zahájení výroby výsledku rychleji. Za tímto účelem podporuje PLINQ <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> metody a <xref:System.Linq.ParallelMergeOptions> výčtu. Další informace najdete v tématu [možnosti sloučení v PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
## <a name="the-forall-operator"></a>Operátor ForAll  
 V sekvenčních [!INCLUDE[vbteclinq](../../../includes/vbteclinq-md.md)] dotazy, provádění je odloženo, dokud je vypočten dotaz buď `foreach` (`For Each` v jazyce Visual Basic) smyčce nebo podle vyvoláním metody <xref:System.Linq.ParallelEnumerable.ToList%2A> , <xref:System.Linq.ParallelEnumerable.ToArray%2A> , nebo <xref:System.Linq.ParallelEnumerable.ToDictionary%2A>. V PLINQ můžete také použít `foreach` k provedení dotazu a iterování přes výsledky. Ale `foreach` samotný není spouštěn paralelně a proto se vyžaduje, aby výstupy z paralelní úlohy být sloučeny zpět do vlákna, na kterém je spuštěna smyčka. V PLINQ můžete použít `foreach` když musíte zachovat konečné řazení výsledku dotazu, a také pokaždé, když zpracováváte výsledky sériovým způsobem, například když voláte `Console.WriteLine` pro každý prvek. Pro rychlejší provádění dotazu, kde není zachováváno pořadí a při zpracování výsledků, které může být paralelizováno, použijte <xref:System.Linq.ParallelEnumerable.ForAll%2A> metody k provedení PLINQ dotazu. <xref:System.Linq.ParallelEnumerable.ForAll%2A> neprovádí krok finálního sloučení. Následující příklad kódu ukazuje, jak používat <xref:System.Linq.ParallelEnumerable.ForAll%2A> metody. <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> je zde použita, protože je optimalizována pro více vláken přidávajících souběžně položky bez pokusu o odebrání nějakých položek.  
  
 [!code-csharp[PLINQ#4](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#4)]
 [!code-vb[PLINQ#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#4)]  
  
 Následující obrázek ukazuje rozdíl mezi `foreach` a <xref:System.Linq.ParallelEnumerable.ForAll%2A> jde o provedení dotazu.  
  
 ![ForAll vs. ForEach](../../../docs/standard/parallel-programming/media/vs-isvnt-allvseach.png "VS_ISVNT_ALLvsEACH")  
  
## <a name="cancellation"></a>Zrušení  
 PLINQ je integrována s typy zrušení v [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. (Další informace najdete v tématu [zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md).) Proto se na rozdíl od sekvenčních LINQ to Objects dotazů, dotazy PLINQ můžete zrušit. Chcete-li vytvořit PLINQ dotaz, použijte <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> operátor v dotazu a zadejte <xref:System.Threading.CancellationToken> instanci jako argument. Když <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> v tokenu je nastavena na hodnotu true, PLINQ bude zpozoruje, zastaví zpracovávání na všech vláknech a vyvolat <xref:System.OperationCanceledException>.  
  
 Je možné, že PLINQ dotaz může pokračovat ve zpracování některých prvků po nastavení tokenu zrušení.  
  
 Pro větší rychlost reakce můžete také odpovídat na požadavky zrušení v dlouhotrvajících uživatelských delegátech. Další informace najdete v tématu [jak: Zrušení dotazu PLINQ](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md).  
  
## <a name="exceptions"></a>Výjimky  
 Při spouštění PLINQ dotazu může být více výjimky vyvolána z různých vláken současně. Kód pro zpracování výjimky může být v jiném vlákně než kód, který vyvolal výjimku. PLINQ používá <xref:System.AggregateException> typ k zapouzdření všech výjimek, které byly vyvolány v dotazu a zařazení těchto výjimek zpět do volajícího vlákna. Na volajícím vlákně je pouze jeden blok try-catch – povinné. Však můžete iterovat přes všechny výjimky, které jsou zapouzdřeny v <xref:System.AggregateException> a zachytit všechny, můžete bezpečně zotavit. Ve výjimečných případech některé výjimky mohou být vyvolány, které nejsou zabaleny v <xref:System.AggregateException>, a <xref:System.Threading.ThreadAbortException>také nejsou zabaleny.  
  
 Pokud je výjimkám umožněn pokračovala zpět do spojovacího vlákna, pak je možné, že dotaz může pokračovat ve zpracování některých položek poté, co je vyvolána výjimka.  
  
 Další informace najdete v tématu [jak: Zpracování výjimek v dotazu PLINQ](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md).  
  
## <a name="custom-partitioners"></a>Vlastní dělicí metody  
 V některých případech můžete zlepšit výkon dotazu napsáním vlastního rozdělovače, který využívá některé typické vlastnosti zdrojových datech. V dotazu je vlastní rozdělovač sám vyčíslitelným objektem, který je dotazován.  
  
 [!code-csharp[PLINQ#2](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#2)]
 [!code-vb[PLINQ#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq3.vb#2)]  
  
 PLINQ podporuje pevný počet oddílů (Ačkoli data mohou být dynamicky přeřazena do těchto oddílů během vyrovnávání zatížení.). <xref:System.Threading.Tasks.Parallel.For%2A> a <xref:System.Threading.Tasks.Parallel.ForEach%2A> podporují pouze dynamické rozdělení, což znamená, že počet oddílů se mění v době běhu. Další informace najdete v tématu [vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="measuring-plinq-performance"></a>Měření výkonu PLINQ  
 V mnoha případech může být dotaz paralelizován, ale režie nastavení paralelního dotaz převažuje získané výhody výkonu. Jestliže dotaz neprovádí mnoho výpočtů nebo zdrojová data jsou malá, PLINQ dotazu může být pomalejší než sekvenční LINQ to Objects dotazům. Můžete použít paralelního Průvodce analýzou výkonu v aplikaci Visual Studio Team Server k porovnání výkonu různých dotazů, k vyhledání problémových místa ve zpracování a na zjištění, zda je dotaz prováděn sekvenčně nebo paralelně. Další informace najdete v tématu [Vizualizátor souběžnosti](/visualstudio/profiling/concurrency-visualizer) a [jak: Měření výkonu dotazu PLINQ](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).  
  
## <a name="see-also"></a>Viz také:

- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)
