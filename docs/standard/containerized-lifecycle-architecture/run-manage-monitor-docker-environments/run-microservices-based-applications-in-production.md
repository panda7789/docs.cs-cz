---
title: Spuštění sestavit a mikroslužeb aplikacím v produkčním prostředí
description: Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 47685bfd8dca50c5e93be7574ea6ef30a49cbede
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568794"
---
# <a name="run-composed-and-microservices-based-applications-in-production-environments"></a>Spuštění sestavit a mikroslužeb aplikacím v produkčním prostředí

Aplikace sestává z několika mikroslužeb nutné k nasazení do clusterů orchestrator, aby bylo možné zjednodušit složitosti nasazení a nastavit jej jako přijatelná z hlediska IT. Bez clusteru služby orchestrator by bylo velmi obtížné nasadit a škálování aplikace komplexní mikroslužeb.

## <a name="introduction-to-orchestrators-schedulers-and-container-clusters"></a>Úvod do orchestrators plánovače a clustery kontejneru

Dříve v této e knihy, zavedli jsme *clustery* a *plánovače* jako součást diskusi o architektura softwaru a vývoj. Příkladem Docker clustery jsou Docker Swarm a Mesosphere Datacenter operačního systému (DC/OS). Obě tyto můžete spouštět jako součást infrastruktury služby Microsoft Azure Container Service.

Když aplikace jsou instancemi mezi několika systémy hostitele, stane se atraktivní schopnost spravovat každý hostitelský systém a abstraktní rychle složitost základní platformy. Je přesněji co orchestrators a plánovače poskytují. Podívejme se stručný na je tady:

-   **Plánovače *** *"Plánování" odkazuje na schopnost Správce služby soubor do systém hostitele, který určuje jak spustit specifický kontejner. Spuštění kontejnery v clusteru Docker obvykle označují jako plánování. I když plánování odkazuje na konkrétní operace načítání definici služby v další obecné smysl, plánovače jsou zodpovědní za zapojování do systému init hostitele ke správě služeb v jakémkoli kapacity potřeby.

Scheduler clusteru má více cílů: efektivně pomocí prostředků clusteru, práce s uživatelem zadané umístění omezení, plánování aplikace rychle není ponechat je ve stavu čekající na vyřízení, má určitý stupeň "rovnosti," Probíhá robustní na chyby, a být vždy k dispozici.

-   **Orchestrace *** *platformy rozšířit funkce pro správu životního cyklu komplexní, multicontainer úlohy, které jsou nasazené na clusteru hostitelů. Podle poskytuje abstrakci infrastruktury hostitele, nástroje orchestration uživatelům poskytnout způsob, jak celý cluster považovat za cíl jedno nasazení.

Proces orchestration zahrnuje nástrojů a platformu, která můžete automatizovat všechny aspekty správy aplikací z počáteční umístění nebo nasazení na kontejneru; Přesunutí kontejnery na různých hostitelích v závislosti na jeho hostitel stavu nebo výkonu. Správa verzí kumulativní aktualizace a monitorování funkce, které podporují škálování a převzetí služeb při selhání; stavu a mnoho dalších.

Orchestrace je široký termín, který odkazuje na kontejner plánování, Správa clusteru a možná zřizování další hostitele.

Funkce poskytované verzí orchestrators a plánovače jsou velmi složité k vývoji a vytvořit od začátku, a proto obvykle by chcete použití orchestration řešení nabízí Dodavatelé.


>[!div class="step-by-step"]
[Předchozí] (index.md) [Další] (spravovat produkční docker-environments.md)
