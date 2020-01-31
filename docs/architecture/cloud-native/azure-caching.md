---
title: Ukládání do mezipaměti v nativní aplikaci cloudu
description: Přečtěte si o strategiích ukládání do mezipaměti v cloudové nativní aplikaci.
author: robvet
ms.date: 01/22/2020
ms.openlocfilehash: 2da61a01fc53233d1934df813fcba3b91a495c43
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794966"
---
# <a name="caching-in-a-cloud-native-app"></a>Ukládání do mezipaměti v nativní aplikaci cloudu

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Výhody ukládání do mezipaměti se dobře rozumí. Technika funguje tak, že dočasně kopíruje často používaná data z back-endu úložiště dat do *rychlého úložiště* , které se nachází blíže k aplikaci. Ukládání do mezipaměti je často implementováno tam, kde...

- Data zůstávají relativně statická.
- Přístup k datům je pomalý, zejména v porovnání s rychlostí paměti.
- Data podléhají vysoké míře sporů.

## <a name="why"></a>Proč?

Jak je popsáno v tématu [pokyny k ukládání do mezipaměti Microsoftu](https://docs.microsoft.com/azure/architecture/best-practices/caching), ukládání do mezipaměti může zvýšit výkon, škálovatelnost a dostupnost jednotlivých mikroslužeb a systému jako celku. Snižuje latenci a spory při zpracování velkých objemů souběžných požadavků do úložiště dat. Po zvýšení objemu dat a počtu uživatelů se stane větší výhoda ukládání do mezipaměti.

Ukládání do mezipaměti je nejúčinnější, když klient opakovaně čte data, která jsou neměnná nebo se nečasto mění. Příklady zahrnují referenční informace, jako jsou informace o produktech a cenách, nebo sdílené statické prostředky, které je náročné vytvořit.

I když by mikroslužby měly být bezstavové, distribuovaná mezipaměť může podporovat souběžný přístup k datům stavu relace, když je to nezbytně nutné.

Zvažte také ukládání do mezipaměti, aby se předešlo opakovaným výpočtům. Pokud operace transformuje data nebo provede složitý výpočet, uloží výsledek pro následné požadavky do mezipaměti.

## <a name="caching-architecture"></a>Architektura pro ukládání do mezipaměti

Nativní cloudové aplikace obvykle implementují distribuovanou architekturu ukládání do mezipaměti. Mezipaměť je hostována jako cloudová [Služba](./definition.md#backing-services), která je oddělená od mikroslužeb. Obrázek 5-20 ukazuje architekturu.

![Ukládání do mezipaměti v nativní aplikaci v cloudu](media/caching-in-a-cloud-native-app.png)

**Obrázek 5-19**: ukládání do mezipaměti v nativní aplikaci v cloudu

Na předchozím obrázku si všimněte, jak je mezipaměť nezávislá a je sdílena mikroslužbami. V tomto scénáři je mezipaměť vyvolaná [bránou rozhraní API](./front-end-communication.md). Jak je popsáno v kapitole 4, brána slouží jako front-end pro všechny příchozí požadavky. Distribuovaná mezipaměť zvyšuje odezvu systému tím, že vrací data uložená v mezipaměti, kdykoli je to možné. Kromě toho oddělení mezipaměti od služeb umožňuje, aby se mezipaměť nezávisle nastavila nebo vyčerpala, aby se splnily zvýšené nároky na provoz.

Obrázek představuje společný vzor pro ukládání do mezipaměti, který je známý jako model doplňování [mezipaměti](https://docs.microsoft.com/azure/architecture/patterns/cache-aside). U příchozího požadavku nejprve vydáte dotaz na mezipaměť (krok \#1) pro odpověď. Pokud se najde, data se vrátí hned. Pokud data v mezipaměti neexistují (označovaná jako [neúspěšný mezipaměť](https://www.techopedia.com/definition/6308/cache-miss)), načte se z místní databáze v rámci služby pro příjem dat (krok \#2). Pak se zapíše do mezipaměti pro budoucí požadavky (krok \#3) a vrátí se volajícímu. K pravidelnému vyřazení dat uložených v mezipaměti musí být nutná péče, aby systém zůstal včas a konzistentní.

Jak sdílená mezipaměť roste, může být výhodné rozdělit data do oddílů napříč více uzly. Díky tomu může pomoci minimalizovat spory a zlepšit škálovatelnost. Celá řada služeb ukládání do mezipaměti podporuje možnost dynamického přidávání a odebírání uzlů a vyrovnávání dat napříč oddíly. Tento přístup obvykle zahrnuje clusteringu. Clustering zpřístupňuje kolekci federovaných uzlů jako bezproblémové a jedinou mezipaměť. Interně se ale data přenáší napříč uzly po předdefinované distribuční strategii, která zatížení rovnoměrně vyrovnává.

## <a name="azure-cache-for-redis"></a>Azure Cache for Redis

[Azure cache pro Redis](https://azure.microsoft.com/services/cache/) je zabezpečená služba pro ukládání dat do mezipaměti a službu Zprostředkovatel zasílání zpráv, která je plně spravovaná Microsoftem. Využito jako nabídka platformy jako služby (PaaS), poskytuje přístup k datům s vysokou propustností a nízkou latencí. Služba je přístupná pro jakoukoli aplikaci v rámci Azure i mimo ni.

Služba Azure cache for Redis spravuje přístup k serverům Redis Open Source hostovaným v datových centrech Azure. Služba funguje jako fasáda, která poskytuje správu, řízení přístupu a zabezpečení. Služba nativně podporuje bohatou sadu datových struktur, včetně řetězců, hodnot hash, seznamů a sad. Pokud už vaše aplikace používá Redis, bude pro Redis fungovat tak, jak je s mezipamětí Azure cache.

Mezipaměť Azure pro Redis je větší než server mezipaměti Simple cache. Může podporovat několik scénářů pro vylepšení architektury mikroslužeb:

- Úložiště dat v paměti
- Distribuovaná databáze, která není relační
- Zprostředkovatel zpráv
- Konfigurační server nebo server zjišťování
  
V případě pokročilých scénářů lze kopii dat uložených v mezipaměti [zachovat na disku](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-how-to-premium-persistence). Pokud závažná událost zakáže primární i mezipaměť repliky, mezipaměť se znovu vytvoří z posledního snímku.

Azure Redis Cache je k dispozici v rámci několika předdefinovaných konfigurací a cenových úrovní.  [Úroveň Premium](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-premium-tier-intro) nabízí mnoho funkcí na podnikové úrovni, jako je clustering, trvalost dat, geografická replikace a izolace virtuální sítě.

>[!div class="step-by-step"]
>[Předchozí](relational-vs-nosql-data.md)
>[Další](elastic-search-in-azure.md)
