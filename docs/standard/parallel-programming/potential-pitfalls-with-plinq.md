---
title: Potenciální nástrahy PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6a316fb7b17a4859fd4e69acf4422c3e4baffc4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478008"
---
# <a name="potential-pitfalls-with-plinq"></a>Potenciální nástrahy PLINQ
V mnoha případech se může poskytnout PLINQ výrazné zlepšení výkonu přes sekvenčních LINQ to Objects dotazů. Paralelní provádění provádění dotazu však zavádí složitost, která může vést k problémům, které v sekvenčním kódu nejsou jako běžné nebo nejsou vůbec došlo k. Toto téma uvádí některé nedoporučované postupy při psaní dotazy PLINQ.  
  
## <a name="do-not-assume-that-parallel-is-always-faster"></a>Nepředpokládejte, že paralelní je vždy rychlejší  
 Někdy paralelizace způsobí, že PLINQ dotaz poběží pomaleji než jeho LINQ na ekvivalentní objekty. Základním pravidlem je, že jsou dotazy, které mají několik zdrojové elementy a rychlé uživatelské delegáty velmi nepravděpodobné, že by zrychlení. Ale vzhledem k tomu výkon ovlivňuje mnoho faktorů, doporučujeme měření skutečné výsledky, než se rozhodnete, jestli se má použít PLINQ. Další informace najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="avoid-writing-to-shared-memory-locations"></a>Vyhněte se zápis do umístění sdílené paměti  
 V sekvenčním kódu není nic neobvyklého, čtení nebo zápis do statické proměnné nebo pole třídy. Pokaždé, když přistupuje více podprocesů tyto proměnné souběžně, existuje však velké objemy potenciální konflikty časování. I když zámky můžete použít k synchronizaci přístupu k proměnné, náklady na synchronizaci může snížit výkon. Proto doporučujeme vám vyhnout, nebo aspoň omezit přístup ke sdílenému stavu v dotazu PLINQ co největší míře.  
  
