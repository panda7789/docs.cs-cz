---
title: Potenciální nástrahy datového a funkčního paralelismu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel programming, pitfalls
ms.assetid: 1e357177-e699-4b8f-9e49-56d3513ed128
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5613128950d53946d55050ba3fd77cf1f0bb048a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54513422"
---
# <a name="potential-pitfalls-in-data-and-task-parallelism"></a>Potenciální nástrahy datového a funkčního paralelismu
V mnoha případech <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> výrazné zlepšení výkonu může poskytovat prostřednictvím běžných sekvenčních smyčkách. Paralelní provádění smyčky však zavádí složitost, která může vést k problémům, které v sekvenčním kódu nejsou jako běžné nebo nejsou vůbec došlo k. Toto téma uvádí některé nedoporučované postupy při psaní paralelní smyčky.  
  
## <a name="do-not-assume-that-parallel-is-always-faster"></a>Nepředpokládejte, že paralelní je vždy rychlejší  
 V některých případech může být pomalejší než sekvenční ekvivalent spuštění paralelní smyčky. Základním pravidlem je, že jsou paralelních smyček, které mají několik iterací a rychlé uživatelské delegáty velmi nepravděpodobné, že by zrychlení. Ale vzhledem k tomu výkon ovlivňuje mnoho faktorů, doporučujeme vždy měření skutečné výsledky.  
  
## <a name="avoid-writing-to-shared-memory-locations"></a>Vyhněte se zápis do umístění sdílené paměti  
 V sekvenčním kódu není nic neobvyklého, čtení nebo zápis do statické proměnné nebo pole třídy. Pokaždé, když přistupuje více podprocesů tyto proměnné souběžně, existuje však velké objemy potenciální konflikty časování. I když zámky můžete použít k synchronizaci přístupu k proměnné, náklady na synchronizaci může snížit výkon. Proto doporučujeme vám vyhnout, nebo aspoň omezit přístup ke sdílenému stavu v paralelních smyčkách co největší míře. Nejlepší způsob, jak to provést, je použít přetížení <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> , které používají <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> proměnnou pro uložení místního vlákna stav během provádění smyčky. Další informace najdete v tématu [jak: Zápis smyčky Parallel.for pomocí proměnných v místním vláknu](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md) a [jak: Zápis smyčky Parallel.ForEach pomocí proměnných v místním oddílu](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md).  
  
## <a name="avoid-over-parallelization"></a>Vyhněte se nadbytečnému  
 Při použití paralelních smyček, se vám účtovat režijní náklady na vytváření oddílů zdrojové kolekce a synchronizace pracovních vláken. Výhody paralelizace jsou dále omezeny počtem procesorů v počítači. Neexistuje žádné zrychlení k získané spuštěním více vláken výpočetní na právě jeden procesor. Proto musí být pozor, abyste nadbytečně smyčku.  
  
 Nejběžnější scénář, ve které nadbytečnému může dojít, je ve vnořených smyčky. Ve většině případů je nejvhodnější paralelizovat jenom vnější smyčky, pokud jedna nebo více z následujících podmínek:  
  
-   Vnitřní smyčky je známo, že trvat velmi dlouho.  
  
-   Provádíte náročné výpočty na jednotlivé objednávky. (Operace je znázorněno v příkladu není nákladné.)  
  
-   Cílový systém jsou známy dostatek procesorů pro zpracování počet vláken, které budou vytvořeny paralelní provádění dotazu na `cust.Orders`.  
  
 Ve všech případech je nejlepší způsob, jak určit optimální tvar dotazu pro testování a měření.  
  
