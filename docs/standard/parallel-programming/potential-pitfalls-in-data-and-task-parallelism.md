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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140030"
---
# <a name="potential-pitfalls-in-data-and-task-parallelism"></a>Potenciální nástrahy datového a funkčního paralelismu
V mnoha případech můžou <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> v rámci běžných sekvenčních cyklů poskytovat významná vylepšení výkonu. Nicméně práce virtuálního smyčka zavádí složitost, která může vést k problémům, které se v sekvenčním kódu nevyskytují jako běžné nebo nejsou vůbec k dispozici. V tomto tématu jsou uvedeny některé postupy, které se vyhnete při psaní paralelních smyček.  
  
## <a name="do-not-assume-that-parallel-is-always-faster"></a>Nepředpokládat, že paralelní je vždycky rychlejší  
 V některých případech může paralelní smyčka běžet pomalejší než jeho sekvenční ekvivalent. Základní pravidlo pro palec je, že paralelní smyčky, které mají několik iterací a rychlé delegáty uživatele, nejsou pravděpodobně zrychlení mnohem. Vzhledem k tomu, že je v výkonu mnoho faktorů, doporučujeme, abyste vždycky měřili skutečné výsledky.  
  
## <a name="avoid-writing-to-shared-memory-locations"></a>Vyhněte se zápisu do sdílených umístění paměti  
 V sekvenčním kódu není běžné číst z nebo zapisovat do statických proměnných nebo polí třídy. Kdykoli však více vláken přistupuje k těmto proměnným současně, existuje velký potenciál pro konflikty časování. I když můžete použít zámky k synchronizaci přístupu k proměnné, náklady na synchronizaci můžou snížit výkon. Proto doporučujeme, abyste se vyhnuli nebo přinejmenším omezili přístup ke sdílenému stavu v paralelní smyčce, a to co nejvíc. Nejlepším způsobem, jak to provést, je použít přetížení <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>, které používají proměnnou <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> k uložení místního stavu vlákna během provádění smyčky. Další informace naleznete v tématu [How to: Write a Parallel. for smyčke s proměnnými místními vlákny](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md) a [How to: napište smyčku Parallel. ForEach s proměnnými místně na oddíl](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md).  
  
## <a name="avoid-over-parallelization"></a>Vyhnout se paralelnímu využití  
 Pomocí paralelních smyček se účtují režijní náklady na rozdělení zdrojové kolekce a synchronizaci pracovních vláken. Výhody paralelismu jsou dále omezeny počtem procesorů v počítači. Neexistují žádné zrychlení, které by bylo možné vymezit spuštěním více výpočetních vláken vázaných na pouze jeden procesor. Proto musíte mít pozor, abyste paralelizovat smyčku.  
  
 Nejběžnější scénář, ve kterém může dojít k paralelnímu navýšení, je ve vnořených smyčkách. Ve většině případů je nejlepší paralelizovat jenom vnější smyčka, pokud se nepoužijí některé z následujících podmínek:  
  
- Je známo, že vnitřní smyčka bude velmi dlouhá.  
  
- V každé objednávce provádíte nákladný výpočet. (Operace uvedená v příkladu není nákladná.)  
  
- Pro cílový systém je známo, že má dostatek procesorů pro zpracování počtu vláken, která budou vytvořena virtuálního dotazem na `cust.Orders`.  
  
 Ve všech případech je nejlepším způsobem, jak určit optimální obrazec dotazu, testování a měření.  
  
