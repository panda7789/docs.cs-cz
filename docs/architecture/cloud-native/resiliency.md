---
title: Odolnost nativního cloudu
description: Architekt cloudových nativních aplikací .NET pro Azure | Nativní odolnost cloudu
ms.date: 06/30/2019
ms.openlocfilehash: 680542abc5d8c43c577321d5ae834f0a13290da3
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184839"
---
# <a name="cloud-native-resiliency"></a>Odolnost nativního cloudu

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Odolnost proti chybám je schopnost systému reagovat na selhání a pořád zůstává funkční. Nejedná se o předcházení selhání. Ale jedná se o přijetí této chyby v cloudových systémech a sestavení vaší aplikace, která na ni reaguje. Koncovým cílem odolnosti proti chybám je vrácení aplikace do plně funkčního stavu po selhání.

Na rozdíl od tradičních aplikací monolitické, kde se všechno souběžně používá v jednom procesu, nativní systémy pro Cloud využívají distribuovanou architekturu, jak je znázorněno na obrázku 6-1:

![Distribuované cloudové prostředí – nativní](./media/distributed-cloud-native-environment.png)

**Obrázek 6-1.** Distribuované cloudové prostředí – nativní

Na předchozím obrázku si všimněte, že každý klient, mikroslužba a cloudová [Služba](https://12factor.net/backing-services) se spouští jako samostatný proces, který běží na různých serverech, a to prostřednictvím síťových volání.

Co by to stalo špatné?

- Neočekávaná [latence sítě](https://www.techopedia.com/definition/8553/network-latency).
- [Přechodné chyby](https://docs.microsoft.com/azure/architecture/best-practices/transient-faults) (dočasné chyby připojení k síti).
- Blokuje dlouhodobě běžící synchronní operace.
- Hostitelský proces, u kterého došlo k chybě a probíhá restartování nebo přesunutí.
- Přetížená mikroslužba, která nemůže reagovat po krátkou dobu.
- DevOps operace, jako je například operace aktualizace nebo škálování.
- Operace nástroje Orchestrator, jako je například přesunutí služby z jednoho uzlu do jiného.
- Selhání hardwaru z komoditního hardwaru.

Při nasazování distribuovaných služeb do cloudové infrastruktury se faktory z předchozího seznamu stanou velmi reálné a Vy musíte architekt a vývoj defensively, abyste s nimi mohli pracovat.

V malém distribuovaném systému bude selhání méně časté, ale při horizontálním navýšení kapacity můžete očekávat větší množství těchto potíží s bodem, kde se částečné selhání změní do normálního provozu.

Proto musí být vaše aplikace a infrastruktura odolné. V následujících částech si probereme techniky obrannou linií, které můžete přidat do své aplikace a integrované funkce cloudu, které vám pomůžou s odrážkami v uživatelském prostředí.

>[!div class="step-by-step"]
>[Předchozí](azure-data-storage.md)
>[Další](application-resiliency-patterns.md)
