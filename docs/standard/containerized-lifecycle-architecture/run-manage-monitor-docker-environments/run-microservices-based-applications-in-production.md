---
title: Spouštění skládá a mikroslužbových aplikací v produkčním prostředí
description: Životní cyklus aplikace kontejnerizovaných Dockeru s platformou a nástroji Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 18e6cb1fb5f496b66c89cb8e009a67894b8a76ad
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48845297"
---
# <a name="run-composed-and-microservices-based-applications-in-production-environments"></a>Spouštění skládá a mikroslužbových aplikací v produkčním prostředí

Aplikace, které sestává z několika mikroslužeb je nutné nasadit do clusterů nástroje orchestrator, abyste zjednodušili složitost nasazení a bylo možné z hlediska IT. Bez clusteru služby orchestrator by bylo velmi obtížné nasadit a škálovat aplikace komplexní mikroslužeb.

## <a name="introduction-to-orchestrators-schedulers-and-container-clusters"></a>Úvod do orchestrátorů, plánovače a clustery kontejnerů

Dříve v této e knihy, zavedli jsme *clustery* a *plánovači* jako součást diskuse o softwaru pro architekturu a vývoj. Mezi clustery Docker patří Docker Swarm a Mesosphere Datacenter operačního systému (DC/OS). Obě tyto můžete spouštět jako součást infrastruktury k dispozici ve službě Microsoft Azure Container Service.

Když aplikace jsou horizontálním navýšením kapacity napříč více hostitelských systémech, stane se atraktivní schopnost spravovat každý hostitelský systém a abstrakci složitost základní platformy. Přesně to je co poskytuje orchestrátorů a plánovače. Pojďme se na to stručný přehled je tady:

- **Plánovači**. "Plánování" odkazuje na možnost pro správce k načtení souboru služby na hostitele systému, který vytváří spuštění konkrétní kontejner. Spouštění kontejnerů v clusteru Docker se obvykle označuje jako plánování. I když plánování odkazuje na konkrétní operace načítání definice služby, v obecnější smysl, zodpovídají za zapojení do hostitele init systému pro správu služeb v libovolné kapacitě potřebné plánovače.

   Plánovač clusteru má více cílů: efektivní využívání prostředků clusteru, práce s omezeními uživatelem zadané umístění, plánování aplikacím rychle nesmí zůstat je ve stavu čekání, s určitý stupeň "rovnost," se na chyby, robustní a mít vždycky k dispozici.

- **Orchestrace**. Platformy rozšířit možnosti správy životního cyklu složité a vícekontejnerových úlohám, které jsou nasazené na clusteru hostitelů. Podle abstrahovat hostitelské infrastruktury, nástroji pro orchestraci uživatelům poskytnout způsob, jak celý cluster považovat za cíl jedno nasazení.

   Proces Orchestrace zahrnuje nástroje a platformy, která můžete automatizovat všechny aspekty správy aplikací z počáteční umístění nebo nasazení na kontejneru; Přesunutí kontejnery na různých hostitelích v závislosti na jeho hostitel stavu nebo výkonu. Správa verzí a kumulativní aktualizace a funkce, které podporují škálování a převzetí služeb při selhání, sledování stavu a mnoho dalších.

   Orchestrace je obecný termín, který odkazuje na kontejner plánování, správu clusteru a možná zřizování další hostitele.

Funkce poskytované verzí orchestrátorů a plánovači jsou velmi složité k vývoji a vytvořit úplně od začátku, a proto je obvykle vhodné provést pomocí Orchestrace řešení nabízí dodavatelů.


>[!div class="step-by-step"]
[Předchozí](index.md)
[další](manage-production-docker-environments.md)
