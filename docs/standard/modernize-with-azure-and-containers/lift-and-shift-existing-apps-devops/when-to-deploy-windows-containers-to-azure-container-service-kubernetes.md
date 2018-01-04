---
title: "Když k nasazení Windows kontejnerů Azure Container Service (Kubernetes)"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Když k nasazení Windows kontejnerů Azure Container Service (Kubernetes)"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2f7ed0c9ebf1c80ae6cae4311b2682d3cc161623
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>Když k nasazení Windows kontejnerů Azure Container Service (Kubernetes)

Azure Container Service optimalizuje konfigurace oblíbených open-source nástrojů a technologií speciálně pro Azure. Získat otevřete řešení, která nabízí přenositelnost pro vaše kontejnery i pro konfiguraci aplikace. Můžete vybrat, velikost, počtu hostitelů a nástroje orchestrator. Azure Container Service zpracovává infrastruktury pro vás.

Pokud již pracujete s otevřeným zdrojem orchestrators jako Kubernetes, Docker Swarm nebo DC/OS, nemusíte měnit vaše stávající postupy správy pro přesun kontejneru úloh do cloudu. Pomocí nástrojů pro správu aplikaci jste již obeznámeni s a připojení přes standardní koncové body rozhraní API pro nástroj orchestrator podle svého výběru.

Pokud používáte Linux Docker kontejnery, ale jejich také podporu Windows kontejnery jako z 2017 (některé dříve, některé nedávno, v závislosti na orchestrator), jsou všechny tyto orchestrators vyspělá prostředí.

Například v Kubernetes, podporu pro kontejnery je nativní (prvotřídní občan), takže použití Windows kontejnerů na Kubernetes je také velmi efektivní a spolehlivý (ve verzi preview, dokud již v rané fázi spadají 2017).

>[!div class="step-by-step"]
[Předchozí](when-to-deploy-windows-containers-to-service-fabric.md)
[další](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
