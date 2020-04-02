---
title: Závity a závity
ms.date: 11/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET]
- threading [.NET], multiple threads
ms.assetid: 5baac3aa-e603-4fa6-9f89-0f2c1084e6b1
ms.openlocfilehash: e29c131f8459179d0641ac9a0cb8234fbba0e7d0
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588434"
---
# <a name="threads-and-threading"></a>Závity a závity

Multithreading umožňuje zvýšit odezvu aplikace a pokud vaše aplikace běží na víceprocesorovém nebo vícejádrovém systému, zvýšit její propustnost.

## <a name="processes-and-threads"></a>Procesy a vlákna

*Proces* je vykonávající program. Operační systém používá procesy k oddělení aplikací, které jsou spouštěny. *Podproces* je základní jednotka, které operační systém přiděluje čas procesoru. Každé vlákno má [prioritu plánování](scheduling-threads.md) a udržuje sadu struktur, které systém používá k uložení kontextu vlákna při pozastavení provádění vlákna. Kontext vlákna obsahuje všechny informace, které vlákno potřebuje k bezproblémovému obnovení provádění, včetně sady registrů procesoru a zásobníku vlákna. V kontextu procesu lze spustit více vláken. Všechna vlákna procesu sdílejí jeho virtuální adresní prostor. Podproces může spustit libovolnou část kódu programu, včetně částí, které jsou aktuálně spouštěny jiným vláknem.

> [!NOTE]
> Rozhraní .NET Framework poskytuje způsob, jak izolovat aplikace v rámci procesu s použitím *aplikačních domén*. (Aplikační domény nejsou k dispozici na .NET Core.) Další informace naleznete v části [Aplikační domény a vlákna](../../framework/app-domains/application-domains.md#application-domains-and-threads) v článku [Aplikační domény.](../../framework/app-domains/application-domains.md)

Ve výchozím nastavení je program .NET spuštěn s jedním vláknem, často nazývaným *primární* vlákno. Může však vytvořit další vlákna pro paralelní nebo souběžné spuštění kódu s primárním vláknem. Tato vlákna se často nazývají *pracovní* vlákna.

## <a name="when-to-use-multiple-threads"></a>Kdy použít více vláken

Pomocí více vláken zvýšit odezvu aplikace a využít výhod víceprocesorového nebo vícejádrového systému ke zvýšení propustnosti aplikace.

Zvažte desktopovou aplikaci, ve které je primární vlákno zodpovědné za prvky uživatelského rozhraní a reaguje na akce uživatele. Pracovní podprocesy slouží k provádění časově náročných operací, které by jinak zabíraly primární vlákno a uživatelské rozhraní by nereagovalo. Můžete také použít vyhrazené vlákno pro komunikaci v síti nebo zařízení, abyste lépe reagovali na příchozí zprávy nebo události.

Pokud program provádí operace, které lze provést paralelně, může být celková doba provádění snížena provedením těchto operací v samostatných vláknech a spuštěním programu na víceprocesorovém nebo vícejádrovém systému. V takovém systému může použití multithreadingu zvýšit propustnost spolu se zvýšenou odezvou.

## <a name="how-to-use-multithreading-in-net"></a>Použití multithreadingu v rozhraní .NET

Počínaje rozhraním .NET Framework 4 je doporučeným způsobem využití multithreadingu použití [paralelní knihovny úloh (TPL)](../parallel-programming/task-parallel-library-tpl.md) a [paralelních LINQ (PLINQ).](../parallel-programming/introduction-to-plinq.md) Další informace naleznete [v tématu Paralelní programování](../parallel-programming/index.md).

TPL i PLINQ spoléhají <xref:System.Threading.ThreadPool> na závity. Třída <xref:System.Threading.ThreadPool?displayProperty=nameWithType> poskytuje aplikaci .NET s fondem pracovních podprocesů. Můžete také použít vlákna fondu vláken. Další informace naleznete [v tématu Fond spravovaných vláken](the-managed-thread-pool.md).

Nakonec můžete použít třídu, <xref:System.Threading.Thread?displayProperty=nameWithType> která představuje spravované vlákno. Další informace naleznete [v tématu Použití vláken a vláken](using-threads-and-threading.md).

Pro přístup ke sdílenému prostředku může být nutné získat více vláken. Chcete-li zachovat prostředek v nepoškozeném stavu a vyhnout se časovým podmínkám, je nutné synchronizovat přístup podprocesu k němu. Můžete také koordinovat interakci více vláken. Rozhraní .NET poskytuje řadu typů, které můžete použít k synchronizaci přístupu ke sdílenému prostředku nebo ke koordinaci interakce podprocesu. Další informace naleznete v [tématu Přehled synchronizačních primitiv](overview-of-synchronization-primitives.md).

Zpracovat výjimky ve vláknech. Neošetřené výjimky ve vláknech obecně ukončit proces. Další informace naleznete [v tématu Výjimky ve spravovaných vláknech](exceptions-in-managed-threads.md).

## <a name="see-also"></a>Viz také

- [Dělení objektů a funkcí na vlákna](threading-objects-and-features.md)
- [Osvědčené postupy spravovaného podprocesu](managed-threading-best-practices.md)
- [Paralelní zpracování, souběžnost a asynchronní programování v rozhraní .NET](../parallel-processing-and-concurrency.md)
- [O procesech a vláknech](/windows/desktop/procthread/about-processes-and-threads)
