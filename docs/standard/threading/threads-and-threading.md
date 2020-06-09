---
title: Vlákna a dělení na vlákna
description: Přečtěte si o vláknech, jako jsou například procesy & vlákny, kdy použít více vláken, & jak používat multithreading ke zvýšení rychlosti odezvy nebo propustnosti v rozhraní .NET.
ms.date: 11/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET]
- threading [.NET], multiple threads
ms.assetid: 5baac3aa-e603-4fa6-9f89-0f2c1084e6b1
ms.openlocfilehash: b332db80069e18d3b52cd03eef4995eaad3fda7b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84583398"
---
# <a name="threads-and-threading"></a>Vlákna a dělení na vlákna

Multithreading umožňuje zvýšit rychlost odezvy vaší aplikace, a pokud vaše aplikace běží na víceprocesorovém nebo multi-core systému, zvyšte její propustnost.

## <a name="processes-and-threads"></a>Procesy a vlákna

*Proces* je spuštěný program. Operační systém používá procesy k oddělení spuštěných aplikací. *Vlákno* je základní jednotka, do které operační systém přiděluje čas procesoru. Každé vlákno má [prioritu plánování](scheduling-threads.md) a udržuje sadu struktur, kterou systém používá k uložení kontextu vlákna, když je spuštění vlákna pozastaveno. Kontext vlákna zahrnuje všechny informace, které vlákno potřebuje k bezproblémovému pokračování v provádění, včetně sady vláken a zásobníků procesoru. V kontextu procesu lze spustit více vláken. Všechna vlákna v procesu sdílejí svůj virtuální adresní prostor. Vlákno může spouštět libovolnou část kódu programu, včetně částí, které jsou aktuálně spouštěny jiným vláknem.

> [!NOTE]
> .NET Framework poskytuje způsob, jak izolovat aplikace v rámci procesu s použitím *domén aplikací*. (Domény aplikací nejsou k dispozici v rozhraní .NET Core.) Další informace naleznete v části [domény aplikace a vlákna](../../framework/app-domains/application-domains.md#application-domains-and-threads) v článku [domény aplikace](../../framework/app-domains/application-domains.md) .

Ve výchozím nastavení je program .NET spuštěn s jedním vláknem, často se nazývá *primární* vlákno. Může však vytvořit další vlákna pro souběžné a souběžné spouštění kódu s primárním vláknem. Tato vlákna se často nazývají *pracovní* vlákna.

## <a name="when-to-use-multiple-threads"></a>Kdy použít více vláken

Můžete použít více vláken ke zvýšení rychlosti odezvy vaší aplikace a využít více procesorů nebo vícejádrových systémů ke zvýšení propustnosti aplikace.

Vezměte v úvahu desktopovou aplikaci, ve které je primární vlákno zodpovědné za prvky uživatelského rozhraní a reaguje na akce uživatele. Použijte pracovní vlákna k provádění časově náročných operací, které by jinak mohly zabírat primární vlákno a předávat uživatelské rozhraní bez odezvy. Můžete také použít vyhrazené vlákno pro komunikaci sítě nebo zařízení, aby bylo možné lépe reagovat na příchozí zprávy nebo události.

Pokud program provádí operace, které lze provést paralelně, může být celková doba spuštění snížena provedením těchto operací v samostatných vláknech a spuštění programu na víceprocesorovém nebo multi-core systému. V takovém systému může použití multithreadingu zvýšit propustnost spolu se zvýšenou odezvou.

## <a name="how-to-use-multithreading-in-net"></a>Jak používat multithreading v .NET

Počínaje .NET Framework 4 je doporučený způsob, jak využít multithreading, je použít [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md) a [Paralelní LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md). Další informace najdete v tématu [paralelní programování](../parallel-programming/index.md).

TPL i PLINQ spoléhají na <xref:System.Threading.ThreadPool> vlákna. <xref:System.Threading.ThreadPool?displayProperty=nameWithType>Třída poskytuje aplikaci .NET s fondem pracovních vláken. Můžete také použít vlákna fondu vláken. Další informace najdete v tématu [spravovaný fond vláken](the-managed-thread-pool.md).

V poslední době můžete použít <xref:System.Threading.Thread?displayProperty=nameWithType> třídu, která představuje spravované vlákno. Další informace najdete v tématu [použití vláken a vláken](using-threads-and-threading.md).

Přístup ke sdílenému prostředku může vyžadovat více vláken. Aby byl prostředek v nepoškozeném stavu a nedocházelo ke konfliktům časování, musíte k němu synchronizovat přístup k vláknu. Také může být vhodné koordinovat interakci více vláken. Rozhraní .NET poskytuje rozsah typů, které můžete použít k synchronizaci přístupu ke sdílenému prostředku nebo k interakci s vlákny pro koordinaci. Další informace najdete v tématu [Přehled primitiv synchronizace](overview-of-synchronization-primitives.md).

Zpracovává výjimky v vláknech. Neošetřené výjimky v vláknech obvykle ukončí proces. Další informace naleznete v tématu [výjimky ve spravovaných vláknech](exceptions-in-managed-threads.md).

## <a name="see-also"></a>Viz také

- [Dělení objektů a funkcí na vlákna](threading-objects-and-features.md)
- [Osvědčené postupy spravovaného vlákna](managed-threading-best-practices.md)
- [Paralelní zpracování, souběžnost a asynchronní programování v .NET](../parallel-processing-and-concurrency.md)
- [O procesech a vláknech](/windows/desktop/procthread/about-processes-and-threads)
