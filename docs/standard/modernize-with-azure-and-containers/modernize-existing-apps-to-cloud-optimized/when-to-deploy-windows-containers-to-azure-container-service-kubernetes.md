---
title: Když k nasazení Windows kontejnerů Azure Container Service (Kubernetes)
description: Modernizovat existující aplikace .NET s kontejnery cloudu Azure a Windows | Když k nasazení Windows kontejnerů Azure Container Service (Kubernetes)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: b7f106e2b79a2c6bb24733debf7f4828505d66a6
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>Když k nasazení Windows kontejnerů Azure Container Service (Kubernetes)

Azure Container Service optimalizuje konfigurace oblíbených open-source nástrojů a technologií speciálně pro Azure. Získat otevřete řešení, která nabízí přenositelnost pro vaše kontejnery i pro konfiguraci aplikace. Můžete vybrat, velikost, počtu hostitelů a nástroje orchestrator. Azure Container Service zpracovává infrastruktury pro vás.

Pokud již pracujete s otevřeným zdrojem orchestrators jako Kubernetes, Docker Swarm nebo DC/OS, nemusíte měnit vaše stávající postupy správy pro přesun kontejneru úloh do cloudu. Pomocí nástroje pro správu aplikací, které jste již obeznámeni s a připojení přes standardní koncové body rozhraní API pro nástroj orchestrator podle svého výběru.

Všechny tyto orchestrators jsou vyspělá prostředí, pokud používáte Linux Docker kontejnery, ale může být pouze ve verzi Preview stavu pro kontejnery systému Windows.

Například v Kubernetes, podporu pro kontejnery je nativní (prvotřídní občan), takže použití Windows kontejnerů na Kubernetes je také efektivní (ve verzi preview v rámci služby ACS od časná 2018).

Důležité upozornění: evolved a "Další PaaS" je verze služby ACS (Azure Container Service) pro Kubernetes AKS (Azure Kubernetes Service), Windows kontejnery nepodporují stále od 2018 Dotaz č. 2, ale budou brzy podporované.

>[!div class="step-by-step"]
[Předchozí](when-to-deploy-windows-containers-to-service-fabric.md)
[další](choosing-azure-compute-options-for-container-based-applications.md)