## <a name="avoid-calls-to-non-thread-safe-methods"></a>Vyhněte se volání metody není bezpečné pro vlákna  
 Zápis do metody instance vláknově bezpečné paralelní smyčky může vést k poškození dat, který může nebo nemusí pokračovat nezjištěné po ve svém programu. Může také vést k výjimkám. V následujícím příkladu by se pokoušet více vláken k volání <xref:System.IO.FileStream.WriteByte%2A?displayProperty=nameWithType> metoda současně, což není podporována třídou.  
  
 [!code-csharp[TPL_Pitfalls#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#04)]
 [!code-vb[TPL_Pitfalls#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#04)]  
  
## <a name="limit-calls-to-thread-safe-methods"></a>Omezení volání metod bezpečným pro vlákno  
 Většina statických metod v rozhraní .NET Framework jsou bezpečné pro vlákna a může být volána z více vláken současně. I v těchto případech se však zapojení synchronizace může vést k výrazné mohou zpomalit zpracování dotazu.  
  
> [!NOTE]
>  Můžete vyzkoušet to sami vložením volání některých <xref:System.Console.WriteLine%2A> v dotazech. I když tato metoda se používá v příkladech dokumentaci pro demonstrační účely, nepoužívejte ji v paralelních smyčkách není-li nezbytné.  
  
## <a name="be-aware-of-thread-affinity-issues"></a>Mějte na paměti problémů, spřažení vláken  
 Některé technologie, například interoperabilita modelů COM pro jedno vláknové objekty Apartment (STA) součásti Windows Forms a Windows Presentation Foundation (WPF), omezení vlákno vztahů, které vyžadují spuštění kódu na konkrétním vlákně. Například ve Windows Forms a WPF, ovládací prvek je přístupný pouze na vlákně, na kterém byla vytvořena. To znamená například, že ovládací prvek seznamu paralelní smyčky nelze aktualizovat, pokud nenakonfigurujete vlákno scheduler k plánování práce pouze na vlákně UI při. Další informace najdete v tématu [jak: Plánování práce ve vlákně uživatelského rozhraní (UI)](https://msdn.microsoft.com/library/32a846a5-d628-4933-907b-4888ff72c663).  
  
## <a name="use-caution-when-waiting-in-delegates-that-are-called-by-parallelinvoke"></a>Buďte opatrní při čekání na v delegáty, kteří jsou volány Parallel.Invoke  
 V některých případech bude Task Parallel Library vložené úlohy, což znamená, že běží na úlohu s aktuálně spuštěné vlákno. (Další informace najdete v tématu [Plánovačích úkolů](https://msdn.microsoft.com/library/638f8ea5-21db-47a2-a934-86e1e961bf65).) Optimalizace výkonu může vést k zablokování v některých případech. Například dvě úlohy mohly stejného delegáta kód, který signalizuje, že dojde k události, a potom čeká na signál jiných úloh. Pokud druhá úloha je vložená ve stejném vlákně jako první a první přejde do stavu čekání, druhá úloha již nikdy nebude moct signalizuje, že jeho událost. Aby se zabránilo taková situace, můžete zadat časový limit na operace čekání nebo použijte explicitní konstruktory vlákna zajistit, že některá úloha nelze blokovat druhé.  
  
## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>Nepředpokládejte, že iterace ForEach, pro a ForAll vždy spustit paralelně  
 Je důležité mít na paměti, že jednotlivé iterace v <xref:System.Threading.Tasks.Parallel.For%2A>, <xref:System.Threading.Tasks.Parallel.ForEach%2A> nebo <xref:System.Linq.ParallelEnumerable.ForAll%2A> smyčky může, ale není nutné spustit paralelně. Proto byste se měli vyhnout psaní kódu, který správnost závisí na paralelní zpracování iterace nebo spuštění iterace v libovolném pořadí. Například tento kód je pravděpodobně dojde k zablokování:  
  
 [!code-csharp[TPL_Pitfalls#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#01)]
 [!code-vb[TPL_Pitfalls#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#01)]  
  
 V tomto příkladu jednu iteraci nastaví událost a všech dalších iterací čekání na událost. Žádné čekající iterace můžete dokončit až do dokončení iterace nastavení události. Je však možné, že čekajících iterací blokovat všechna vlákna, které se používají ke spouštění paralelní smyčky před událostí iterace dostala příležitost k provedení. Výsledkem zablokování – událost iterace se nikdy neprovede a iterace čekání se nikdy probuzení.  
  
 Zejména jedné iterace paralelní smyčky by nikdy čekat na další iteraci smyčky pokroku. Pokud se rozhodne paralelní smyčky naplánování iterace sekvenčně, ale v opačném pořadí, dojde k zablokování.  
  
## <a name="avoid-executing-parallel-loops-on-the-ui-thread"></a>Vyhněte se na vlákně UI při spouštění paralelní smyčky  
 Je důležité udržovat responzivní uživatelské rozhraní (UI). Pokud operace obsahuje dostatek práce, aby vláknem, ho pravděpodobně by neměla být spusťte tuto operaci na vlákně UI.  Místo toho by měl snižování zátěže tuto operaci k použití na vlákně na pozadí. Například pokud chcete použít paralelní smyčky pro výpočet nějaká data, která má být vykreslen pak do ovládacího prvku uživatelského rozhraní, měli byste zvážit spuštění smyčky v rámci instance úlohy, nikoli přímo v obslužné rutině události uživatelského rozhraní.  Pouze po dokončení základní výpočetní by vám pak zařazování aktualizace uživatelského rozhraní zpět do vlákna uživatelského rozhraní.  
  
 Pokud na vlákně UI při spouštění paralelní smyčky, pečlivě vyhnout aktualizace ovládacích prvků uživatelského rozhraní z v rámci smyčky. Pokus o aktualizaci uživatelského rozhraní ovládacích prvků z v rámci paralelní smyčky, který spouští ve vlákně uživatelského rozhraní může vést k poškození stavu, výjimky, opožděné aktualizace a dokonce zablokování, v závislosti na tom, jak vyvolat aktualizaci uživatelského rozhraní. Paralelní smyčka v následujícím příkladu blokuje vlákno uživatelského rozhraní, na kterém je spuštěn, dokud nejsou dokončeny všechny iterace. Ale pokud iteraci smyčky běží na vlákně na pozadí (jako <xref:System.Threading.Tasks.Parallel.For%2A> může provádět), volání Invoke způsobí, že zprávy k odeslání do vlákna uživatelského rozhraní a čeká na zpracování této zprávy. Protože blokovaný vlákně UI při spuštění <xref:System.Threading.Tasks.Parallel.For%2A>, může nikdy být zpráva zpracována a zablokování vlákna uživatelského rozhraní.  
  
 [!code-csharp[TPL_Pitfalls#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#02)]
 [!code-vb[TPL_Pitfalls#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#02)]  
  
 Následující příklad ukazuje, jak nedošlo k zablokování spuštěním smyčky do instance úlohy. Smyčky neblokuje vlákno uživatelského rozhraní a může být zpráva zpracována.  
  
 [!code-csharp[TPL_Pitfalls#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#03)]
 [!code-vb[TPL_Pitfalls#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#03)]  
  
## <a name="see-also"></a>Viz také:

- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
- [Potenciální nástrahy PLINQ](../../../docs/standard/parallel-programming/potential-pitfalls-with-plinq.md)
- [Vzory paralelního programování: Principy a použití paralelních vzorů s rozhraním .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222)
