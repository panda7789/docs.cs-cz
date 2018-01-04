---
title: "Úvod do PLINQ"
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
helpviewer_keywords: PLINQ queries, introduction to
ms.assetid: eaa720d8-8999-4eb7-8df5-3c19ca61cad0
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d14f82fa73400695faad49f010e6ef52a14dd9e3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="introduction-to-plinq"></a>Úvod do PLINQ
## <a name="what-is-a-parallel-query"></a>Co je paralelní dotaz?  
 Language-Integrated Query (LINQ) byla zavedená v [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)].  Jeho součástí jsou jednotný model pro dotazování žádné <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> zdroj dat způsobem bezpečnost typů. LINQ na objekty je název pro LINQ dotazů, které jsou spouštěny proti kolekci v paměti, jako například <xref:System.Collections.Generic.List%601> a pole. Tento článek předpokládá, že máte základní znalosti o LINQ. Další informace najdete v tématu [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).  
  
 Paralelní LINQ (PLINQ) je paralelní provádění vzoru LINQ. PLINQ dotazu v mnoha směrech se podobá nejsou rovnoběžné dotazu LINQ to objekty. Dotazy PLINQ, stejně jako sekvenční [!INCLUDE[vbteclinq](../../../includes/vbteclinq-md.md)] dotazy, pracují na všech paměťových <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601> datového zdroje a mají odložené spouštění, což znamená, se nespustí dříve než dotaz zpracován. Základní rozdíl je, že PLINQ pokusí plně využívat všechny procesory systému. Dělá to pomocí vytváření oddílů zdroje dat do segmentů a spouštění dotazu v každém segmentu na samostatné pracovních vláken paralelně na více procesorů. V mnoha případech paralelní provádění znamená, že spuštění dotazu výrazně rychlejší.  
  
 Prostřednictvím paralelní provádění PLINQ může dosáhnout výrazné vylepšení výkonu než starší kód pro určité typy dotazů, často pouze přidáním <xref:System.Linq.ParallelEnumerable.AsParallel%2A> operace ke zdroji dat dotazů. Ale paralelismus můžete zavádět vlastní složitosti a ne všechny operace dotazů běží rychleji v PLINQ. Ve skutečnosti paralelizace může zpomalit některé dotazy. Proto byste měli porozumět, jak například třídění ovlivní paralelní dotazy. Další informace najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
> [!NOTE]
>  Tato dokumentace používá k definování delegátů v PLINQ výrazy lambda. Pokud nejste obeznámeni s výrazy lambda v jazyce C# nebo Visual Basic, přečtěte si téma [výrazy Lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 Zbývající část tohoto článku bude stručně charakterizovat hlavní třídy PLINQ a popisuje, jak vytvořit dotazy PLINQ. Každá část obsahuje odkazy na podrobnější informace a ukázky kódu.  
  
