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
ms.openlocfilehash: ff6ac9e8c41ee203ae72e1b28c088f462ddf6a54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140030"
---
# <a name="potential-pitfalls-in-data-and-task-parallelism"></a>Potenciální nástrahy datového a funkčního paralelismu
V mnoha <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> případech <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> a může poskytnout významné zlepšení výkonu přes běžné sekvenční smyčky. Práce paralelizace smyčky však zavádí složitost, která může vést k problémům, které v sekvenčním kódu nejsou tak běžné nebo se vůbec nevyskytují. Toto téma uvádí některé postupy, kterým je třeba se vyhnout při psaní paralelních smyček.  
  
## <a name="do-not-assume-that-parallel-is-always-faster"></a>Nepředpokládejte, že paralelní je vždy rychlejší  
 V některých případech může paralelní smyčka běžet pomaleji než jeho sekvenční ekvivalent. Základní pravidlo je, že paralelní smyčky, které mají několik iterací a rychlé uživatelské delegáty je nepravděpodobné, že urychlit hodně. Protože však do výkonu je zapojeno mnoho faktorů, doporučujeme vždy měřit skutečné výsledky.  
  
## <a name="avoid-writing-to-shared-memory-locations"></a>Vyhněte se zápisu do umístění sdílené paměti  
 V sekvenčním kódu není neobvyklé číst nebo zapisovat do statických proměnných nebo polí tříd. Však vždy, když více vláken přístup k těmto proměnným současně, je velký potenciál pro podmínky závodu. I když můžete použít zámky k synchronizaci přístupu k proměnné, náklady na synchronizaci může poškodit výkon. Proto doporučujeme vyhnout nebo alespoň omezit přístup ke sdílenému stavu v paralelní smyčce co nejvíce. Nejlepší způsob, jak to provést, je <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> použít přetížení <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> a které používají proměnnou k uložení místního stavu vlákna během spuštění smyčky. Další informace naleznete v [tématu How to: Write a Parallel.For Loop with Thread-Local Variables](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md) and [How to: Write a Parallel.ForEach Loop with Partition-Local Variables](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md).  
  
## <a name="avoid-over-parallelization"></a>Vyhněte se nadměrné paralelizaci  
 Pomocí paralelní smyčky, vzniknou režijní náklady na rozdělení zdrojové kolekce a synchronizace pracovních podprocesů. Výhody paralelizace jsou dále omezeny počtem procesorů v počítači. Neexistuje žádné zrychlení, které lze získat spuštěním více vláken vázaných na výpočetní výkon pouze na jednom procesoru. Proto musíte být opatrní, abyste příliš neparalelizovali smyčku.  
  
 Nejběžnější scénář, ve kterém může dojít k over-parallelization je v vnořené smyčky. Ve většině případů je nejlepší paralelizovat pouze vnější smyčku, pokud neplatí jedna nebo více z následujících podmínek:  
  
- Vnitřní smyčka je známo, že je velmi dlouhá.  
  
- Provádíte nákladné výpočty na každé objednávce. (Operace zobrazená v příkladu není nákladná.)  
  
- Cílový systém je známo, že mají dostatek procesorů pro zpracování počtu podprocesů, `cust.Orders`které budou vytvořeny paralelizace dotazu na .  
  
 Ve všech případech je nejlepším způsobem, jak určit optimální tvar dotazu, testování a měření.  
  
