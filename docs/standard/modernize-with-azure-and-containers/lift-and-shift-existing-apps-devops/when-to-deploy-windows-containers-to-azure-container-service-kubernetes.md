---
title: Když k nasazení Windows kontejnerů Azure Container Service (Kubernetes)
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Když k nasazení Windows kontejnerů Azure Container Service (Kubernetes)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cccf78ef5b7683a2eefa3efab50a7bbe1bffda18
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>Když k nasazení Windows kontejnerů Azure Container Service (Kubernetes)

Azure Container Service optimalizuje konfigurace oblíbených open-source nástrojů a technologií speciálně pro Azure. Získat otevřete řešení, která nabízí přenositelnost pro vaše kontejnery i pro konfiguraci aplikace. Můžete vybrat, velikost, počtu hostitelů a nástroje orchestrator. Azure Container Service zpracovává infrastruktury pro vás.

Pokud již pracujete s otevřeným zdrojem orchestrators jako Kubernetes, Docker Swarm nebo DC/OS, nemusíte měnit vaše stávající postupy správy pro přesun kontejneru úloh do cloudu. Pomocí nástrojů pro správu aplikaci jste již obeznámeni s a připojení přes standardní koncové body rozhraní API pro nástroj orchestrator podle svého výběru.

Pokud používáte Linux Docker kontejnery, ale jejich také podporu Windows kontejnery jako z 2017 (některé dříve, některé nedávno, v závislosti na orchestrator), jsou všechny tyto orchestrators vyspělá prostředí.

Například v Kubernetes, podporu pro kontejnery je nativní (prvotřídní občan), takže použití Windows kontejnerů na Kubernetes je také velmi efektivní a spolehlivý (ve verzi preview, dokud již v rané fázi spadají 2017).

>[!div class="step-by-step"]
[Předchozí](when-to-deploy-windows-containers-to-service-fabric.md)
[další](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
