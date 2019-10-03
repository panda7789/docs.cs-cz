---
title: Správa prostředí produkčního Docker
description: Získejte informace o klíčových bodech pro správu produkčního prostředí založeného na kontejneru.
ms.date: 02/15/2019
ms.openlocfilehash: 26e7a3319afe593d75e2384d023c901a389245dc
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834505"
---
# <a name="manage-production-docker-environments"></a>Správa prostředí produkčního Docker

Správa clusteru a orchestrace je proces řízení skupiny hostitelů. To může zahrnovat přidávání a odebírání hostitelů z clusteru, získávání informací o aktuálním stavu hostitelů a kontejnerů a spouštění a zastavování procesů. Správa clusteru a orchestrace jsou úzce vázané na plánování, protože Plánovač musí mít přístup ke každému hostiteli v clusteru, aby bylo možné plánovat služby. Z tohoto důvodu se pro oba účely často používá stejný nástroj.

## <a name="container-service-and-management-tools"></a>Služby kontejnerů a nástroje pro správu

Služba kontejneru poskytuje rychlé nasazení oblíbených open source řešení clusteringu a orchestrace kontejnerů. Pomocí Docker images zajišťuje, aby byly kontejnery aplikací plně přenosné. Pomocí služby Container Service můžete nasadit DC/OS (napájený pomocí Mesosphere a Apache Mesos) a clustery Docker Swarm pomocí šablon Azure Resource Manager nebo Azure Portal, abyste měli jistotu, že můžete tyto aplikace škálovat na tisíce – i desítky tisíců – kontejnery.

Tyto clustery nasadíte pomocí sad škálování virtuálních počítačů Azure, a díky tomu bude u nich možné využívat nabídky Azure v oblasti sítí a úložišť. Pro přístup ke službě kontejneru potřebujete předplatné Azure. Díky službě Container Service můžete využívat výhody funkcí Azure na podnikové úrovni a přitom zachovat přenositelnost aplikace, včetně vrstev orchestrace.

Tabulka 6-1 obsahuje seznam běžných nástrojů pro správu, které souvisejí s jejich orchestrací, plánovači a platformou clusteringu.

**Tabulka 6-1**. Nástroje pro správu Docker

| Nástroje pro správu | Popis | Související orchestrace |
|------------------|-------------|-----------------------|
| [Azure Monitor pro kontejnery](https://docs.microsoft.com/azure/monitoring/monitoring-container-insights-overview) | Nástroj pro správu vyhrazených Kubernetes Azure | Služby Azure Kubernetes (AKS) |
| [Webové uživatelské rozhraní Kubernetes (řídicí panel)](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) | Nástroj pro správu Kubernetes může monitorovat a spravovat místní cluster Kubernetes. | Azure Kubernetes Service (AKS)<br/>Místní Kubernetes |
| [Azure Portal pro Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal)<br/>[Service Fabric Explorer Azure](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) | Online a desktopová verze pro správu Service Fabricch clusterů, v Azure, místním vývoji a dalších cloudech | Azure Service Fabric |
| [Monitorování kontejnerů (Azure Monitor)](https://docs.microsoft.com/azure/azure-monitor/insights/containers) | Obecné řešení pro monitorování kontejnerů y. Může spravovat clustery Kubernetes prostřednictvím [Azure monitor pro kontejnery](https://docs.microsoft.com/azure/monitoring/monitoring-container-insights-overview). | Azure Service Fabric<br/>Azure Kubernetes Service (AKS)<br/>Mesosphere DC/OS a další. |

## <a name="azure-service-fabric"></a>Azure Service Fabric

Další možností pro nasazení clusteru a správy je Service Fabric Azure. [Service Fabric](https://azure.microsoft.com/services/service-fabric/) je platforma mikroslužeb společnosti Microsoft, která zahrnuje orchestraci kontejnerů, a vývojové vývojové modely pro vytváření vysoce škálovatelných aplikací mikroslužeb. Service Fabric podporuje Docker v kontejnerech Linux a Windows a může běžet na serverech se systémy Windows a Linux.

Následující jsou Service Fabric nástroje pro správu:

- [Azure Portal pro Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal) operace související s clustery (vytvořit/aktualizovat/odstranit) cluster nebo nakonfigurovat jeho infrastrukturu (virtuální počítače, nástroj pro vyrovnávání zatížení, sítě atd.)

- [Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) je specializované webové uživatelské rozhraní a desktopové nástroje pro více platforem, které poskytuje přehledy a určité operace v clusteru Service Fabric, z pohledu uzlů/virtuálních počítačů a z hlediska aplikací a služeb.

>[!div class="step-by-step"]
>[Předchozí](run-microservices-based-applications-in-production.md)@no__t – 1 –[Další](monitor-containerized-application-services.md)