## <a name="avoid-calls-to-non-thread-safe-methods"></a>Vyhněte se volání metod, které nejsou bezpečné pro přístup z více vláken  
 Zápis do metod instancí, které nejsou bezpečné pro přístup z více vláken z paralelní smyčky, může vést k poškození dat, které může nebo nemusí zůstat v programu neodhaleno. To může také vést k výjimkám. V následujícím příkladu by se více vláken <xref:System.IO.FileStream.WriteByte%2A?displayProperty=nameWithType> pokoušelo volat metodu současně, což není podporováno třídou.  
  
 [!code-csharp[TPL_Pitfalls#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#04)]
 [!code-vb[TPL_Pitfalls#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#04)]  
  
## <a name="limit-calls-to-thread-safe-methods"></a>Omezit volání metod bezpečných pro přístup z více vláken  
 Většina statických metod v rozhraní .NET Framework je bezpečná pro přístup z více vláken a lze je volat z více vláken současně. Však i v těchto případech synchronizace účastní může vést k významné zpomalení v dotazu.  
  
> [!NOTE]
> Můžete otestovat sami vložením některé <xref:System.Console.WriteLine%2A> volání do dotazů. Ačkoli tato metoda se používá v příkladech dokumentace pro demonstrační účely, nepoužívejte ji v paralelních smyčkách, pokud to není nutné.  
  
## <a name="be-aware-of-thread-affinity-issues"></a>Buďte si vědomi problémů s afinitou vláken  
 Některé technologie, například interoperabilita modelu COM pro součásti sta (Single Threaded Apartment), Windows Forms a Windows Presentation Foundation (WPF), ukládají omezení spřažení vláken, která vyžadují spuštění kódu v určitém vlákně. Například ve formulářích systému Windows a WPF ovládací prvek lze přistupovat pouze ve vlákně, ve kterém byl vytvořen. To například znamená, že nelze aktualizovat ovládací prvek seznamu z paralelní smyčky, pokud nenakonfigurujete plánovač podprocesů tak, aby naplánoval práci pouze ve vlákně uživatelského rozhraní. Další informace naleznete [v tématu Určení kontextu synchronizace](xref:System.Threading.Tasks.TaskScheduler#specifying-a-synchronization-context).  
  
## <a name="use-caution-when-waiting-in-delegates-that-are-called-by-parallelinvoke"></a>Při čekání v delegátech, které jsou volány parallel.invoke, buďte opatrní při čekání v delegátech, které jsou volány parallel.invoke  
 Za určitých okolností paralelní knihovna úlohy vstoní úlohy, což znamená, že je spuštěna na úkolu v aktuálně spuštěném vlákně. (Další informace naleznete v [tématu Plánovače úloh](xref:System.Threading.Tasks.TaskScheduler).) Tato optimalizace výkonu může vést k zablokování v určitých případech. Například dva úkoly může spustit stejný kód delegáta, který signalizuje, když dojde k události a pak čeká na signál jiné úlohy. Pokud druhý úkol je vloženve stejném vlákně jako první a první přejde do wait stavu, druhý úkol nikdy nebude moci signalizovat jeho událost. Chcete-li se takovému výskytu vyhnout, můžete zadat časový čas operace Wait nebo použít explicitní konstruktory vláken, které pomohou zajistit, že jeden úkol nemůže blokovat druhou.  
  
## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>Nepředpokládejte, že iterace ForEach, For a ForAll vždy spustit paralelně  
 Je důležité mít na paměti, že <xref:System.Threading.Tasks.Parallel.For%2A>jednotlivé <xref:System.Threading.Tasks.Parallel.ForEach%2A> <xref:System.Linq.ParallelEnumerable.ForAll%2A> iterace v , nebo smyčky může, ale nemusí provádět paralelně. Proto byste se měli vyhnout psaní kódu, který závisí na správnosti na paralelní provádění iterací nebo na provádění iterací v libovolném pořadí. Například tento kód je pravděpodobně zablokování:  
  
 [!code-csharp[TPL_Pitfalls#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#01)]
 [!code-vb[TPL_Pitfalls#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#01)]  
  
 V tomto příkladu jedna iterace nastaví událost a všechny ostatní iterace čekat na událost. Žádná z čekajících iterací nemůže být dokončena, dokud nebude dokončena iterace nastavení události. Je však možné, že čekající iterace blokují všechna vlákna, která se používají ke spuštění paralelní smyčky, než má iterace nastavení události šanci provést. To má za následek zablokování – iterace nastavení událostí se nikdy nespustí a čekající iterace se nikdy neprobudí.  
  
 Zejména jedna iterace paralelní smyčky by nikdy neměla čekat na jinou iteraci smyčky, aby se pokročilo. Pokud paralelní smyčka rozhodne naplánovat iterací postupně, ale v opačném pořadí, dojde k zablokování.  
  
## <a name="avoid-executing-parallel-loops-on-the-ui-thread"></a>Vyhněte se provádění paralelních smyček ve vlákně uživatelského rozhraní  
 Je důležité, aby uživatelské rozhraní (UI) vaší aplikace reagovalo. Pokud operace obsahuje dostatek práce pro ritování paralelizace, pak je pravděpodobné, že by neměl a spustit tuto operaci ve vlákně uživatelského rozhraní.  Místo toho by měl převést tuto operaci spustit na podprocesu na pozadí. Například pokud chcete použít paralelní smyčky vypočítat některá data, která by pak měla být vykreslena do ovládacího prvku ui, měli byste zvážit spuštění smyčky v rámci instance úlohy, nikoli přímo v obslužné rutině události ui.  Pouze po dokončení výpočtu jádra by pak zařazování aktualizace uživatelského rozhraní zpět do vlákna uživatelského rozhraní.  
  
 Pokud spustíte paralelní smyčky ve vlákně uživatelského rozhraní, dávejte pozor, abyste se vyhnuli aktualizaci ovládacích prvků uživatelského rozhraní z smyčky. Pokus o aktualizaci ovládacích prvků uživatelského rozhraní z paralelní smyčky, která je spuštěna ve vlákně uživatelského rozhraní může vést k poškození stavu, výjimky, zpožděné aktualizace a dokonce i zablokování, v závislosti na tom, jak je vyvolána aktualizace uživatelského rozhraní. V následujícím příkladu paralelní smyčka blokuje vlákno uživatelského rozhraní, na kterém je spuštěna, dokud nejsou dokončeny všechny iterace. Však pokud iterace smyčky je spuštěna <xref:System.Threading.Tasks.Parallel.For%2A> na podprocesu na pozadí (jak může provést), volání Invoke způsobí, že zpráva, která má být odeslána do vlákna uživatelského rozhraní a bloky čekání na tuto zprávu, která má být zpracována. Vzhledem k tomu, že <xref:System.Threading.Tasks.Parallel.For%2A>vlákno uživatelského rozhraní je blokován o spuštění , zpráva nelze nikdy zpracovat a zablokování vlákna uživatelského rozhraní.  
  
 [!code-csharp[TPL_Pitfalls#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#02)]
 [!code-vb[TPL_Pitfalls#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#02)]  
  
 Následující příklad ukazuje, jak se vyhnout zablokování spuštěním smyčky uvnitř instance úlohy. Vlákno uživatelského rozhraní není blokován o smyčku a zpráva může být zpracována.  
  
 [!code-csharp[TPL_Pitfalls#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#03)]
 [!code-vb[TPL_Pitfalls#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#03)]  
  
## <a name="see-also"></a>Viz také

- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
- [Potenciální nástrahy PLINQ](../../../docs/standard/parallel-programming/potential-pitfalls-with-plinq.md)
- [Vzory pro paralelní programování: Pochopení a použití paralelních vzorů s rozhraním .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222)
