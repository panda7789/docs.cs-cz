---
title: Spuštění složených aplikací a aplikací založených na mikroslužbách v produkčních prostředích
description: Poznejte klíčové komponenty pro spouštění kontejnerových aplikací v produkčním prostředí
ms.date: 02/15/2019
ms.openlocfilehash: 69df3d39a00b91cbe59c96e5fcab841a60943bcc
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644965"
---
# <a name="run-composed-and-microservices-based-applications-in-production-environments"></a>Spuštění složených aplikací a aplikací založených na mikroslužbách v produkčních prostředích

Aplikace, které sestává z několika mikroslužeb je nutné nasadit do clusterů nástroje orchestrator, abyste zjednodušili složitost nasazení a bylo možné z hlediska IT. Bez clusteru služby orchestrator by bylo obtížné nasadit a horizontální navýšení kapacity aplikace komplexní mikroslužeb.

## <a name="introduction-to-orchestrators-schedulers-and-container-clusters"></a>Úvod do orchestrátorů, plánovače a clustery kontejnerů

Dříve v této e kniha *clustery* a *plánovači* byly představeny jako součást diskuse o softwaru pro architekturu a vývoj. Kubernetes a Service Fabric jsou příklady Docker clusterů. Obě tyto orchestrátory můžete spustit v rámci infrastruktury k dispozici ve službě Microsoft Azure Kubernetes Service.

Když aplikace jsou horizontálním navýšením kapacity napříč více hostitelských systémech, stane se atraktivní schopnost spravovat každý hostitelský systém a abstrakci složitost základní platformy. Přesně to je co poskytuje orchestrátorů a plánovače. Pojďme se na to stručný přehled je tady:

- **Plánovači**. "Plánování" odkazuje na možnost pro správce k načtení souboru služby na hostitele systému, který vytváří spuštění konkrétní kontejner. Spouštění kontejnerů v clusteru Docker se obvykle označuje jako plánování. I když plánování odkazuje na konkrétní operace načítání definice služby, v obecnější smysl, zodpovídají za zapojení do hostitele init systému pro správu služeb v libovolné kapacitě potřebné plánovače.

   Plánovač clusteru má více cílů: efektivní využívání prostředků clusteru, práce s omezeními uživatelem zadané umístění, plánování aplikacím rychle nesmí zůstat je ve stavu čekání, s určitý stupeň "rovnost," se na chyby, robustní a mít vždycky k dispozici.

- **Orchestrátory**. Platformy rozšířit možnosti správy životního cyklu složité a vícekontejnerových úlohám, které jsou nasazené na clusteru hostitelů. Podle abstrahovat hostitelské infrastruktury, nástroji pro orchestraci uživatelům poskytnout způsob, jak celý cluster považovat za cíl jedno nasazení.

   Proces Orchestrace zahrnuje nástroje a platformy, která můžete automatizovat všechny aspekty správy aplikací z počáteční umístění nebo nasazení na kontejneru; Přesunutí kontejnery na různých hostitelích v závislosti na jeho hostitel stavu nebo výkonu. Správa verzí a kumulativní aktualizace a funkce, které podporují škálování a převzetí služeb při selhání, sledování stavu a mnoho dalších.

   Orchestrace je obecný termín, který odkazuje na kontejner plánování, správu clusteru a možná zřizování další hostitele.

Funkce poskytované verzí orchestrátorů a plánovači jsou komplexní k vývoji a vytvořit úplně od začátku, proto je obvykle vhodné použít Orchestrace řešení nabídnutých dodavatelů.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](manage-production-docker-environments.md)
