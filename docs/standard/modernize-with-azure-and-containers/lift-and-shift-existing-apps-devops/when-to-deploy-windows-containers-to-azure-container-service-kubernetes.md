---
title: "Když k nasazení Windows kontejnerů Azure Container Service (Kubernetes)"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Když k nasazení Windows kontejnerů Azure Container Service (Kubernetes)"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f0a096712e14e506403961f0b9283ca4b707cbda
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2018
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>Když k nasazení Windows kontejnerů Azure Container Service (Kubernetes)

Azure Container Service optimalizuje konfigurace oblíbených open-source nástrojů a technologií speciálně pro Azure. Získat otevřete řešení, která nabízí přenositelnost pro vaše kontejnery i pro konfiguraci aplikace. Můžete vybrat, velikost, počtu hostitelů a nástroje orchestrator. Azure Container Service zpracovává infrastruktury pro vás.

Pokud již pracujete s otevřeným zdrojem orchestrators jako Kubernetes, Docker Swarm nebo DC/OS, nemusíte měnit vaše stávající postupy správy pro přesun kontejneru úloh do cloudu. Pomocí nástrojů pro správu aplikaci jste již obeznámeni s a připojení přes standardní koncové body rozhraní API pro nástroj orchestrator podle svého výběru.

Pokud používáte Linux Docker kontejnery, ale jejich také podporu Windows kontejnery jako z 2017 (některé dříve, některé nedávno, v závislosti na orchestrator), jsou všechny tyto orchestrators vyspělá prostředí.

Například v Kubernetes, podporu pro kontejnery je nativní (prvotřídní občan), takže použití Windows kontejnerů na Kubernetes je také velmi efektivní a spolehlivý (ve verzi preview, dokud již v rané fázi spadají 2017).

>[!div class="step-by-step"]
[Předchozí](when-to-deploy-windows-containers-to-service-fabric.md)
[další](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