## <a name="avoid-over-parallelization"></a>Vyhněte se nadbytečnému  
 S použitím `AsParallel` operátoru, se vám účtovat režijní náklady na vytváření oddílů zdrojové kolekce a synchronizace pracovních vláken. Výhody paralelizace jsou dále omezeny počtem procesorů v počítači. Neexistuje žádné zrychlení k získané spuštěním více vláken výpočetní na právě jeden procesor. Proto musí být pozor, abyste nadbytečně dotazu.  
  
 Nejběžnější scénář, ve které nadbytečnému může dojít, je ve vnořené dotazy, jak je znázorněno v následujícím fragmentu kódu.  
  
 [!code-csharp[PLINQ#20](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
 [!code-vb[PLINQ#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]  
  
 V takovém případě je nejlepší paralelizovat pouze na vnější zdroj dat (zákazníci), pokud jedna nebo více z následujících podmínek:  
  
-   Zdroj dat vnitřní (zákazníka. Objednávky) je známo, že trvat velmi dlouho.  
  
-   Provádíte náročné výpočty na jednotlivé objednávky. (Operace je znázorněno v příkladu není nákladné.)  
  
-   Cílový systém jsou známy dostatek procesorů pro zpracování počet vláken, které budou vytvořeny paralelní provádění dotazu na `cust.Orders`.  
  
 Ve všech případech je nejlepší způsob, jak určit optimální tvar dotazu pro testování a měření. Další informace najdete v tématu [jak: Měření výkonu dotazu PLINQ](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).  
  
## <a name="avoid-calls-to-non-thread-safe-methods"></a>Vyhněte se volání metody není bezpečné pro vlákna  
 Zápis do metody instance vláknově bezpečné PLINQ dotazu může vést k poškození dat, který může nebo nemusí pokračovat nezjištěné po ve svém programu. Může také vést k výjimkám. V následujícím příkladu by se pokoušet více vláken k volání `Filestream.Write` metoda současně, což není podporována třídou.  
  
```vb  
Dim fs As FileStream = File.OpenWrite(…)  
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))  
```  
  
```csharp  
FileStream fs = File.OpenWrite(...);  
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));  
```  
  
## <a name="limit-calls-to-thread-safe-methods"></a>Omezení volání metod bezpečným pro vlákno  
 Většina statických metod v rozhraní .NET Framework jsou bezpečné pro vlákna a může být volána z více vláken současně. I v těchto případech se však zapojení synchronizace může vést k výrazné mohou zpomalit zpracování dotazu.  
  
> [!NOTE]
>  Můžete vyzkoušet to sami vložením volání některých <xref:System.Console.WriteLine%2A> v dotazech. I když tato metoda se používá v příkladech dokumentaci pro demonstrační účely, nepoužívejte ji v PLINQ dotazy.  
  
## <a name="avoid-unnecessary-ordering-operations"></a>Vyhněte se zbytečným operace řazení  
 Při PLINQ dotaz spuštěn paralelně, rozdělí zdrojovou sekvenci na oddíly, které mohou být provozována současně z více vláken. Ve výchozím nastavení, není předvídatelný pořadí, ve které se zpracovávají oddíly a jsou doručeny výsledky (s výjimkou operátory, jako například `OrderBy`). Můžete určit, aby PLINQ zachovávaní řazení jakékoli zdrojové sekvence, ale tato akce nemá negativní dopad na výkon. Osvědčeným postupem, kdykoli je to možné, je struktura dotazy tak, aby jejich nespoléhejte na zachování pořadí. Další informace najdete v tématu [zachování pořadí v PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).  
  
## <a name="prefer-forall-to-foreach-when-it-is-possible"></a>V případě ForEach je možné raději ForAll  
 I když PLINQ provede dotaz z více vláken, je-li využívají výsledky v `foreach` smyčky (`For Each` v jazyce Visual Basic), pak výsledky dotazu musí být sloučeny zpět do jednoho vlákna a sériově přistupuje enumerátor. V některých případech je to nevyhnutelné; však kdykoli je to možné, použijte `ForAll` metoda umožňuje každému vláknu vlastní výsledky, například výstup například zapsáním do kolekce bezpečné pro vlákna <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.  
  
 Stejný problém se vztahuje na <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> jinými slovy, `source.AsParallel().Where().ForAll(...)` by měl být důrazně upřednostňován do  
  
 `Parallel.ForEach(source.AsParallel().Where(), ...)`.  
  
## <a name="be-aware-of-thread-affinity-issues"></a>Mějte na paměti problémů, spřažení vláken  
 Některé technologie, například interoperabilita modelů COM pro jedno vláknové objekty Apartment (STA) součásti Windows Forms a Windows Presentation Foundation (WPF), omezení vlákno vztahů, které vyžadují spuštění kódu na konkrétním vlákně. Například ve Windows Forms a WPF, ovládací prvek je přístupný pouze na vlákně, na kterém byla vytvořena. Při pokusu o přístup ke sdílenému stavu ovládacího prvku Windows Forms v PLINQ dotaz, je vyvolána výjimka, pokud používáte v ladicím programu. (Toto nastavení vypnete.) Ale pokud váš dotaz využívá ve vlákně uživatelského rozhraní, pak dostanete ovládacího prvku z `foreach` smyčku, která se zobrazí dotaz výsledky vzhledem k tomu, že kód je prováděn pouze jedno vlákno.  
  
## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>Nepředpokládejte, že iterace ForEach, pro a ForAll vždy spustit paralelně  
 Je důležité mít na paměti, že jednotlivé iterace v <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> nebo <xref:System.Linq.ParallelEnumerable.ForAll%2A> smyčky může, ale není nutné spustit paralelně. Proto byste se měli vyhnout psaní kódu, který správnost závisí na paralelní zpracování iterace nebo spuštění iterace v libovolném pořadí.  
  
 Například tento kód je pravděpodobně dojde k zablokování:  
  
```vb  
Dim mre = New ManualResetEventSlim()  
Enumerable.Range(0, Environment.ProcessorCount * 100).AsParallel().ForAll(Sub(j)   
   If j = Environment.ProcessorCount Then  
       Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)  
       mre.Set()  
   Else  
       Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)  
       mre.Wait()  
   End If  
End Sub) ' deadlocks  
```  
  
```csharp  
ManualResetEventSlim mre = new ManualResetEventSlim();  
Enumerable.Range(0, Environment.ProcessorCount * 100).AsParallel().ForAll((j) =>  
{  
    if (j == Environment.ProcessorCount)  
    {  
        Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);  
        mre.Set();  
    }  
    else  
    {  
        Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);  
        mre.Wait();  
    }  
}); //deadlocks  
```  
  
 V tomto příkladu jednu iteraci nastaví událost a všech dalších iterací čekání na událost. Žádné čekající iterace můžete dokončit až do dokončení iterace nastavení události. Je však možné, že čekajících iterací blokovat všechna vlákna, které se používají ke spouštění paralelní smyčky před událostí iterace dostala příležitost k provedení. Výsledkem zablokování – událost iterace se nikdy neprovede a iterace čekání se nikdy probuzení.  
  
 Zejména jedné iterace paralelní smyčky by nikdy čekat na další iteraci smyčky pokroku. Pokud se rozhodne paralelní smyčky naplánování iterace sekvenčně, ale v opačném pořadí, dojde k zablokování.  
  
## <a name="see-also"></a>Viz také:

- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
