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
ms.openlocfilehash: 73ec2d2fb73ee95b39a15307d136c35542578c41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="potential-pitfalls-with-plinq"></a>Potenciální nástrahy PLINQ
V mnoha případech můžete PLINQ poskytují významné zlepšení výkonu přes sekvenčních LINQ na objekty dotazy. Vytváření paralelních dotazů však zavádí složitost, který může vést k problémům, které v sekvenčních kódu nejsou jako běžné nebo nejsou vůbec došlo. Toto téma uvádí některé postupy, abyste se vyhnuli při psaní PLINQ dotazů.  
  
## <a name="do-not-assume-that-parallel-is-always-faster"></a>Nepředpokládejte, že paralelní, není vždy rychlejší  
 Někdy paralelizace způsobí, že dotazu PLINQ spustit něco pomalejší než jeho LINQ na objekty ekvivalentní. Základní pravidlem je, že jsou dotazy, které mají několik zdrojové elementy a rychlé uživatelské delegáty mnohem není možné příliš. Ale protože výkonu mnoho faktorů, doporučujeme změřit skutečné výsledky, než se rozhodnete, jestli se má použít PLINQ. Další informace najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="avoid-writing-to-shared-memory-locations"></a>Vyhněte se zápis do umístění sdílené paměti  
 V sekvenčních kódu není z číst nebo zapisovat na statické proměnné nebo třída polí. Vždy, když souběžně několik vláken přistupují takovéto proměnné, je však vysoká pravděpodobnost časování. I když používáte zámky synchronizovat přístup k proměnné náklady na synchronizace může narušit výkonnost. Proto doporučujeme můžete vyhnout, nebo alespoň omezit přístup ke sdílenému stavu v PLINQ dotazu co nejvíc.  
  
