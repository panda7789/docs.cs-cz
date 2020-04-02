---
title: Potenciální úskalí s PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
ms.openlocfilehash: 44f40d6caad9187376a790f9a0ed09e22c861e37
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588602"
---
# <a name="potential-pitfalls-with-plinq"></a>Potenciální úskalí s PLINQ

V mnoha případech PLINQ může poskytnout významné zlepšení výkonu oproti sekvenční LINQ na objekty dotazy. Práce paralelizace spuštění dotazu však zavádí složitost, která může vést k problémům, které v sekvenčním kódu nejsou tak běžné nebo se vůbec nevyskytují. Toto téma uvádí některé postupy, kterým je třeba se vyhnout při psaní dotazů PLINQ.

## <a name="dont-assume-that-parallel-is-always-faster"></a>Nepředpokládejte, že paralelní je vždy rychlejší

Paralelizace někdy způsobí, že dotaz PLINQ spustit pomaleji než jeho LINQ na objekty ekvivalent. Základní pravidlo je, že dotazy, které mají málo zdrojových prvků a rychlé uživatelské delegáty je nepravděpodobné, že urychlit hodně. Však vzhledem k tomu, že mnoho faktorů jsou zapojeny do výkonu, doporučujeme měřit skutečné výsledky před se rozhodnete, zda použít PLINQ. Další informace naleznete [v tématu Principy zrychlení v PLINQ](understanding-speedup-in-plinq.md).

## <a name="avoid-writing-to-shared-memory-locations"></a>Vyhněte se zápisu do sdílených umístění paměti

V sekvenčním kódu není neobvyklé číst nebo zapisovat do statických proměnných nebo polí tříd. Však vždy, když více vláken přístup k těmto proměnným současně, je velký potenciál pro podmínky závodu. I když můžete použít zámky k synchronizaci přístupu k proměnné, náklady na synchronizaci může poškodit výkon. Proto doporučujeme vyhnout nebo alespoň omezit přístup ke sdílenému stavu v dotazu PLINQ co nejvíce.

## <a name="avoid-over-parallelization"></a>Vyhněte se nadměrné paralelizaci

Pomocí `AsParallel` metody vzniknou režijní náklady na rozdělení zdrojové kolekce a synchronizaci pracovních podprocesů. Výhody paralelizace jsou dále omezeny počtem procesorů v počítači. Neexistuje žádné zrychlení, které lze získat spuštěním více vláken vázaných na výpočetní výkon pouze na jednom procesoru. Proto je třeba dbát na to, aby příliš paralelizovat dotaz.

Nejběžnější scénář, ve kterém může dojít k nadměrné paralelizaci, je v nosných dotazech, jak je znázorněno v následujícím fragmentu.

