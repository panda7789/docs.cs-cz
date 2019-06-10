---
title: Kdy nasadit kontejnery Windows do Azure Container Service (Kubernetes)
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a Windows kontejnery | Kdy nasadit kontejnery Windows do Azure Container Service (Kubernetes)
ms.date: 04/30/2018
ms.openlocfilehash: 903082deba635dd0dfc22d0186fbc589f8d05b92
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758564"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>Kdy nasadit kontejnery Windows do Azure Container Service (Kubernetes)

Služba Azure Container Service optimalizuje konfiguraci oblíbených opensourcových nástrojů a technologií konkrétně pro Azure. Získáte otevřené řešení, které nabízí přenositelnost pro vaše kontejnery i Konfigurace aplikací. Vyberete velikost, počet hostitelů a nástroje orchestrator. Služba Azure Container Service obstarává infrastrukturu za vás.

Pokud již pracujete s open source orchestrátorů, jako je Kubernetes, Docker Swarm nebo DC/OS, nemusíte měnit svoje dosavadní postupy správy chcete přesunout úlohy kontejnerů do cloudu. Pomocí nástroje pro správu aplikací, které jste již obeznámeni s a připojte se pomocí standardních koncových bodů rozhraní API k orchestrátoru podle vaší volby.

Všechny tyto orchestrátorů jsou až po zralé prostředí, pokud používáte kontejnery linuxového Dockeru, ale může být pouze ve verzi Preview pro kontejnery Windows.

Například v Kubernetes, podpora kontejnerů je nativní (prvotřídní občany), takže pomocí kontejnerů Windows v Kubernetes platí také (ve verzi preview ve službě ACS od začátkem roku 2018).

Důležitá poznámka: Evolved a "Další PaaS" verze služby ACS (Azure Container Service) pro Kubernetes je AKS (služby Azure Kubernetes Service), ale kontejnerů Windows se ještě nepodporují od 2. čtvrtletí 2018, ale bude brzy podporovat.

>[!div class="step-by-step"]
>[Předchozí](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
>[další](choosing-azure-compute-options-for-container-based-applications.md)
