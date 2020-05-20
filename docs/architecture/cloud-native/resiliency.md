---
title: Odolnost nativní pro cloud
description: Architekt cloudových nativních aplikací .NET pro Azure | Nativní odolnost cloudu
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: f3aa89e3ae21b13a31f65013b59636b3f931553c
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613769"
---
# <a name="cloud-native-resiliency"></a>Odolnost nativní pro cloud

Odolnost proti chybám je schopnost systému reagovat na selhání a pořád zůstává funkční. Nejedná se o předcházení chybám, ale přijímá selhání a sestavuje vaše cloudové nativní služby, aby na ně reagovaly. Chcete se rychle vrátit do plně funkčního stavu.

Na rozdíl od tradičních aplikací monolitické, kde všechno běží společně v jednom procesu, cloudové systémy pro Cloud využívají distribuovanou architekturu, jak je znázorněno na obrázku 6-1:

![Distribuované cloudové prostředí – nativní](./media/distributed-cloud-native-environment.png)

**Obrázek 6-1.** Distribuované cloudové prostředí – nativní

Na předchozím obrázku se každá mikroslužba a cloudová [Služba](https://12factor.net/backing-services) provádí v samostatném procesu v rámci serverové infrastruktury a komunikuje prostřednictvím síťových volání.

Provoz v tomto prostředí musí být citlivý na mnoho různých výzev:

- Neočekávaná latence sítě – čas, kdy se žádost o službu dopravuje na příjemce a zpátky.

- [Přechodné chyby](https://docs.microsoft.com/azure/architecture/best-practices/transient-faults) – krátkodobé chyby připojení k síti

- Zablokování dlouhodobě spuštěnou synchronní operací.

- Hostitelský proces, u kterého došlo k chybě a probíhá restartování nebo přesunutí.

- Přetížená mikroslužba, která nemůže reagovat po krátkou dobu.

- Provozní operace nástroje Orchestrator, jako je například postupná inovace nebo přesunutí služby z jednoho uzlu do jiného.

- Selhání hardwaru.

Cloudové platformy můžou detekovat a zmírnit mnohé z těchto potíží s infrastrukturou. Může se restartovat, škálovat a dokonce znovu distribuovat službu do jiného uzlu.  Abyste ale mohli plně využít této integrované ochrany, musíte navrhnout vaše služby, aby na ně reagovaly a i v tomto dynamickém prostředí.

V následujících částech budeme zkoumat techniky obrannou linií, které vaše služba a spravované cloudové prostředky můžou využít k minimalizaci výpadků a přerušení.

>[!div class="step-by-step"]
>[Předchozí](elastic-search-in-azure.md) 
> [Další](application-resiliency-patterns.md)
