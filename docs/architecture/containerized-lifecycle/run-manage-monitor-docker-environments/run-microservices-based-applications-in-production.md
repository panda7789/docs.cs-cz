---
title: Spuštění složených aplikací a aplikací založených na mikroslužbách v produkčních prostředích
description: Seznamte se s klíčovými součástmi pro spouštění aplikací založených na kontejnerech ve výrobě
ms.date: 02/15/2019
ms.openlocfilehash: 69df3d39a00b91cbe59c96e5fcab841a60943bcc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295463"
---
# <a name="run-composed-and-microservices-based-applications-in-production-environments"></a>Spuštění složených aplikací a aplikací založených na mikroslužbách v produkčních prostředích

Aplikace složené z více mikroslužeb je třeba nasadit do clusterů orchestrator, aby se zjednodušila složitost nasazení a z hlediska IT bylo životaschopné. Bez clusteru orchestrator by bylo obtížné nasadit a škálovat komplexní aplikace mikroslužeb.

## <a name="introduction-to-orchestrators-schedulers-and-container-clusters"></a>Úvod do orchestrátorů, plánovačů a clusterů kontejnerů

Dříve v této e-knihy, *clustery* a *plánovače* byly zavedeny jako součást diskuse o softwarové architektury a vývoje. Kubernetes a Service Fabric jsou příklady clusterů Docker. Oba tyto orchestrátory lze spustit jako součást infrastruktury poskytované službou Microsoft Azure Kubernetes Service.

Při škálování aplikací napříč více hostitelských systémů, schopnost spravovat každý hostitelský systém a abstraktní pryč složitost podkladové platformy se stává atraktivní. To je přesně to, co orchestrátory a plánovače poskytují. Podívejme se na ně krátce zde:

- **Plánovače**."Plánování" odkazuje na schopnost správce načíst soubor služby do hostitelského systému, který stanoví, jak spustit konkrétní kontejner. Spouštění kontejnerů v clusteru Dockeru bývá označováno jako plánování. Přestože plánování odkazuje na konkrétní akt načítání definice služby, v obecnějším smyslu plánovače jsou zodpovědné za připojení do hostitelského systému init pro správu služeb v jakékoli potřebné kapacity.

   Plánovač clusteru má více cílů: efektivní využití prostředků clusteru, efektivní práce s omezeními umístění dodanými uživateli, rychlé plánování aplikací tak, aby je nenechávaly v čekajícím stavu, s určitou mírou "spravedlnosti", odolností vůči chybám a být vždy k dispozici.

- **Orchestrátory**.Platformy rozšiřují možnosti správy životního cyklu na složité úlohy s více kontejnery nasazené v clusteru hostitelů. Abstrakcí hostitelské infrastruktury poskytují nástroje orchestrace uživatelům způsob, jak považovat celý cluster za jeden cíl nasazení.

   Proces orchestrace zahrnuje nástroje a platformu, která může automatizovat všechny aspekty správy aplikací od počátečního umístění nebo nasazení na kontejner; přesouvání kontejnerů do různých hostitelů v závislosti na stavu nebo výkonu hostitele; správa verzí a postupné aktualizace a funkce monitorování stavu, které podporují škálování a převzetí služeb při selhání; a mnoho dalších.

   Orchestrace je obecný termín, který odkazuje na plánování kontejnerů, správu clusteru a případně zřizování dalších hostitelů.

Funkce poskytované orchestrátory a plánovači jsou složité pro vývoj a vytváření od začátku, proto byste obvykle chtěli použít orchestrační řešení nabízená dodavateli.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](manage-production-docker-environments.md)