[!code-csharp[PLINQ#20](~/samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
[!code-vb[PLINQ#20](~/samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]

V tomto případě je nejlepší paralelizovat pouze vnější zdroj dat (zákazníky), pokud neplatí jedna nebo více z následujících podmínek:

- Vnitřní zdroj dat (cust. Objednávky) je známo, že je velmi dlouhá.

- Provádíte nákladné výpočty na každé objednávce. (Operace zobrazená v příkladu není nákladná.)

- Cílový systém je známo, že mají dostatek procesorů pro zpracování počtu podprocesů, `cust.Orders`které budou vytvořeny paralelizace dotazu na .

Ve všech případech je nejlepším způsobem, jak určit optimální tvar dotazu, testování a měření. Další informace naleznete v [tématu How to: Measure PLINQ Query Performance](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).

## <a name="avoid-calls-to-non-thread-safe-methods"></a>Vyhněte se volání metod, které nejsou bezpečné pro přístup z více vláken

Zápis do metod instancí, které nejsou bezpečné pro přístup z více vláken z dotazu PLINQ, může vést k poškození dat, které může nebo nemusí zůstat v programu neodhaleno. To může také vést k výjimkám. V následujícím příkladu by se více vláken `FileStream.Write` pokoušelo volat metodu současně, což není podporováno třídou.

```vb
Dim fs As FileStream = File.OpenWrite(…)
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))
```

```csharp
FileStream fs = File.OpenWrite(...);
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));
```

## <a name="limit-calls-to-thread-safe-methods"></a>Omezit volání na metody bezpečné pro přístup z více vláken

Většina statických metod v rozhraní .NET Framework je bezpečná pro přístup z více vláken a lze je volat z více vláken současně. Však i v těchto případech synchronizace účastní může vést k významné zpomalení v dotazu.

> [!NOTE]
> Můžete otestovat sami vložením některé <xref:System.Console.WriteLine%2A> volání do dotazů. Přestože tato metoda se používá v příkladech dokumentace pro demonstrační účely, nepoužívejte ji v plinq dotazy.

## <a name="avoid-unnecessary-ordering-operations"></a>Vyhněte se zbytečným operacím objednávání

Když PLINQ spustí dotaz paralelně, rozdělí zdrojové sekvence do oddílů, které mohou být provozovány současně na více vláken. Ve výchozím nastavení pořadí, ve kterém jsou zpracovány oddíly a výsledky jsou dodávány není předvídatelné (s výjimkou operátorů, jako je například `OrderBy`). Můžete pokyn PLINQ zachovat řazení libovolné zdrojové sekvence, ale to má negativní vliv na výkon. Osvědčeným postupem, kdykoli je to možné, je strukturovat dotazy tak, aby se nespoléhaly na zachování pořadí. Další informace naleznete [v tématu Order Preservation in PLINQ](order-preservation-in-plinq.md).

## <a name="prefer-forall-to-foreach-when-it-is-possible"></a>Preferujte forall na ForEach, když je to možné

Přestože PLINQ spustí dotaz na více vláken, pokud `foreach` spotřebováváte`For Each` výsledky ve smyčce (v jazyce Visual Basic), pak výsledky dotazu musí být sloučeny zpět do jednoho vlákna a přistupovat sériově čítač výčtu. V některých případech je to nevyhnutelné; pokud je to však možné, použijte metodu, `ForAll` která umožní každému vláknu vytvořit vlastní <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>výsledky, například zápisem do kolekce bezpečné pro přístup z více vláken, například .

Stejný problém platí <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>pro . Jinými slovy, `source.AsParallel().Where().ForAll(...)` by měla `Parallel.ForEach(source.AsParallel().Where(), ...)`být silně upřednostňována .

## <a name="be-aware-of-thread-affinity-issues"></a>Mějte na paměti problémy se spřažením vláken

Některé technologie, například interoperabilita modelu COM pro součásti sta (Single Threaded Apartment), Windows Forms a Windows Presentation Foundation (WPF), ukládají omezení spřažení vláken, která vyžadují spuštění kódu v určitém vlákně. Například ve formulářích systému Windows a WPF ovládací prvek lze přistupovat pouze ve vlákně, ve kterém byl vytvořen. Pokud se pokusíte o přístup ke sdílenému stavu ovládacího prvku Windows Forms v dotazu PLINQ, je vyvolána výjimka, pokud používáte v ladicím programu. (Toto nastavení lze vypnout.) Pokud je však dotaz spotřebován ve vlákně uživatelského `foreach` rozhraní, můžete získat přístup k ovládacímu prvku ze smyčky, která obsahuje enumerates výsledky dotazu, protože tento kód se spustí pouze v jednom vlákně.

## <a name="dont-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>Nepředpokládejte, že iterace ForEach, For a ForAll vždy spustit paralelně

Je důležité mít na paměti, že <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>jednotlivé <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>iterace v , , nebo <xref:System.Linq.ParallelEnumerable.ForAll%2A> smyčky může, ale nemusí provádět paralelně. Proto byste se měli vyhnout psaní kódu, který závisí na správnosti na paralelní provádění iterací nebo na provádění iterací v libovolném pořadí.

Například tento kód je pravděpodobně zablokování:

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

V tomto příkladu jedna iterace nastaví událost a všechny ostatní iterace čekat na událost. Žádná z čekajících iterací nemůže být dokončena, dokud nebude dokončena iterace nastavení události. Je však možné, že čekající iterace blokují všechna vlákna, která se používají ke spuštění paralelní smyčky, než má iterace nastavení události šanci provést. To má za následek zablokování – iterace nastavení událostí se nikdy nespustí a čekající iterace se nikdy neprobudí.

Zejména jedna iterace paralelní smyčky by nikdy neměla čekat na jinou iteraci smyčky, aby se pokročilo. Pokud paralelní smyčka rozhodne naplánovat iterací postupně, ale v opačném pořadí, dojde k zablokování.

## <a name="see-also"></a>Viz také

- [Paralelní LINQ (PLINQ)](introduction-to-plinq.md)
