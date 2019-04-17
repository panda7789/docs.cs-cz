---
title: Správa produkčních prostředí Dockeru
description: Seznámení s klíčové body pro správu založených na kontejnerech produkčním prostředí.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 3f8c51b95f52a655de470ac237c51dd4ee9c13eb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2019
ms.locfileid: "59672097"
---
# <a name="manage-production-docker-environments"></a>Správa produkčních prostředí Dockeru

Správa clusterů a Orchestrace je proces řízení skupiny hostitelů. To může zahrnovat přidání a odebrání hostitele z clusteru, získávání informací o aktuálním stavu hostitelů a kontejnery a spuštěním nebo zastavením procesy. Správa clusterů a Orchestrace jsou úzce vázané na plánování, protože plánovači musí na každém hostiteli v clusteru, abyste měli naplánovat služby. Z tohoto důvodu se často používá stejný nástroj pro oba účely.

## <a name="container-service-and-management-tools"></a>Nástroje služby a správu kontejnerů

Container Service umožňuje rychlé nasazení oblíbených open source kontejneru řešení pro clustering a orchestraci kontejnerů. Používá Image Dockeru k zajištění, že plné přenositelnosti kontejnerů vaší aplikace. Pomocí služby Container Service můžete nasadit (používá technologii Mesosphere a Apache Mesos) DC/OS a Docker Swarm clustery pomocí šablon Azure Resource Manageru nebo webu Azure portal k zajištění, že je můžete tyto aplikace škálovat do tisíců – dokonce desítek tisíců – z kontejnery.

Tyto clustery nasadíte pomocí sad škálování virtuálních počítačů Azure a nich možné využívat nabídky Azure v oblasti sítí a úložišť. Pro přístup k službě Container Service, budete potřebovat předplatné Azure. Se službou Container Service můžete využít výhod funkcí Azure na podnikové úrovni a přitom zachovávat přenositelnost aplikací, včetně v orchestračních vrstvách.

Tabulka 6-1 jsou uvedeny běžné nástroje pro správu týkající se jejich orchestrátorů, plánovače a clusteringu platformy.

**Tabulka 6-1**. Nástroje dockeru pro správu

| Nástroje pro správu | Popis | Související orchestrátorů |
|------------------|-------------|-----------------------|
| [Azure Monitor for Containers](https://docs.microsoft.com/azure/monitoring/monitoring-container-insights-overview) | Azure vyhrazené nástroje pro správu Kubernetes | Služby Azure Kubernetes (AKS) |
| [Webové uživatelské rozhraní Kubernetes (řídicí panel)](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) | Nástroj pro správu Kubernetes, můžete monitorovat a spravovat místní cluster Kubernetes | Azure Kubernetes Service (AKS)<br/>Místní Kubernetes |
| [Portál Azure portal pro Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal)<br/>[Azure Service Fabric Exploreru](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) | Verze online a klasické pracovní plochy pro správu clusterů Service Fabric v Azure, v místním prostředí, místním vývojovém i v jiných cloudech | Azure Service Fabric |
| [(Monitorování Azure) pro monitorování kontejnerů](https://docs.microsoft.com/azure/azure-monitor/insights/containers) | Obecné kontejneru Správa y řešení pro monitorování. Můžete spravovat clustery Kubernetes pomocí [monitorování Azure pro kontejnery](https://docs.microsoft.com/azure/monitoring/monitoring-container-insights-overview). | Azure Service Fabric<br/>Azure Kubernetes Service (AKS)<br/>Mesosphere DC/OS a další. |

## <a name="azure-service-fabric"></a>Azure Service Fabric

Je další volbou pro správu a nasazení clusteru Azure Service Fabric. [Service Fabric](https://azure.microsoft.com/services/service-fabric/) je platforma mikroslužeb Microsoftu, která zahrnuje Orchestrace kontejnerů, jakož i pro vývojáře programovacích modelů pro vytváření vysoce škálovatelných mikroslužeb aplikací. Service Fabric podporuje Dockeru v systému Linux a kontejnery Windows a můžete spustit na serverech Windows a Linux.

Nástroje pro správu Service Fabric jsou následující:

- [Portál Azure portal pro Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal) operace související s clusterem (vytvoření/aktualizace/odstranění) clusteru nebo nakonfigurovat svou infrastrukturu (virtuální počítače, nástroj pro vyrovnávání zatížení, sítě atd.)

- [Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) je specializovaný webové uživatelské rozhraní desktopový nástroj víc platforem, které poskytují přehledy a určité operace v clusteru Service Fabric, z hlediska uzly nebo virtuální počítače a z aplikace a služby pohledu.

>[!div class="step-by-step"]
>[Předchozí](run-microservices-based-applications-in-production.md)
>[další](monitor-containerized-application-services.md)
