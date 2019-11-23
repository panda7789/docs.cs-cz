---
title: Spuštění složených aplikací a aplikací založených na mikroslužbách v produkčních prostředích
description: Získejte informace o klíčových součástech, které spouští aplikace založené na kontejnerech v produkčním prostředí.
ms.date: 02/15/2019
ms.openlocfilehash: 69df3d39a00b91cbe59c96e5fcab841a60943bcc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295463"
---
# <a name="run-composed-and-microservices-based-applications-in-production-environments"></a>Spuštění složených aplikací a aplikací založených na mikroslužbách v produkčních prostředích

Aplikace, které se skládají z více mikroslužeb, je potřeba nasadit do clusterů Orchestrator, aby se zjednodušila složitost nasazení a zajistila její životaschopnost z jejího pohledu. Bez clusteru Orchestrator by bylo obtížné nasazovat a škálovat komplexní aplikace mikroslužeb.

## <a name="introduction-to-orchestrators-schedulers-and-container-clusters"></a>Seznámení s orchestrací, plánovači a clustery kontejnerů

Dříve v této elektronické knize byly *clustery* a *schedulery* představené jako součást diskuse o softwarových architekturách a vývoji. Kubernetes a Service Fabric jsou příklady clusterů Docker. Oba tyto orchestrace můžou běžet jako součást infrastruktury poskytované službou Microsoft Azure Kubernetes.

Když se aplikace škálují napříč více hostitelskými systémy, možnost spravovat jednotlivé hostitelské systémy a oddělit složitost základní platformy se budou atraktivní. To je přesně to, jaké Orchestrace a plánovače poskytují. Pojďme se na ně podívat v krátkém umístění:

- **Schedulery**. "Plánování" odkazuje na schopnost správce načíst soubor služby do hostitelského systému, který stanoví, jak spustit konkrétní kontejner. Spouštění kontejnerů v clusteru Docker je v úmyslu známé jako plánování. I když plánování odkazuje na konkrétní akt načtení definice služby, v obecnější smyslu jsou schedulery zodpovědné za zapojení do inicializačního systému hostitele za účelem správy služeb v jakékoli potřebné kapacitě.

   Plánovač clusteru má několik cílů: efektivní využívání prostředků clusteru, práci s uživatelskými omezeními pro umístění a rychlé plánování aplikací, které neopouští stav v nevyřízeném stavu, který je odolný proti chybám. vždy k dispozici.

- **Orchestrace**. Platformy rozšíří možnosti správy životního cyklu do složitých úloh s více kontejnery nasazených na cluster hostitelů. Díky abstrakci hostitelské infrastruktury poskytují nástroje Orchestration uživatelům způsob, jak zacházet s celým clusterem jako s jedním cílem nasazení.

   Proces orchestrace zahrnuje nástroje a platformu, které mohou automatizovat všechny aspekty správy aplikací z počátečního umístění nebo nasazení na kontejner. Přesunutí kontejnerů do různých hostitelů v závislosti na stavu nebo výkonu hostitele; Správa verzí a průběžné aktualizace a funkce monitorování stavu, které podporují škálování a převzetí služeb při selhání; a spousta dalších.

   Orchestrace je rozsáhlý pojem, který odkazuje na plánování kontejneru, správu clusterů a případně zřizování dalších hostitelů.

Možnosti poskytované orchestrací a plánovači jsou složité pro vývoj a vytváření zcela od začátku, proto byste obvykle chtěli použít řešení orchestrace nabízená dodavateli.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[Další](manage-production-docker-environments.md)
