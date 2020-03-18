---
title: Kdy nasadit kontejnery Windows do služby Azure Container Service (to znamená Kubernetes)
description: Modernizace stávajících aplikací .NET pomocí Azure Cloudu a kontejnerů Windows | Kdy nasadit kontejnery Windows do služby Azure Container Service (to znamená Kubernetes)
ms.date: 04/30/2018
ms.openlocfilehash: 903082deba635dd0dfc22d0186fbc589f8d05b92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "68676910"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>Kdy nasadit kontejnery Windows do služby Azure Container Service (to znamená Kubernetes)

Azure Container Service optimalizuje konfiguraci oblíbených open source nástrojů a technologií speciálně pro Azure. Získáte otevřené řešení, které nabízí přenositelnost pro vaše kontejnery i pro konfiguraci aplikace. Můžete vybrat velikost, počet hostitelů a nástroje orchestrator. Azure Container Service zpracovává infrastrukturu za vás.

Pokud už pracujete s orchestrátory s otevřeným zdrojovým kódem, jako jsou Kubernetes, Docker Swarm nebo DC/OS, nemusíte měnit stávající postupy správy, abyste přesunuli úlohy kontejnerů do cloudu. Použijte nástroje pro správu aplikací, které už znáte, a připojte se přes standardní koncové body rozhraní API pro orchestrátorpodle vašeho výběru.

Všechny tyto orchestrátory jsou vyspělá prostředí, pokud používáte kontejnery Linux Docker, ale může být pouze ve stavu Náhled pro kontejnery systému Windows.

Například v Kubernetes je podpora kontejnerů nativní (prvotřídní občan), takže použití kontejnerů Windows na Kubernetes je také efektivní (ve verzi Preview v ACS od začátku roku 2018).

Důležitá poznámka: Vyvinutá a "více PaaS" verze ACS (Azure Container Service) pro Kubernetes je AKS (Služba Azure Kubernetes), ale kontejnery Windows stále nejsou podporovány od Q2 2018, ale brzy budou podporovány.

>[!div class="step-by-step"]
>[Předchozí](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
>[další](choosing-azure-compute-options-for-container-based-applications.md)
