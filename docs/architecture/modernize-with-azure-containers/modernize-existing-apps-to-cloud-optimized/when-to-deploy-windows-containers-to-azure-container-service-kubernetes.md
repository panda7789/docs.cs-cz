---
title: Kdy nasadit kontejnery Windows do Azure Container Service (tj. Kubernetes)
description: Modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows | Kdy nasadit kontejnery Windows do Azure Container Service (tj. Kubernetes)
ms.date: 04/30/2018
ms.openlocfilehash: 903082deba635dd0dfc22d0186fbc589f8d05b92
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/08/2019
ms.locfileid: "68676910"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>Kdy nasadit kontejnery Windows do Azure Container Service (tj. Kubernetes)

Azure Container Service optimalizuje konfiguraci oblíbených open source nástrojů a technologií konkrétně pro Azure. Získáte otevřené řešení, které nabízí přenositelnost pro vaše kontejnery i pro konfiguraci aplikace. Vyberte velikost, počet hostitelů a nástroje Orchestrator. Azure Container Service zpracovává infrastrukturu za vás.

Pokud už pracujete s open source orchestrací, jako je Kubernetes, Docker Swarm nebo DC/OS, nemusíte měnit stávající postupy správy, aby bylo možné přesunout úlohy kontejneru do cloudu. Použijte nástroje pro správu aplikací, které už znáte, a připojte se přes standardní koncové body rozhraní API pro Orchestrator podle vašeho výběru.

Všechny tyto orchestrace jsou vyspělá prostředí, pokud používáte kontejnery Docker pro Linux, ale můžou být jenom ve verzi Preview pro kontejnery Windows.

Například v Kubernetes je podpora pro kontejnery nativní (občan první třídy), takže použití kontejnerů Windows v Kubernetes je také účinné (ve verzi Preview ve službě ACS k začátku 2018).

Důležité upozornění: vývojová a další PaaS verze ACS (Azure Container Service) pro Kubernetes je AKS (služba Azure Kubernetes), ale kontejnery Windows se ještě nepodporují od Q2 2018, ale budou se brzy podporovat.

>[!div class="step-by-step"]
>[Předchozí](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
>[Další](choosing-azure-compute-options-for-container-based-applications.md)
