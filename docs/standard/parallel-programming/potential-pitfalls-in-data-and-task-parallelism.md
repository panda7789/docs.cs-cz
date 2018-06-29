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
ms.openlocfilehash: 6d4fd91eccd5e8f3fd6be7c8a63ab1c097002382
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2018
ms.locfileid: "37073226"
---
# <a name="potential-pitfalls-in-data-and-task-parallelism"></a>Potenciální nástrahy datového a funkčního paralelismu
V mnoha případech <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> může poskytnout významné zlepšení výkonu oproti běžným sekvenčním smyčkám. Vytváření paralelní smyčky však zavádí složitost, která může vést k problémům, které v sekvenčních kódu nejsou jako běžné nebo nejsou vůbec došlo. Toto téma uvádí některé postupy, abyste se vyhnuli při psaní paralelní smyčky.  
  
## <a name="do-not-assume-that-parallel-is-always-faster"></a>Nepředpokládejte, že paralelní, není vždy rychlejší  
 V některých případech může paralelní smyčky pracovat pomaleji než sekvenční ekvivalent. Základní pravidlem je, že jsou paralelní smyčky, které mají několik iterací a rychlé uživatelské delegáty mnohem není možné příliš. Ale protože výkonu mnoho faktorů, doporučujeme vždy změřit skutečné výsledky.  
  
## <a name="avoid-writing-to-shared-memory-locations"></a>Vyhněte se zápis do umístění sdílené paměti  
 V sekvenčních kódu není z číst nebo zapisovat na statické proměnné nebo třída polí. Vždy, když souběžně několik vláken přistupují takovéto proměnné, je však vysoká pravděpodobnost časování. I když používáte zámky synchronizovat přístup k proměnné náklady na synchronizace může narušit výkonnost. Proto doporučujeme můžete vyhnout, nebo alespoň omezit přístup ke sdílenému stavu v co nejvíce paralelní smyčky. Nejlepší způsob, jak to udělat, je použít přetížení <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> využívající <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> proměnnou pro uložení místní stav během provádění smyčky. Další informace najdete v tématu [postupy: zápis smyčky Parallel.For pomocí proměnných Thread-Local](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md) a [postupy: zápis smyčky Parallel.ForEach pomocí proměnných oddílu místní](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md).  
  
## <a name="avoid-over-parallelization"></a>Vyhněte se nadbytečnému  
 Pomocí paralelní smyčky způsobit režijní náklady na vytváření oddílů zdrojové kolekci a synchronizaci pracovních vláken. Výhody paralelního zpracování jsou další omezen počet procesorů v počítači. Neexistuje žádné zrychlení užitečného spuštěním několika výpočetních vláken na počítače s více procesory. Proto musí být pozor, abyste přepsání paralelní smyčka.  
  
 Nejběžnější scénáře v nadbytečného paralelního zpracování může dojít, je ve vnořené smyčky. Ve většině případů je nejlepší učinit paralelní pouze vnější smyčku, pokud jeden nebo více z následujících podmínek:  
  
-   Vnitřní smyčky je znám trvat velmi dlouho.  
  
-   V každé pořadí jsou prováděny nákladné výpočty. (Operace v příkladu není nákladné.)  
  
-   Cílový systém se označuje má dostatek procesorů pro zpracování počet vláken, které budou vytvořeny paralelním prováděním dotaz na `cust.Orders`.  
  
 Ve všech případech je nejlepší způsob, jak určit optimální tvar dotazu pro testování a měření.  
  