## <a name="avoid-over-parallelization"></a>Vyhněte se nadbytečnému  
 Pomocí `AsParallel` operátor, způsobit režijní náklady na vytváření oddílů zdrojové kolekci a synchronizaci pracovních vláken. Výhody paralelního zpracování jsou další omezen počet procesorů v počítači. Neexistuje žádné zrychlení užitečného spuštěním několika výpočetních vláken na počítače s více procesory. Proto musí být pozor, abyste přepsání paralelní dotaz.  
  
 Nejběžnější scénáře v nadbytečného paralelního zpracování může dojít, je ve vnořené dotazy, jak je znázorněno v následujícím fragmentu kódu.  
  
 [!code-csharp[PLINQ#20](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
 [!code-vb[PLINQ#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]  
  
 V takovém případě je nejlepší učinit paralelní pouze vnější zdroji dat (zákazníci), pokud jeden nebo více z následujících podmínek:  
  
-   Zdroj dat vnitřní (položka zákazníka. Objednávky) je znám trvat velmi dlouho.  
  
-   V každé pořadí jsou prováděny nákladné výpočty. (Operace v příkladu není nákladné.)  
  
-   Cílový systém se označuje má dostatek procesorů pro zpracování počet vláken, které budou vytvořeny paralelním prováděním dotaz na `cust.Orders`.  
  
 Ve všech případech je nejlepší způsob, jak určit optimální tvar dotazu pro testování a měření. Další informace najdete v tématu [postupy: měření výkonu dotazu PLINQ](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).  
  
## <a name="avoid-calls-to-non-thread-safe-methods"></a>Vyhněte se volání metody není bezpečná pro přístup z více vláken  
 Zápis metod není bezpečná pro přístup z více vláken, které PLINQ dotazu může vést k poškození dat, který může nebo nemusí být v programu. Může vést k výjimkám. V následujícím příkladu by být více vláken pokusit volání `Filestream.Write` metoda současně, což není podporováno v třídě.  
  
```vb  
Dim fs As FileStream = File.OpenWrite(…)  
a.Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))  
```  
  
```csharp  
FileStream fs = File.OpenWrite(...);  
a.Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));  
```  
  
## <a name="limit-calls-to-thread-safe-methods"></a>Limit volání metody bezpečné pro přístup z více vláken  
 Většina statických metod v rozhraní .NET Framework jsou bezpečné pro přístup z více vláken a lze volat z více vláken současně. I v těchto případech však zapojení synchronizace může vést k významnému zpomalení v dotazu.  
  
> [!NOTE]
>  Můžete vyzkoušet pro tento sami vložením některé volání <xref:System.Console.WriteLine%2A> v dotazech. I když tato metoda se používá v příkladech dokumentace pro demonstrační účely, nepoužívejte ji v PLINQ dotazy.  
  
## <a name="avoid-unnecessary-ordering-operations"></a>Vyhněte se nadbytečným operacím řazení  
 Když PLINQ provede dotaz paralelně, rozdělí zdrojové sekvence na oddíly, které lze provozovat na souběžně na více vláken. Ve výchozím nastavení, není předvídatelný pořadí, ve kterém oddíly, které se zpracovávají a výsledky se dodávají (s výjimkou operátory, jako například `OrderBy`). Můžete určit, aby PLINQ zachovat řazení žádné zdrojové sekvence, ale to má negativní dopad na výkon. Osvědčený postup, kdykoli je to možné, je na dotazy, struktura, aby se nespoléhejte na zachování pořadí. Další informace najdete v tématu [zachování pořadí v PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).  
  
## <a name="prefer-forall-to-foreach-when-it-is-possible"></a>Foreach – Pokud je možné, raději ForAll  
 I když PLINQ provede dotaz na více vláken, pokud využívat výsledky v `foreach` smyčky (`For Each` v jazyce Visual Basic), pak musí být sloučeny zpět do jednoho vlákna a k sériově pomocí enumerátoru výsledky dotazu. V některých případech je to nevyhnutelné; ale pokud je to možné, použijte `ForAll` způsob povolení každé vlákno výstup vlastních výsledků, například jako zápisem do kolekce bezpečné pro přístup z více vláken <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.  
  
 Stejný problém se vztahuje na <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> jinými slovy, `source.AsParallel().Where().ForAll(...)` by měla být důrazně upřednostňované na  
  
 `Parallel.ForEach(source.AsParallel().Where(), ...)`.  
  
## <a name="be-aware-of-thread-affinity-issues"></a>Mějte na paměti problémy spřažení podprocesu  
 Některé technologie, například interoperabilita modelů COM pro jedno vláknové objekty Apartment (STA) součásti Windows Forms a Windows Presentation Foundation (WPF) použít omezení na spřažení vláken, které vyžadují spuštění kódu na konkrétní vlákno. Například ve Windows Forms a WPF ovládacího prvku můžete přistupovat pouze ve vlákně, v němž byla vytvořena. Pokud se pokusíte přístup ke sdílenému stavu ovládacího prvku Windows Forms v PLINQ dotazu, je vyvolána výjimka, pokud používáte v ladicím programu. (Toto nastavení může být vypnuto.) Ale pokud dotaz se využívá v vlákna uživatelského rozhraní, pak dostanete z ovládacího prvku `foreach` smyčky, která se zobrazí dotaz výsledky, protože tento kód je prováděn pouze jedno vlákno.  
  
## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>Nepředpokládejte, že iterace ForEach, pro a ForAll vždy provést paralelní  
 Je důležité mít na paměti, že jednotlivé iterace ve <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> nebo <xref:System.Linq.ParallelEnumerable.ForAll%2A> cykly může, ale není nutné provést paralelně. Proto byste neměli psaní jakéhokoli kódu, který správnost závisí na paralelní provádění iterací nebo provádění iterací v libovolném pořadí.  
  
 Tento kód je například pravděpodobně dojde k zablokování:  
  
```vb  
Dim mre = New ManualResetEventSlim()  
    Enumerable.Range(0, ProcessorCount * 100).AsParallel().ForAll(Sub(j)   
  
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
            Enumerable.Range(0, ProcessorCount * 100).AsParallel().ForAll((j) =>  
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
  
 V tomto příkladu jedna iterace události a všechny ostatní iterace čekat na události. Žádná z čekajících iterací provést až po dokončení nastavení události iterací. Je však možné, že čekajících iterací blokovat všechna vlákna, které se používají ke spouštění paralelní smyčky před událostí iterace dostal příležitost provést. To vede k zablokování – událost iterace se nikdy neprovede a čekající iterace se nikdy probuzení.  
  
 Na konkrétní jeden iterace paralelní smyčky by nikdy čekat na jinou iteraci smyčky pokračovat. Pokud se při plánování iterace sekvenčně, ale v opačném pořadí rozhodne paralelní smyčky, dojde k zablokování.  
  
## <a name="see-also"></a>Viz také  
 [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