## <a name="avoid-calls-to-non-thread-safe-methods"></a>Nepoužívejte volání metod, které nejsou bezpečné pro přístup z více vláken  
 Zápis na metody instance bez vlákna z paralelní smyčky může vést k poškození dat, které může nebo nemusí být v programu nedetekováno. Může také vést k výjimkám. V následujícím příkladu se více vláken pokusí zavolat metodu <xref:System.IO.FileStream.WriteByte%2A?displayProperty=nameWithType> současně, což není podporováno třídou.  
  
 [!code-csharp[TPL_Pitfalls#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#04)]
 [!code-vb[TPL_Pitfalls#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#04)]  
  
## <a name="limit-calls-to-thread-safe-methods"></a>Omezení volání metod bezpečných pro přístup z více vláken  
 Většina statických metod v .NET Framework je bezpečná pro přístup z více vláken a je možné ji volat z více vláken současně. Nicméně i v těchto případech může synchronizace vést k významnému zpomalení dotazu.  
  
> [!NOTE]
> Můžete to otestovat sami vložením některých volání do <xref:System.Console.WriteLine%2A> v dotazech. I když se tato metoda používá v příkladech dokumentace pro demonstrační účely, nepoužívejte ji v paralelních smyčkách, pokud není potřeba.  
  
## <a name="be-aware-of-thread-affinity-issues"></a>Informace o problémech spřažení vláken  
 Některé technologie, například interoperabilita modelu COM pro součásti s jedním vláknem (STA), model Windows Forms a Windows Presentation Foundation (WPF), ukládají omezení spřažení vláken, která vyžadují spouštění kódu v konkrétním vlákně. Například v model Windows Forms i WPF může být ovládací prvek k dispozici pouze ve vlákně, ve kterém byl vytvořen. To znamená, že například nelze aktualizovat ovládací prvek seznamu z paralelní smyčky, pokud nenastavíte Plánovač vlákna tak, aby naplánoval práci pouze ve vlákně uživatelského rozhraní. Další informace naleznete v tématu [určení kontextu synchronizace](xref:System.Threading.Tasks.TaskScheduler#specifying-a-synchronization-context).  
  
## <a name="use-caution-when-waiting-in-delegates-that-are-called-by-parallelinvoke"></a>Při čekání v delegátech volaných voláním Parallel. Invoke buďte opatrní.  
 V některých případech bude úloha paralelní knihovny vložen úkol, což znamená, že se spustí na úkolu v aktuálně zpracovávaném vlákně. (Další informace najdete v tématu [plánovače úloh](xref:System.Threading.Tasks.TaskScheduler).) Tato optimalizace výkonu může vést k zablokování v určitých případech. Například dvě úlohy mohou spustit stejný kód delegáta, který signalizuje, když dojde k události, a poté čeká, až se druhý úkol dorazí na signál. Pokud je druhá úloha vložena ve stejném vlákně jako první a první přejde do stavu čekání, druhá úloha nebude nikdy moci signalizovat událost. Chcete-li se tomuto výskytu vyhnout, můžete zadat časový limit pro operaci čekání nebo použít explicitní konstruktory vlákna, které vám pomohou zajistit, že jeden úkol nemůže blokovat druhý.  
  
## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>Nepředpokládáme, že iterace ForEach, for a ForAll vždy provádějí paralelně  
 Je důležité pamatovat na to, že jednotlivé iterace v <xref:System.Threading.Tasks.Parallel.For%2A>, <xref:System.Threading.Tasks.Parallel.ForEach%2A> nebo <xref:System.Linq.ParallelEnumerable.ForAll%2A> smyčka nemusí být spouštěny paralelně. Proto byste se měli vyhnout psaní kódu, který závisí na správnosti paralelního provádění iterací nebo při provádění iterací v jakémkoli konkrétním pořadí. Například tento kód může zablokovat:  
  
 [!code-csharp[TPL_Pitfalls#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#01)]
 [!code-vb[TPL_Pitfalls#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#01)]  
  
 V tomto příkladu jedna iterace nastaví událost a všechny ostatní iterace na událost čekají. Žádná z čekacích iterací nemůže být dokončena, dokud se nedokončí iterace nastavení události. Je však možné, že čekající iterace zablokují všechna vlákna, která se používají ke spuštění paralelní smyčky, před tím, než bude iterace nastavení událostí vykonána. Výsledkem je zablokování – iterace nastavení události se nikdy nespustí a čekací iterace se nikdy neprobudí.  
  
 Konkrétně jedna iterace paralelní smyčky by nikdy neměla čekat na další iteraci smyčky, aby bylo možné postupovat. Pokud se paralelní smyčka rozhodne naplánovat iterace sekvenčně, ale v opačném pořadí, dojde k zablokování.  
  
## <a name="avoid-executing-parallel-loops-on-the-ui-thread"></a>Nespouštět paralelní smyčky ve vlákně UI  
 Je důležité zachovat reakce uživatelského rozhraní (UI) vaší aplikace. Pokud operace obsahuje dostatek práce pro zajištění paralelismu, pak pravděpodobně není nutné tuto operaci spustit ve vlákně uživatelského rozhraní.  Místo toho by měla přesměrovat tuto operaci na vlákno na pozadí. Například pokud chcete použít paralelní smyčku k výpočtu dat, která by měla být vykreslena do ovládacího prvku uživatelského rozhraní, měli byste zvážit spuštění smyčky v instanci úlohy, nikoli přímo v obslužné rutině události uživatelského rozhraní.  Pouze v případě, že je dokončeno základní výpočet, je třeba zařadit aktualizaci uživatelského rozhraní zpět do vlákna uživatelského rozhraní.  
  
 Pokud spouštíte paralelní smyčky ve vlákně uživatelského rozhraní, buďte opatrní, abyste se vyhnuli aktualizaci ovládacích prvků uživatelského rozhraní v rámci smyčky. Při pokusu o aktualizaci ovládacích prvků uživatelského rozhraní z paralelní smyčky, která je spuštěna na vlákně UI, může dojít k poškození stavu, výjimkám, zpožděným aktualizacím a dokonce zablokování v závislosti na tom, jak je vyvolána aktualizace uživatelského rozhraní. V následujícím příkladu paralelní smyčka zablokuje vlákno uživatelského rozhraní, na kterém je spuštěno, až do dokončení všech iterací. Pokud je však iterace smyčky spuštěna ve vlákně na pozadí (jako <xref:System.Threading.Tasks.Parallel.For%2A> může), volání metody Invoke způsobí odeslání zprávy do vlákna uživatelského rozhraní a blokuje čekání na zpracování této zprávy. Vzhledem k tomu, že vlákno uživatelského rozhraní je blokováno spuštěním <xref:System.Threading.Tasks.Parallel.For%2A>, zpráva nemůže být nikdy zpracována a dojde k zablokování vlákna uživatelského rozhraní.  
  
 [!code-csharp[TPL_Pitfalls#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#02)]
 [!code-vb[TPL_Pitfalls#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#02)]  
  
 Následující příklad ukazuje, jak se vyhnout zablokování spuštěním smyčky uvnitř instance úlohy. Vlákno uživatelského rozhraní není blokováno smyčkou a zprávu lze zpracovat.  
  
 [!code-csharp[TPL_Pitfalls#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#03)]
 [!code-vb[TPL_Pitfalls#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#03)]  
  
## <a name="see-also"></a>Viz také:

- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
- [Potenciální nástrahy PLINQ](../../../docs/standard/parallel-programming/potential-pitfalls-with-plinq.md)
- [Vzory paralelního programování: porozumění a použití paralelních vzorů s .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222)
