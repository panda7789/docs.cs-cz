---
title: Správa produkčních prostředí Dockeru
description: Seznamte se s klíčovými body pro správu produkčního prostředí založeného na kontejnerech.
ms.date: 02/15/2019
ms.openlocfilehash: 26e7a3319afe593d75e2384d023c901a389245dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "71834505"
---
# <a name="manage-production-docker-environments"></a>Správa produkčních prostředí Dockeru

Správa clusteru a orchestrace je proces řízení skupiny hostitelů. To může zahrnovat přidání a odebrání hostitelů z clusteru, získání informací o aktuálním stavu hostitelů a kontejnerů a spuštění a zastavení procesů. Správa clusteru a orchestrace jsou úzce spojeny s plánováním, protože plánovač musí mít přístup ke každému hostiteli v clusteru, aby mohl plánovat služby. Z tohoto důvodu se stejný nástroj často používá pro oba účely.

## <a name="container-service-and-management-tools"></a>Kontejnerové služby a nástroje pro správu

Container Service poskytuje rychlé nasazení populárních open source řešení clusteringu a orchestrace kontejnerů. Používá image Dockeru k zajištění, že vaše kontejnery aplikace jsou plně přenosné. Pomocí kontejnerové služby můžete nasadit clustery DC/OS (využívající technologii Mesosphere a Apache Mesos) a clustery Docker Swarm se šablonami Azure Resource Manageru nebo portálem Azure, abyste zajistili, že tyto aplikace můžete škálovat na tisíce – dokonce desítky tisíc – kontejnerů.

Tyto clustery nasadíte pomocí sad škálování virtuálních počítačů Azure, a díky tomu bude u nich možné využívat nabídky Azure v oblasti sítí a úložišť. Pro přístup ke službě Container Service potřebujete předplatné Azure. S Kontejnerovou službou můžete využívat funkce Azure na podnikové úrovni a přitom zachovat přenositelnost aplikací, a to i ve vrstvách orchestrace.

Tabulka 6-1 uvádí běžné nástroje pro správu související s jejich orchestrátory, plánovači a clustering platformy.

**Tabulka 6-1**. Nástroje pro správu Dockeru

| Nástroje pro správu | Popis | Související orchestrátory |
|------------------|-------------|-----------------------|
| [Azure Monitor pro kontejnery](https://docs.microsoft.com/azure/monitoring/monitoring-container-insights-overview) | Nástroj pro správu Kubernetes věnovaný Azure | Služby Azure Kubernetes (AKS) |
| [Webové uživatelské uzlina Kubernetes (řídicí panel)](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) | Nástroj pro správu Kubernetes, může monitorovat a spravovat místní cluster Kubernetes | Azure Kubernetes Service (AKS)<br/>Místní Kubernetes |
| [Portál Azure pro service fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal)<br/>[Průzkumník prostředků infrastruktury služby Azure](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) | Online a desktopová verze pro správu clusterů Service Fabric v Azure, v místním prostředí, v místním vývoji a dalších cloudech | Azure Service Fabric |
| [Monitorování kontejnerů (Azure Monitor)](https://docs.microsoft.com/azure/azure-monitor/insights/containers) | Obecné řešení monitorování kontejnerů y. Můžete spravovat Clustery Kubernetes prostřednictvím [Azure Monitor pro kontejnery](https://docs.microsoft.com/azure/monitoring/monitoring-container-insights-overview). | Azure Service Fabric<br/>Azure Kubernetes Service (AKS)<br/>Mesosphere DC/OS a další. |

## <a name="azure-service-fabric"></a>Azure Service Fabric

Další volbou pro nasazení a správu clusteru je Azure Service Fabric. [Service Fabric](https://azure.microsoft.com/services/service-fabric/) je platforma mikroslužeb společnosti Microsoft, která zahrnuje orchestraci kontejnerů a také vývojářské programovací modely pro vytváření vysoce škálovatelných aplikací mikroslužeb. Service Fabric podporuje Docker v Linuxu a Windows kontejnery a lze spustit na serverech Windows a Linux.

Následují nástroje pro správu Service Fabric:

- [Azure portal for Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal) související operace související s clusterem (vytvořit/aktualizovat/odstranit) clusteru nebo nakonfigurovat jeho infrastrukturu (virtuální počítače, nástroj pro vyrovnávání zatížení, sítě, atd.)

- [Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) je specializovaný webový uživatelský počítač a desktopový multiplatformní nástroj, který poskytuje přehledy a určité operace v clusteru Service Fabric, z hlediska uzlů/virtuálních počítačů a z hlediska aplikací a služeb.

>[!div class="step-by-step"]
>[Předchozí](run-microservices-based-applications-in-production.md)
>[další](monitor-containerized-application-services.md)
