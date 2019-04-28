---
title: Vlákna a dělení na vlákna
ms.date: 11/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET]
- threading [.NET], multiple threads
ms.assetid: 5baac3aa-e603-4fa6-9f89-0f2c1084e6b1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 095bd92921c9cd54d3a7d97ed07b35526b85c57f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61682986"
---
# <a name="threads-and-threading"></a>Vlákna a dělení na vlákna

Multithreading můžete zvýšit rychlost reakce aplikace a, pokud je aplikace spuštěná v systému s více procesory nebo s více jádry, zvýšit jeho propustnost.

## <a name="processes-and-threads"></a>Procesy a vlákna

A *procesu* je prováděnému programu. Operační systém používá procesy pro oddělení aplikací, které se spouští. A *vlákno* je základní jednotkou, ke kterému operační systém přiděluje čas procesoru. Každé vlákno má [Priorita plánování](scheduling-threads.md) a udržuje sadu struktury systému použije k uložení kontext vlákna při pozastavení provádění vlákna. Kontext vlákna obsahuje všechny informace, které vlákno je potřeba bez problémů pokračovat v provádění, včetně sady registrech procesoru a zásobníku vlákna. V rámci procesu můžete spustit více vláken. Všechna vlákna procesu sdílet jeho virtuální adresní prostor. Vlákno můžete provést kteroukoli část kódu programu, včetně částí aktuálně prováděné jiné vlákno.

> [!NOTE]
> Rozhraní .NET Framework poskytuje způsob, jak izolovat aplikace v rámci procesu s použitím *aplikačních doménách*. (Aplikační domény nejsou k dispozici v rozhraní .NET Core.) Další informace najdete v tématu [domény aplikace a vlákna](../../framework/app-domains/application-domains.md#application-domains-and-threads) část [aplikačních doménách](../../framework/app-domains/application-domains.md) článku.

Ve výchozím nastavení, spuštění aplikace .NET s jedním vláknem, často označované jako *primární* vlákna. To však můžete vytvořit další vlákna ke spouštění kódu vytvořeného paralelně nebo současně primárnímu vláknu. Tato vlákna se často nazývají *pracovního procesu* vlákna.

## <a name="when-to-use-multiple-threads"></a>Použití více vláken

Zvýšit rychlost reakce aplikace a chcete využít výhod systému s více procesory nebo s více jádry chcete zvýšit propustnost aplikace, používejte více vláken.

Vezměte v úvahu desktopová aplikace, ve kterém primární vlákno je zodpovědný za prvky uživatelského rozhraní a reaguje na akce uživatele. Použití pracovních vláken provádět časově náročná operace, které, v opačném případě by zabírat primární vlákno a ujistěte se, uživatelské rozhraní přestane reagovat. Také můžete použít jedno vyhrazené vlákno pro komunikace sítě nebo zařízení rychleji reagující na příchozí zprávy nebo události.

Pokud váš program provádí operace, které lze provést paralelně, celková doba spuštění lze snížit pomocí provádí tyto operace v oddělených vláknech a spuštění programu v systému s více procesory nebo s více jádry. V systému, použití více vláken může zvýšit propustnost spolu s vyšší rychlost odezvy.

## <a name="how-to-use-multithreading-in-net"></a>Jak používat multithreading v .NET

Od verze rozhraní .NET Framework 4, je doporučeným způsobem, jak používat multithreading používat [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md) a [paralelní LINQ (PLINQ)](../parallel-programming/parallel-linq-plinq.md). Další informace najdete v tématu [paralelní programování](../parallel-programming/index.md).

TPL a PLINQ využívají <xref:System.Threading.ThreadPool> vlákna. <xref:System.Threading.ThreadPool?displayProperty=nameWithType> Třída poskytuje aplikace .NET pomocí fondu pracovních vláken. Můžete použít také vláken fondu vláken. Další informace najdete v tématu [spravovaný fond vláken](the-managed-thread-pool.md).

V poslední, můžete použít <xref:System.Threading.Thread?displayProperty=nameWithType> třídu, která představuje spravované vlákno. Další informace najdete v tématu [použití vláken a dělení na vlákna](using-threads-and-threading.md).

Více vláken může být nutné pro přístup ke sdíleným prostředkům. Mějte nepoškozeným stavu prostředku a nedošlo ke konfliktům časování, musíte synchronizovat vlákno přístup k němu. Můžete také chtít koordinovat interakce více vláken. .NET poskytuje celou řadu typů, které slouží k synchronizaci přístupu ke sdíleným prostředkům nebo koordinovat interakce vlákna. Další informace najdete v tématu [přehled primitiv synchronizace](overview-of-synchronization-primitives.md).

Zpracování výjimek ve vláknech. Neošetřené výjimky ve vláknech obecně ukončit proces. Další informace najdete v tématu [výjimky ve spravovaných vláknech](exceptions-in-managed-threads.md).

## <a name="see-also"></a>Viz také:

- [Práce s vlákny funkce a objekty](threading-objects-and-features.md)
- [Dělení na spravovaná vlákna osvědčené postupy](managed-threading-best-practices.md)
- [Paralelní zpracování, souběžnost a asynchronní programování v rozhraní .NET](../parallel-processing-and-concurrency.md)
- [Informace o procesech a vláknech](/windows/desktop/procthread/about-processes-and-threads)