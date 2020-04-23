---
title: Uvolňování paměti na pozadí
description: Další informace o uvolňování paměti na pozadí v rozhraní .NET a o tom, jak se liší v uvolňování paměti pracovní stanice a serveru.
ms.date: 04/21/2020
helpviewer_keywords:
- garbage collection, background
- background garbage collection
ms.openlocfilehash: dcb1d348e679e07646273b8fbc4ea29b44ee4974
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82103560"
---
# <a name="background-garbage-collection"></a>Uvolňování paměti na pozadí

V uvolňování paměti na pozadí (GC) dočasné generace (0 a 1) jsou shromažďovány podle potřeby, zatímco probíhá kolekce generace 2. Uvolňování paměti na pozadí se provádí na jednom nebo více vyhrazených vláknech v závislosti na tom, zda je to pozadí nebo server GC a platí pouze pro kolekce generace 2.

Uvolnění paměti na pozadí je ve výchozím nastavení povoleno. Může být povolena nebo zakázána nastavením [konfigurace gcConcurrent](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) v aplikacích rozhraní .NET Framework nebo [nastavenísystem.GC.Concurrent](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent) v aplikacích .NET Core.

> [!NOTE]
> Uvolňování paměti na pozadí nahrazuje [souběžné uvolňování paměti](#concurrent-garbage-collection) a je k dispozici v rozhraní .NET Framework 4 a novějších verzích. V rozhraní .NET Framework 4 je podporována pouze pro uvolňování paměti *pracovní stanice.* Počínaje rozhraním .NET Framework 4.5 je k dispozici uvolňování paměti na pozadí pro uvolňování paměti *pracovní stanice* i *serveru.*

Kolekce na dočasné generace během uvolňování paměti na pozadí se označuje jako uvolňování paměti *popředí.* Dojde-li k uvolnění paměti v popředí, jsou pozastavena všechna spravovaná vlákna.

Pokud probíhá uvolňování paměti na pozadí a v generaci 0 jste přidělili dostatek objektů, clr provádí generování 0 nebo generace 1 uvolňování paměti na popředí. Vyhrazené vlákno uvolňování paměti na pozadí kontroluje v častých bezpečných bodech k určení, zda existuje požadavek na uvolnění paměti v popředí. Pokud existuje, kolekce pozadí pozastaví sám tak, aby může dojít k uvolňování paměti popředí. Po dokončení uvolňování paměti na popředí, vyhrazené podprocesy uvolňování paměti na pozadí a vlákna uživatele pokračovat.

Uvolňování paměti na pozadí odebere omezení přidělení uložená souběžným uvolňováním paměti, protože dočasné uvolnění paměti může nastat během uvolňování paměti na pozadí. Uvolňování paměti na pozadí může odebrat nevrácené objekty v dočasných generacích. Může také rozbalit haldy v případě potřeby během uvolnění paměti generace 1.

## <a name="background-workstation-vs-server-gc"></a>Pracovní stanice na pozadí vs. server GC

Počínaje rozhraním .NET Framework 4.5 je pro server GC k dispozici uvolňování paměti na pozadí. Gc na pozadí je výchozí režim pro uvolnění paměti serveru.

Uvolňování paměti serveru na pozadí funguje podobně jako uvolňování paměti pracovní stanice na pozadí, ale existuje několik rozdílů:

- Uvolňování paměti pracovní stanice na pozadí používá jedno vyhrazené vlákno uvolňování paměti na pozadí, zatímco uvolňování paměti serveru na pozadí používá více vláken. Obvykle je vyhrazené vlákno pro každý logický procesor.

- Na rozdíl od vlákna uvolňování paměti na pozadí pracovní stanice nejsou časový mj.

Následující obrázek znázorňuje uvolňování paměti *pracovní stanice* na pozadí provedené v samostatném vyhrazeném vlákně:

![Uvolňování paměti pracovní stanice na pozadí](./media/fundamentals/background-workstation-garbage-collection.png)

Následující obrázek znázorňuje uvolňování paměti *serveru* na pozadí prováděné v samostatných vyhrazených vláknech:

![Uvolnění paměti serveru na pozadí](./media/fundamentals/background-server-garbage-collection.png)

## <a name="concurrent-garbage-collection"></a>Souběžné uvolňování paměti

> [!TIP]
> Tento oddíl se vztahuje na:
>
> - Rozhraní .NET Framework 3.5 a starší pro uvolňování paměti pracovní stanice
> - Rozhraní .NET Framework 4 a starší pro uvolnění paměti serveru
>
> Souběžné nesmysly jsou nahrazeny uvolňováním paměti na pozadí v novějších verzích.

V uvolňování paměti pracovní stanice nebo serveru můžete [povolit souběžné uvolňování paměti](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md), které umožňuje souběžné spuštění vláken s vyhrazeným vláknem, které provádí uvolňování paměti po většinu doby trvání kolekce. Tato možnost ovlivňuje pouze uvolňování paměti v generaci 2; generace 0 a 1 jsou vždy nesouběžné, protože se rychle dokončí.

Souběžné uvolňování paměti umožňuje interaktivní masy lépe reagovat minimalizací pauzy pro kolekci. Spravovaná vlákna mohou pokračovat ve většině času při spuštění souběžného vlákna uvolňování paměti. To má za následek kratší pauzy při uvolňování paměti dochází.

Souběžné uvolňování paměti se provádí ve vyhrazeném vlákně. Ve výchozím nastavení clr spustí uvolňování paměti pracovní stanice s souběžným uvolňováním paměti povoleno v počítačích s jedním i více procesory.

Následující obrázek znázorňuje souběžné uvolňování paměti prováděné v samostatném vyhrazeném vlákně.

![Souběžná vlákna uvolňování paměti](./media/gc-concurrent.png)

## <a name="see-also"></a>Viz také

- [Uvolňování paměti pracovní stanice a serveru](workstation-server-gc.md)
- [Možnosti konfigurace za běhu pro uvolňování paměti](../../core/run-time-config/garbage-collector.md)
