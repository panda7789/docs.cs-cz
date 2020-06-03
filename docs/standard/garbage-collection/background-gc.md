---
title: Uvolňování paměti na pozadí
description: Přečtěte si o uvolňování paměti na pozadí v rozhraní .NET a o tom, jak se liší v pracovní stanici a uvolňování paměti serveru.
ms.date: 04/21/2020
helpviewer_keywords:
- garbage collection, background
- background garbage collection
ms.openlocfilehash: 8134c0af55d74e57dcfce8c7174265b8c9902feb
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/03/2020
ms.locfileid: "84307069"
---
# <a name="background-garbage-collection"></a>Uvolňování paměti na pozadí

V uvolňování paměti na pozadí (GC) jsou dočasné generace (0 a 1) shromažďovány podle potřeby, zatímco probíhá shromažďování 2. generace. Uvolňování paměti na pozadí se provádí v jednom nebo více vyhrazených vláknech v závislosti na tom, zda se jedná o pozadí nebo server GC, a vztahuje se pouze na kolekce 2. generace.

Uvolňování paměti na pozadí je ve výchozím nastavení povolené. Dá se zapnout nebo vypnout s nastavením konfigurace [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) v aplikacích .NET Framework nebo v nastavení [System. GC. souběžné](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent) v aplikacích .NET Core.

> [!NOTE]
> Uvolňování paměti na pozadí nahrazuje [souběžné uvolňování paměti](#concurrent-garbage-collection) a je k dispozici v .NET Framework 4 a novějších verzích. V .NET Framework 4 se podporuje jenom pro uvolňování paměti *pracovní stanice* . Počínaje .NET Framework 4,5 se uvolňování paměti na pozadí dá použít jak pro *pracovní stanice* , tak pro uvolňování paměti *serveru* .

Kolekce na dočasných generacích během uvolňování paměti na pozadí je známá jako uvolnění paměti na *popředí* . Když dojde k uvolnění paměti na popředí, pozastaví se všechna spravovaná vlákna.

Když probíhá uvolňování paměti na pozadí a přidělíte dostatek objektů v generaci 0, modul CLR provede uvolňování paměti od generace 0 nebo 1. generace v popředí. Vyhrazené vlákno uvolňování paměti na pozadí kontroluje v častých bezpečných bodech, aby bylo možné zjistit, zda existuje požadavek na uvolnění paměti na popředí. V takovém případě se kolekce na pozadí odblokuje, aby mohlo dojít k uvolnění paměti na popředí. Po dokončení uvolňování paměti na popředí se vyhradí vyhrazená vlákna uvolňování paměti na pozadí a obnovení uživatelských vláken.

Uvolňování paměti na pozadí odebírá omezení přidělení, která jsou vynucená souběžným uvolňováním paměti, protože dočasné uvolňování paměti mohou nastat během uvolňování paměti na pozadí. Uvolňování paměti na pozadí může odebrat nedoručené objekty v dočasných generacích. Může také rozšířit haldu v případě potřeby během uvolňování paměti 1. generace.

## <a name="background-workstation-vs-server-gc"></a>Pracovní stanice na pozadí a uvolňování paměti serveru

Počínaje .NET Framework 4,5 je pro uvolňování paměti na pozadí k dispozici uvolňování paměti na pozadí. GC na pozadí je výchozím režimem pro uvolňování paměti serveru.

Uvolňování paměti serveru na pozadí funguje podobně jako uvolnění paměti pracovní stanice na pozadí, ale existuje několik rozdílů:

- Uvolňování paměti pracovní stanice na pozadí používá jedno vyhrazené vlákno uvolňování paměti na pozadí, zatímco uvolňování paměti serveru na pozadí používá více vláken. Obvykle existuje vyhrazené vlákno pro každý logický procesor.

- Na rozdíl od vlákna uvolňování paměti na pozadí pracovní stanice nevypršel časový limit vláken GC serveru na pozadí.

Následující obrázek znázorňuje uvolnění paměti *pracovní stanice* na pozadí v samostatném vyhrazeném vlákně:

![Uvolňování paměti pracovní stanice na pozadí](media/fundamentals/background-workstation-garbage-collection.png)

Na následujícím obrázku je znázorněno uvolňování paměti *serveru* na pozadí provedené na samostatných vyhrazených vláknech:

![Uvolňování paměti serveru na pozadí](media/fundamentals/background-server-garbage-collection.png)

## <a name="concurrent-garbage-collection"></a>Souběžné uvolňování paměti

> [!TIP]
> Tato část se týká:
>
> - Uvolňování paměti pro pracovní stanice .NET Framework 3,5 a starší
> - .NET Framework 4 a starší pro uvolňování paměti serveru
>
> Souběžné uvolňování paměti je nahrazeno uvolňováním paměti na pozadí v novějších verzích.

V pracovní stanici nebo uvolňování paměti serveru můžete [Povolit souběžné uvolňování paměti](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md), které umožňuje spouštět vlákna souběžně s vyhrazeným vláknem, které provádí uvolňování paměti po většinu doby trvání kolekce. Tato možnost má vliv jenom na uvolňování paměti v generaci 2. generace 0 a 1 jsou vždy nesouběžná, protože dokončí rychlé.

Souběžné uvolňování paměti umožňuje interaktivním aplikacím lépe reagovat tím, že minimalizuje pozastavení kolekce. Spravovaná vlákna mohou i nadále běžet v době, kdy běží souběžné vlákno uvolňování paměti. Výsledkem je kratší pozastavení během uvolňování paměti.

Souběžné uvolňování paměti se provádí ve vyhrazeném vlákně. Ve výchozím nastavení spustí modul CLR uvolňování paměti pracovní stanice s povoleným souběžným uvolňováním paměti na počítačích s jedním procesorem i s více procesory.

Následující ilustrace znázorňuje souběžné uvolňování paměti prováděné na samostatném vyhrazeném vlákně.

![Souběžná vlákna uvolňování paměti](media/gc-concurrent.png)

## <a name="see-also"></a>Viz také

- [Uvolnění paměti pracovní stanice a serveru](workstation-server-gc.md)
- [Možnosti konfigurace běhu pro uvolňování paměti](../../core/run-time-config/garbage-collector.md)
