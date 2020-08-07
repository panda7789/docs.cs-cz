---
title: Pracovní stanice vs. shromažďování paměti serveru (GC)
description: Přečtěte si o uvolňování paměti pracovních stanic a serverů v .NET.
ms.date: 04/21/2020
helpviewer_keywords:
- garbage collection, workstation
- garbage collection, server
- workstation garbage collection
- server garbage collection
ms.openlocfilehash: 640b5f42c1f841c2537284e4721e827248e3d300
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87917006"
---
# <a name="workstation-and-server-garbage-collection"></a>Uvolnění paměti pracovní stanice a serveru

Systém uvolňování paměti je samoobslužné ladění a může fungovat v nejrůznějších scénářích. V závislosti na charakteristikách úlohy však můžete [nastavit typ uvolňování paměti](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection) . CLR poskytuje následující typy uvolňování paměti:

- Uvolňování paměti pracovní stanice (GC), která je určená pro klientské aplikace. Jedná se o výchozí charakter GC pro samostatné aplikace. U hostovaných aplikací, například těch, které hostuje ASP.NET, hostitel určí výchozí charakter GC.

  Uvolňování paměti pracovní stanice může být souběžné nebo nesouběžné. Souběžné uvolňování paměti (nebo *pozadí*) umožňuje spravovaným vláknům pokračovat v operacích během uvolňování paměti. [Kolekce uvolnění paměti na pozadí](background-gc.md) nahrazuje [souběžné uvolňování paměti](background-gc.md#concurrent-garbage-collection) v .NET Framework 4 a novějších verzích.

- Uvolňování paměti serveru, které je určeno pro serverové aplikace, které vyžadují vysokou propustnost a škálovatelnost.

  - V rozhraní .NET Core může být uvolňování paměti serveru nesouběžné nebo na pozadí.

  - V .NET Framework 4,5 a novějších verzích může být uvolňování paměti serveru nesouběžné nebo na pozadí. V .NET Framework 4 a předchozích verzích je uvolňování paměti serveru nesouběžné.

Následující ilustrace znázorňuje vyhrazená vlákna, která provádějí uvolňování paměti na serveru:

![Vlákna uvolňování paměti serveru](media/gc-server.png)

## <a name="performance-considerations"></a>Otázky výkonu

### <a name="workstation-gc"></a>GC pracovní stanice

Následují požadavky na vlákna a výkon pro uvolňování paměti pracovních stanic:

- Kolekce probíhá na uživatelském vlákně, které aktivovalo uvolňování paměti a zůstává ve stejné prioritě. Vzhledem k tomu, že se uživatelské vlákna obvykle spouští s normální prioritou, musí být systém uvolňování paměti (který běží na normální prioritní vlákně) s ostatními vlákny pro čas procesoru. (Vlákna, která spouštějí nativní kód, nejsou pozastavena buď na serveru, nebo v uvolnění paměti pracovní stanice.)

- Uvolňování paměti pracovní stanice se vždycky používá v počítači, který má jenom jeden procesor, bez ohledu na [nastavení konfigurace](../../core/run-time-config/garbage-collector.md#workstation-vs-server).

### <a name="server-gc"></a>Uvolňování paměti serveru

Následují požadavky na vlákna a výkon pro uvolňování paměti serveru:

- Kolekce probíhá ve více vyhrazených vláknech, které jsou spuštěny na `THREAD_PRIORITY_HIGHEST` úrovni priority.

- Halda a vyhrazené vlákno pro provádění uvolňování paměti jsou k dispozici pro každý procesor a haldy jsou shromažďovány ve stejnou dobu. Každá halda obsahuje malou haldu objektů a velké haldy objektů a ke všem haldám je možné přistupovat pomocí uživatelského kódu. Objekty na různých haldách mohou vzájemně odkazovat.

- Vzhledem k tomu, že více vláken uvolňování paměti současně spolupracuje, je uvolňování paměti serveru rychlejší než uvolnění paměti pracovní stanice ve stejné velikosti haldy.

- Uvolňování paměti serveru má často větší velikost segmentů. Toto je však pouze generalizace: velikost segmentu je specifická pro konkrétní implementaci a může se změnit. Při ladění aplikace nevytvářejte předpoklady o velikosti segmentů přidělených systémem uvolňování paměti.

- Uvolňování paměti serveru může být náročné na prostředky. Představte si například, že v počítači, který má čtyři procesory, je spuštěno 12 procesů, které používají GC serveru. Pokud se u všech procesů vyskytne uvolňování paměti ve stejnou dobu, může to narušit navzájem, protože ve stejném procesoru bylo naplánováno 12 vláken. Pokud jsou procesy aktivní, není vhodné, abyste je používali při použití GC serveru.

Pokud používáte stovky instancí aplikace, zvažte použití uvolňování paměti pracovní stanice se zakázaným souběžným uvolňováním paměti. Výsledkem bude méně přepínání kontextu, což může zlepšit výkon.

## <a name="see-also"></a>Viz také

- [Uvolňování paměti na pozadí](background-gc.md)
- [Možnosti konfigurace běhu pro uvolňování paměti](../../core/run-time-config/garbage-collector.md)