## <a name="the-parallelenumerable-class"></a>Třída ParallelEnumerable  
 <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> Třída zpřístupňuje téměř všechny funkce PLINQ.  To a zbytek <xref:System.Linq?displayProperty=nameWithType> obor názvů je kompilovány do sestavení System.Core.dll. Výchozí projektů C# a Visual Basic v sadě Visual Studio referenční sestavení a importovat obor názvů.  
  
 <xref:System.Linq.ParallelEnumerable>zahrnuje implementace všechny operátory standardní dotazu, které podporuje LINQ na objekty, i když se nepokusí učinit paralelní každé z nich. Pokud nejste obeznámeni s [!INCLUDE[vbteclinq](../../../includes/vbteclinq-md.md)], najdete v části [Úvod do LINQ](http://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e).  
  
 Kromě standardní operátory dotazu <xref:System.Linq.ParallelEnumerable> třída obsahuje sadu metody, které umožňují specifické chování pro paralelní zpracování. Tyto metody specifické pro PLINQ jsou uvedeny v následující tabulce.  
  
|Operátor ParallelEnumerable|Popis|  
|---------------------------------|-----------------|  
|<xref:System.Linq.ParallelEnumerable.AsParallel%2A>|Vstupní bod pro PLINQ. Určuje, že by měl být paralelizovaná několika málo zbytkem dotazu, pokud je to možné.|  
|<xref:System.Linq.ParallelEnumerable.AsSequential%2A>|Určuje, že zbývajícím částem dotazu by měl být spuštěn postupně, jako jiný paralelní dotaz LINQ.|  
|<xref:System.Linq.ParallelEnumerable.AsOrdered%2A>|Určuje, že by měl PLINQ zachování pořadí zdrojové sekvence pro zbývající dotazu, nebo dokud řazení se nezmění, například pomocí klauzule orderby (Order by Vlsual Basic).|  
|<xref:System.Linq.ParallelEnumerable.AsUnordered%2A>|Určuje, že PLINQ pro zbytek dotaz není potřeba zachovat řazení zdrojové sekvence.|  
|<xref:System.Linq.ParallelEnumerable.WithCancellation%2A>|Určuje, že by měl PLINQ pravidelně sledovat stav token poskytnutý zrušení a zrušit provádění, pokud se vyžaduje.|  
|<xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A>|Určuje maximální počet procesorů, které by měl PLINQ používat učinit paralelní dotaz.|  
|<xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A>|Poskytuje informace o tom, jak by měl PLINQ, pokud je to možné, sloučit paralelní výsledky do jediné sekvence spotřebitelské vlákno.|  
|<xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A>|Určuje, zda by měl PLINQ paralelní dotaz i v případě, že by mohla být výchozí chování spouští sekvenčně.|  
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Vícevláknové výčtu metoda umožňující, na rozdíl od iterování přes výsledky dotazu, výsledky mají být zpracovány současně bez předchozího sloučení zpět k příjemce vlákno.|  
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A>přetížení|Přetížení, které jsou jedinečné pro PLINQ a umožňuje přechodnou agregaci přes místní oddíly plus finální agregační funkce, která se kombinují výsledky všech oddílů.|  
  
## <a name="the-opt-in-model"></a>Model přidání  
 Při psaní dotazu vyjádřit výslovný souhlas pro PLINQ vyvoláním <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> rozšiřující metody na zdroji dat, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[PLINQ#1](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#1)]
 [!code-vb[PLINQ#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#1)]  
  
 <xref:System.Linq.ParallelEnumerable.AsParallel%2A> Metoda rozšíření váže operátory pro následné dotazování, v takovém případě `where` a `select`do <xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType> implementace.  
  
## <a name="execution-modes"></a>Režim spuštění  
 Ve výchozím nastavení je PLINQ konzervativní. V době běhu PLINQ infrastruktura analyzuje celková struktura dotazu. Pokud je dotaz pravděpodobně paralelizací podle paralelizace, oddíly PLINQ zdrojové sekvence do úlohy, které můžou běžet souběžně. Pokud není bezpečné učinit paralelní dotaz, PLINQ právě spouští dotaz postupně. Pokud PLINQ volba mezi potenciálně nákladné paralelní algoritmus nebo nenákladné sekvenční algoritmus, zvolí sekvenční algoritmus ve výchozím nastavení. Můžete použít <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> metoda a <xref:System.Linq.ParallelExecutionMode?displayProperty=nameWithType> výčet k vynucení PLINQ paralelního algoritmu. To je užitečné, když víte, testování a měření, která konkrétní dotaz rychleji spustí paralelně. Další informace najdete v tématu [postupy: určení režimu spouštění v PLINQ](../../../docs/standard/parallel-programming/how-to-specify-the-execution-mode-in-plinq.md).  
  
## <a name="degree-of-parallelism"></a>Stupně paralelního zpracování  
 Ve výchozím nastavení PLINQ používá všech procesorů v hostitelském počítači. Můžete určit, aby PLINQ používat více než zadaný počet procesorů pomocí <xref:System.Linq.ParallelEnumerable.WithDegreeOfParallelism%2A> metoda. To je užitečné, pokud chcete zajistit, aby ostatní procesy spuštěné v počítači přijímat množství času procesoru. Následující fragment kódu omezuje dotaz k použití maximálně dva procesory.  
  
 [!code-csharp[PLINQ#5](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#5)]
 [!code-vb[PLINQ#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#5)]  
  
 V případech, kde dotaz provádí významné množství výpočetních hranice pracovní například soubor vstupně-výstupních operací může být užitečné k určení stupně paralelního zpracování větší než počet jader na počítači.  
  
## <a name="ordered-versus-unordered-parallel-queries"></a>Seřazené a neuspořádané paralelní dotazy  
 U některých dotazů musí operátor dotazu nepřineslo výsledky, které zachovat řazení zdrojové sekvence. Poskytuje PLINQ <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operátor pro tento účel. <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>se liší od <xref:System.Linq.ParallelEnumerable.AsSequential%2A>. <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> Pořadí je stále zpracovávají paralelně, ale jeho výsledky jsou uložená do vyrovnávací paměti a seřazeny. Protože zachování pořadí obvykle zahrnuje další práci <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> pořadí může být zpracována pomaleji než výchozí <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> pořadí. Zda speciální paralelní operace řazení je rychlejší než verze sekvenční operace závisí na mnoha faktorech.  
  
 Následující příklad kódu ukazuje, jak se vyjádřit výslovný souhlas pro zachování pořadí.  
  
 [!code-csharp[PLINQ#3](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#3)]
 [!code-vb[PLINQ#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#3)]  
  
 Další informace najdete v tématu [zachování pořadí v PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).  
  
## <a name="parallel-vs-sequential-queries"></a>Paralelní vs. Sekvenční dotazy  
 Některé operace vyžadují doručení zdrojová data sekvenční způsobem. <xref:System.Linq.ParallelEnumerable> Dotazu operátory vrátí do sekvenčního režimu automaticky pokud je to požadováno. Pro dotaz uživatelem definované operátory a delegáti uživatele, které vyžadují sekvenční provádění, poskytuje PLINQ <xref:System.Linq.ParallelEnumerable.AsSequential%2A> metoda. Při použití <xref:System.Linq.ParallelEnumerable.AsSequential%2A>, všechny následné operátory v dotazu se postupně, dokud <xref:System.Linq.ParallelEnumerable.AsParallel%2A> nebude volán znovu. Další informace najdete v tématu [postupy: Kombinování paralelních a sekvenčních LINQ dotazů](../../../docs/standard/parallel-programming/how-to-combine-parallel-and-sequential-linq-queries.md).  
  
## <a name="options-for-merging-query-results"></a>Možnosti sloučení výsledky dotazu  
 Když PLINQ dotazu se provede paralelně, je potřeba sloučit své výsledky z každé pracovní vlákno zpět do hlavní vlákno pro spotřeba `foreach` smyčky (`For Each` v [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), nebo pro vložení do seznamu nebo pole. V některých případech může být výhodné, zadejte konkrétní typ operace sloučení, například, při zahájení výroby výsledku rychleji. Pro tento účel PLINQ podporuje <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> metody a <xref:System.Linq.ParallelMergeOptions> výčtu. Další informace najdete v tématu [možnosti sloučení v PLINQ](../../../docs/standard/parallel-programming/merge-options-in-plinq.md).  
  
## <a name="the-forall-operator"></a>Operátor ForAll  
 V sekvenčních [!INCLUDE[vbteclinq](../../../includes/vbteclinq-md.md)] dotazy, spuštění je odložení, dokud není dotaz zpracován buď v `foreach` (`For Each` v [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) cykly nebo podle vyvoláním metody <xref:System.Linq.ParallelEnumerable.ToList%2A> , <xref:System.Linq.ParallelEnumerable.ToArray%2A> , nebo <xref:System.Linq.ParallelEnumerable.ToDictionary%2A>. V PLINQ, můžete také použít `foreach` iteraci v rámci výsledky a provést dotaz. Ale `foreach` samotné nespustí paralelně, a proto vyžaduje, aby výstup z paralelní úlohy slučované zpět do vlákna, na kterém je spuštěn smyčky. V PLINQ, můžete použít `foreach` při musí zachovat konečné řazení výsledků dotazu, a také vždy, když zpracováváte výsledky sériovým způsobem, například když voláte `Console.WriteLine` pro jednotlivé elementy. Pro rychlejší provádění dotazu není zachováváno pořadí a při zpracování výsledků, které může být paralelizováno, použijte <xref:System.Linq.ParallelEnumerable.ForAll%2A> metodu za účelem provedení PLINQ dotazu. <xref:System.Linq.ParallelEnumerable.ForAll%2A>neprovede krok finálního sloučení. Následující příklad kódu ukazuje, jak používat <xref:System.Linq.ParallelEnumerable.ForAll%2A> metoda. <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>je zde použít, protože je optimalizovaný pro více vláken současně přidání bez pokusu o odebrání všech položek.  
  
 [!code-csharp[PLINQ#4](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#4)]
 [!code-vb[PLINQ#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#4)]  
  
 Následující obrázek ukazuje rozdíl mezi `foreach` a <xref:System.Linq.ParallelEnumerable.ForAll%2A> s ohledem na spuštění dotazu.  
  
 ![ForAll vs. ForEach](../../../docs/standard/parallel-programming/media/vs-isvnt-allvseach.png "VS_ISVNT_ALLvsEACH")  
  
## <a name="cancellation"></a>Zrušení  
 PLINQ je integrována s typy zrušení v [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. (Další informace najdete v tématu [zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md).) Proto na rozdíl od sekvenčních LINQ na objekty dotazy, dotazy PLINQ můžete zrušit. Pokud chcete vytvořit PLINQ dotaz, použít <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> operátor na dotaz a zadejte <xref:System.Threading.CancellationToken> instance jako argument. Když <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> na tokenu je nastavena na hodnotu true, PLINQ Všimněte si ho, zastaví zpracování na všechna vlákna a throw <xref:System.OperationCanceledException>.  
  
 Je možné, že dotazu PLINQ může pokračovat ve zpracování některých prvků po nastavení tokenu zrušení.  
  
 Pro větší rychlost reakce můžete také reagovat na požadavky zrušení v delegátech dlouho běžící uživatele. Další informace najdete v tématu [postupy: zrušení dotazu PLINQ](../../../docs/standard/parallel-programming/how-to-cancel-a-plinq-query.md).  
  
## <a name="exceptions"></a>Výjimky  
 Když PLINQ dotazu se provede, může být více výjimky vyvolány z různých vláknech současně. Kód pro zpracování výjimky může být v jiném podprocesu než kód, který způsobil výjimku. PLINQ používá <xref:System.AggregateException> typ zapouzdření všechny výjimky, které byly vyvolány v dotazu a zařazení těchto výjimek zpět volající vlákno. Volající vlákno je vyžadována pouze jeden blok try-catch. Však můžete iterovat všechny výjimky, které jsou zapouzdřené v <xref:System.AggregateException> a všechny, které můžete bezpečně zotavit catch. Ve výjimečných případech některé výjimky může vyvolat, které nejsou zabalené v <xref:System.AggregateException>, a <xref:System.Threading.ThreadAbortException>s také není zabalena.  
  
 Pokud je výjimky umožněno vyvolat zpět do spojovacího vlákna, je možné, že dotaz může pokračovat ve zpracování některé položky po je vyvolána výjimka.  
  
 Další informace najdete v tématu [postupy: zpracování výjimek v PLINQ dotazu](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md).  
  
## <a name="custom-partitioners"></a>Vlastní dělicí metody  
 V některých případech může zlepšit výkon dotazu napsáním vlastní dělicí metody, který využívá některé typické vlastnosti zdrojová data. V dotazu je vlastní rozdělovač sám vyčíslitelný objekt, který je dotazován.  
  
 [!code-csharp[PLINQ#2](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinq2_cs.cs#2)]
 [!code-vb[PLINQ#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq3.vb#2)]  
  
 PLINQ podporuje pevný počet oddílů (i když se data mohou být dynamicky přeřazena do těchto oddílů při běhu pro vyrovnávání zatížení.). <xref:System.Threading.Tasks.Parallel.For%2A>a <xref:System.Threading.Tasks.Parallel.ForEach%2A> podporují pouze dynamické rozdělení, to znamená, že počet oddílů se mění v době běhu. Další informace najdete v tématu [vlastní dělicí metody pro PLINQ a TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="measuring-plinq-performance"></a>Měření výkonu PLINQ  
 V mnoha případech může být paralelizovaná málo dotazu, ale režie nastavení paralelního dotazu převáží získané výhody výkonu. Pokud dotaz neprovádí mnoho výpočtu nebo zdroj dat je malý, může být pomalejší než sekvenčních LINQ na objekty dotazu PLINQ dotazu. Paralelní Analyzátor výkonu v sadě Visual Studio Team Server můžete použít k porovnání výkonu různé dotazy, zjistit kritická místa zpracování a k určení, zda dotaz běží paralelně nebo postupně. Další informace najdete v tématu [vizualizér souběžnosti](/visualstudio/profiling/concurrency-visualizer) a [postupy: měření výkonu dotazu PLINQ](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).  
  
## <a name="see-also"></a>Viz také  
 [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)
