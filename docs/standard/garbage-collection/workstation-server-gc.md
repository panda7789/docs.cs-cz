---
title: Pracovní stanice vs. server uvolňování paměti (GC)
description: Informace o uvolňování paměti pracovní stanice a serveru v rozhraní .NET.
ms.date: 04/21/2020
helpviewer_keywords:
- garbage collection, workstation
- garbage collection, server
- workstation garbage collection
- server garbage collection
ms.openlocfilehash: 6b8e5f6802e5d44669b95d43d4e897fa4a418512
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82103553"
---
# <a name="workstation-and-server-garbage-collection"></a>Uvolňování paměti pracovní stanice a serveru

Systém uvolňování paměti je samoladný a může pracovat v široké škále scénářů. Můžete však [nastavit typ uvolňování paměti](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection) na základě charakteristik pracovního vytížení. CLR poskytuje následující typy uvolňování paměti:

- Uvolňování paměti pracovní stanice (GC), který je určen pro klientské aplikace. Je to výchozí gc příchuť pro samostatné aplikace. Pro hostované aplikace, například ty, které hostuje ASP.NET, hostitel určuje výchozí gc příchuť.

  Uvolňování paměti pracovní stanice může být souběžné nebo nesouběžné. Souběžné (nebo *pozadí)* uvolňování paměti umožňuje spravovaných podprocesů pokračovat v operacích během uvolňování paměti. [Uvolňování paměti na pozadí](background-gc.md) nahrazuje [souběžné uvolňování paměti](background-gc.md#concurrent-garbage-collection) v rozhraní .NET Framework 4 a novějších verzích.

- Uvolňování paměti serveru, který je určen pro serverové aplikace, které vyžadují vysokou propustnost a škálovatelnost.

  - V .NET Core může být uvolňování paměti serveru nesouběžné nebo na pozadí.

  - V rozhraní .NET Framework 4.5 a novějších verzích může být uvolňování paměti serveru nesouběžné nebo na pozadí. V rozhraní .NET Framework 4 a předchozích verzích je uvolňování paměti serveru nesouběžné.

Následující obrázek znázorňuje vyhrazená vlákna, která provádějí uvolňování paměti na serveru:

![Vlákna uvolňování paměti serveru](./media/gc-server.png)

## <a name="performance-considerations"></a>Otázky výkonu

### <a name="workstation-gc"></a>Pracovní stanice GC

Níže jsou zřetězení a výkon aspekty pro uvolňování paměti pracovní stanice:

- Kolekce dochází ve vlákně uživatele, který spustil uvolňování paměti a zůstává na stejnou prioritu. Vzhledem k tomu, že vlákna uživatele obvykle běží s normální prioritou, systém uvolňování paměti (který běží v normálním vlákně s prioritou) musí soutěžit s jinými vlákny pro čas procesoru. (Vlákna, která spouštějí nativní kód, nejsou pozastavena na serveru ani na uvolnění paměti pracovní stanice.)

- Uvolňování paměti pracovní stanice se vždy používá v počítači, který má pouze jeden procesor, bez ohledu na [nastavení konfigurace](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).

### <a name="server-gc"></a>Server GC

Následují aspekty zřetězení a výkonu pro uvolnění paměti serveru:

- Kolekce se vyskytuje na více vyhrazených `THREAD_PRIORITY_HIGHEST` podprocesů, které jsou spuštěny na úrovni priority.

- Haldy a vyhrazené vlákno k provedení uvolňování paměti jsou k dispozici pro každý procesor a haldy jsou shromažďovány ve stejnou dobu. Každá halda obsahuje haldu malého objektu a haldu velkého objektu a všechny haldy jsou přístupné podle uživatelského kódu. Objekty na různých hromadách mohou odkazovat na sebe navzájem.

- Vzhledem k tomu, že více podprocesů uvolňování paměti spolupracovat, uvolňování paměti serveru je rychlejší než uvolňování paměti pracovní stanice na stejné haldy velikosti.

- Uvolňování paměti serveru má často větší segmenty velikosti. Toje však pouze generalizace: velikost segmentu je specifické pro implementaci a může se změnit. Neprovádělte předpoklady o velikosti segmentů přidělených systémem uvolňování paměti při ladění aplikace.

- Uvolňování paměti serveru může být náročné na prostředky. Představte si například, že existuje 12 procesů, které používají server GC spuštěné v počítači, který má čtyři procesory. Pokud všechny procesy náhodou sbírat odpadky ve stejnou dobu, by zasahovali do sebe, protože by bylo 12 podprocesů naplánovaných na stejném procesoru. Pokud jsou procesy aktivní, není vhodné, aby všechny používaly server GC.

Pokud používáte stovky instancí aplikace, zvažte použití uvolňování paměti pracovní stanice s uvolňování souběžných uvolňování paměti zakázáno. To bude mít za následek méně přepínání kontextu, což může zlepšit výkon.

## <a name="see-also"></a>Viz také

- [Uvolňování paměti na pozadí](background-gc.md)
- [Možnosti konfigurace za běhu pro uvolňování paměti](../../core/run-time-config/garbage-collector.md)