## <a name="avoid-calls-to-non-thread-safe-methods"></a>Vyhněte se volání metody není bezpečná pro přístup z více vláken  
 Zápis metod není bezpečná pro přístup z více vláken, které z paralelní smyčky může vést k poškození dat, který může nebo nemusí být v programu. Může vést k výjimkám. V následujícím příkladu by být více vláken pokusit volání <xref:System.IO.FileStream.WriteByte%2A?displayProperty=nameWithType> metoda současně, což není podporováno v třídě.  
  
 [!code-csharp[TPL_Pitfalls#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#04)]
 [!code-vb[TPL_Pitfalls#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#04)]  
  
## <a name="limit-calls-to-thread-safe-methods"></a>Limit volání metody bezpečné pro přístup z více vláken  
 Většina statických metod v rozhraní .NET Framework jsou bezpečné pro přístup z více vláken a lze volat z více vláken současně. I v těchto případech však zapojení synchronizace může vést k významnému zpomalení v dotazu.  
  
> [!NOTE]
>  Můžete vyzkoušet pro tento sami vložením některé volání <xref:System.Console.WriteLine%2A> v dotazech. I když tato metoda se používá v příkladech dokumentace pro demonstrační účely, nepoužívejte ji v paralelních smyčkách Pokud nezbytné.  
  
## <a name="be-aware-of-thread-affinity-issues"></a>Mějte na paměti problémy spřažení podprocesu  
 Některé technologie, například interoperabilita modelů COM pro jedno vláknové objekty Apartment (STA) součásti Windows Forms a Windows Presentation Foundation (WPF) použít omezení na spřažení vláken, které vyžadují spuštění kódu na konkrétní vlákno. Například ve Windows Forms a WPF ovládacího prvku můžete přistupovat pouze ve vlákně, v němž byla vytvořena. To znamená, například ovládací prvek seznamu paralelní smyčky nelze aktualizovat, pokud nezměníte konfiguraci Plánovač vlákno k plánování práce pouze ve vlákně UI. Další informace najdete v tématu [postup: plánování práce ve vláknu uživatelského rozhraní (UI)](http://msdn.microsoft.com/library/32a846a5-d628-4933-907b-4888ff72c663).  
  
## <a name="use-caution-when-waiting-in-delegates-that-are-called-by-parallelinvoke"></a>Při čekání na v delegátech, které jsou volány Parallel.Invoke buďte opatrní  
 V některých případech bude Task Parallel Library vložené úlohy, což znamená, že je spuštěna na úlohu s aktuálně prováděné vlákno. (Další informace najdete v tématu [plánovače úloh](http://msdn.microsoft.com/library/638f8ea5-21db-47a2-a934-86e1e961bf65).) Optimalizace výkonu může dojít k zablokování v určitých případech. Například dvě úlohy mohou spouštět stejného delegáta, kód, který signalizuje, že dojde k události, a poté čeká na signál jiné úlohy. Pokud v druhé úloze je vložená ve stejném vlákně jako první a první přejde do stavu čekání, nikdy v druhé úloze bude moct signalizovat svou událost. Aby nedošlo k tomu, můžete zadat časový limit na operace čekání, nebo použijte explicitní vlákno konstruktory zajistit, aby jeden úkol nelze blokovat dalších.  
  
## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>Nepředpokládejte, že iterace ForEach, pro a ForAll vždy provést paralelní  
 Je důležité mít na paměti, že jednotlivé iterace ve <xref:System.Threading.Tasks.Parallel.For%2A>, <xref:System.Threading.Tasks.Parallel.ForEach%2A> nebo <xref:System.Linq.ParallelEnumerable.ForAll%2A> cykly může, ale není nutné provést paralelně. Proto byste neměli psaní jakéhokoli kódu, který správnost závisí na paralelní provádění iterací nebo provádění iterací v libovolném pořadí. Tento kód je například pravděpodobně dojde k zablokování:  
  
 [!code-csharp[TPL_Pitfalls#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#01)]
 [!code-vb[TPL_Pitfalls#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#01)]  
  
 V tomto příkladu jedna iterace události a všechny ostatní iterace čekat na události. Žádná z čekajících iterací provést až po dokončení nastavení události iterací. Je však možné, že čekajících iterací blokovat všechna vlákna, které se používají ke spouštění paralelní smyčky před událostí iterace dostal příležitost provést. To vede k zablokování – událost iterace se nikdy neprovede a čekající iterace se nikdy probuzení.  
  
 Na konkrétní jeden iterace paralelní smyčky by nikdy čekat na jinou iteraci smyčky pokračovat. Pokud se při plánování iterace sekvenčně, ale v opačném pořadí rozhodne paralelní smyčky, dojde k zablokování.  
  
## <a name="avoid-executing-parallel-loops-on-the-ui-thread"></a>Vyhněte se provádění paralelní smyčky ve vlákně UI  
 Je důležité udržovat reaguje aplikace uživatelské rozhraní (UI). Pokud operace obsahuje dostatek práce vláknem, je pravděpodobně by neměla být spusťte tuto operaci ve vlákně UI.  Místo toho by měla přesměrování zpracování této operace se mají v vlákna na pozadí. Například pokud chcete použít k výpočtu data, která má být vykreslen pak do ovládacího prvku uživatelského rozhraní paralelní smyčky, měli byste zvážit provádění smyčky v rámci instance úlohy, nikoli přímo v obslužné rutině uživatelského rozhraní.  Jenom v případě, že výpočty dokončeny by vám pak zařazování aktualizace uživatelského rozhraní zpět vlákna uživatelského rozhraní.  
  
 Pokud spustíte paralelní smyčky vlákna uživatelského rozhraní, je potřeba zabránit aktualizace ovládacích prvků uživatelského rozhraní z v rámci smyčky. Pokus o aktualizaci uživatelského rozhraní ovládacích prvků z paralelní smyčky, který provádí ve vlákně UI může vést k poškození stavu, výjimky, zpožděné aktualizace a dokonce zablokování, v závislosti na tom, jak je vyvolána aktualizace uživatelského rozhraní. V následujícím příkladu blokuje paralelní smyčky vlákna uživatelského rozhraní, ve kterém je spuštěn, dokud nebudou dokončeny všechny iterace. Ale pokud iterace smyčky běží na vlákna na pozadí (jako <xref:System.Threading.Tasks.Parallel.For%2A> může provádět), volání Invoke způsobí, že zprávu k odeslání do vlákna uživatelského rozhraní a čeká na zpracování této zpráva. Vzhledem k tomu, že vlákna uživatelského rozhraní je blokovaný, spuštěná <xref:System.Threading.Tasks.Parallel.For%2A>, nikdy nelze zpracovat zprávu a blokování vlákna uživatelského rozhraní.  
  
 [!code-csharp[TPL_Pitfalls#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#02)]
 [!code-vb[TPL_Pitfalls#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#02)]  
  
 Následující příklad ukazuje, jak, aby nedošlo k zablokování spuštěním smyčky uvnitř instance úlohy. Vlákna uživatelského rozhraní není blokován bránou smyčky a může být zpráva zpracována.  
  
 [!code-csharp[TPL_Pitfalls#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#03)]
 [!code-vb[TPL_Pitfalls#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#03)]  
  
## <a name="see-also"></a>Viz také  
 [Paralelní programování](../../../docs/standard/parallel-programming/index.md)  
 [Potenciální nástrahy PLINQ](../../../docs/standard/parallel-programming/potential-pitfalls-with-plinq.md)  
 [Vzory pro paralelní programování: Princip fungování a způsob použití paralelní vzory s rozhraním .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222)
