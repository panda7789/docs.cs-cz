---
title: Správa produkčních prostředí Dockeru
description: Životní cyklus aplikace kontejnerizovaných Dockeru s platformou a nástroji Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 3bafdd9f6a6aa4f850fd28b6315e68c643d1f8c0
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50202852"
---
# <a name="manage-production-docker-environments"></a>Správa produkčních prostředí Dockeru

Správa clusterů a Orchestrace je proces řízení skupiny hostitelů. To může zahrnovat přidání a odebrání hostitele z clusteru, získávání informací o aktuálním stavu hostitelů a kontejnery a spuštěním nebo zastavením procesy. Správa clusterů a Orchestrace jsou úzce vázané na plánování, protože plánovači musí na každém hostiteli v clusteru, abyste měli naplánovat služby. Z tohoto důvodu se často používá stejný nástroj pro oba účely.

## <a name="container-service-and-management-tools"></a>Nástroje služby a správu kontejnerů

Container Service umožňuje rychlé nasazení oblíbených open source kontejneru řešení pro clustering a orchestraci kontejnerů. Používá Image Dockeru k zajištění, že plné přenositelnosti kontejnerů vaší aplikace. Pomocí služby Container Service můžete nasadit (používá technologii Mesosphere a Apache Mesos) DC/OS a Docker Swarm clustery pomocí šablon Azure Resource Manageru nebo webu Azure portal k zajištění, že je můžete tyto aplikace škálovat do tisíců – dokonce desítek tisíců – z kontejnery.

Tyto clustery nasadíte pomocí sad škálování virtuálních počítačů Azure a nich možné využívat nabídky Azure v oblasti sítí a úložišť. Pro přístup k službě Container Service, budete potřebovat předplatné Azure. Se službou Container Service můžete využít výhod funkcí Azure na podnikové úrovni a přitom zachovávat přenositelnost aplikací, včetně v orchestračních vrstvách.

Tabulka 6-1 jsou uvedeny běžné nástroje pro správu týkající se jejich orchestrátorů, plánovače a clusteringu platformy.

Nástroje pro správu Docker Tabulka 6-1:


| Nástroje pro správu      | Popis           | Související orchestrátorů |
|-----------------------|-----------------------|-----------------------|
| Container Service\(správu uživatelského rozhraní na webu Azure portal) | [Container Service](https://azure.microsoft.com/services/container-service/) poskytuje snadno získat způsob, jak začít [nasazení clusteru kontejneru v Azure](https://docs.microsoft.com/azure/container-service/dcos-swarm/container-service-deployment) podle oblíbených orchestrátorů, jako je Mesosphere DC/OS, Kubernetes a Docker Swarm. <br /><br /> Container Service optimalizuje konfiguraci tyto platformy. Stačí vybrat velikost, počet hostitelů a požadované orchestrační nástroje a služby Container Service se postará o všechno ostatní. | Mesosphere DC/OS <br /><br /> Kubernetes <br /><br /> Docker Swarm |
| Docker Universal rovina řízení\(místní nebo v cloudu) | [Docker Universal rovina řízení](https://docs.docker.com/v1.11/ucp/overview/) je podnikové řešení pro správu clusteru od Dockeru. To vám pomůže spravovat celý cluster z jednoho místa. <br /><br /> Docker Universal rovina řízení se součástí obchodní produkt s názvem Docker Datacenter, která poskytuje Docker Swarm, Docker Universal rovina řízení a Docker Trusted Registry. <br /><br /> Docker Datacenter můžou být nainstalované na místním nebo zajištěného z veřejného cloudu, jako je Azure. | Docker Swarm\(podporované ve službě Container Service) |
| Docker cloudu\(označované také jako Tutum; cloudu SaaS) | [Docker cloudu](https://docs.docker.com/docker-cloud/) je služba pro správu hostované (SaaS), který poskytuje možnosti Orchestrace a registr Dockeru pomocí sestavení a testování zařízení pro Dockerized obrázky aplikace, nástroje, které vám pomůžou nastavit a spravovat infrastrukturu hostitele nasazení funkce a které vám pomůžou automatizovat nasazování imagí pro konkrétní infrastrukturu. Propojení účtu Docker cloudu SaaS pro vaši infrastrukturu v Container Service s cluster Docker Swarm. | Docker Swarm\(podporované ve službě Container Service) |
| Mesosphere Marathon\(místní nebo v cloudu) | [Marathon](https://mesosphere.github.io/marathon/docs/marathon-ui.html) je platforma Plánovač a Orchestrace kontejnerů na produkční úrovni od Mesosphere DC/OS a Apache Mesos. <br /><br /> Funguje s Mesos (DC/OS je založená na Apache Mesos) na ovládací prvek dlouhotrvající služeb a poskytuje [webového uživatelského rozhraní pro správu procesu a kontejneru](https://mesosphere.github.io/marathon/docs/marathon-ui.html). Umožňuje nástroj pro správu webového uživatelského rozhraní | Mesosphere DC/OS\(založené na Apache Mesos; podporované ve službě Container Service) |
| Google Kubernetes | [Kubernetes](https://kubernetes.io/docs/user-guide/ui/#dashboard-access) orchestraci, plánování a infrastruktura clusteru. Je open source platforma pro automatizaci nasazení, škálování a provoz kontejnerů aplikací napříč clustery hostitelů, poskytuje zaměřené na kontejner infrastruktury. | Google Kubernetes\(podporované ve službě Container Service) |

## <a name="azure-service-fabric"></a>Azure Service Fabric

Je další volbou pro správu a nasazení clusteru Azure Service Fabric. [Service Fabric](https://azure.microsoft.com/services/service-fabric/) je platforma mikroslužeb Microsoftu, která zahrnuje Orchestrace kontejnerů, jakož i pro vývojáře programovacích modelů pro vytváření vysoce škálovatelných mikroslužeb aplikací. Service Fabric podporuje Docker v aktuální verzi preview verze Linuxu, jako [náhled Service Fabric v Linuxu](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere)a pro kontejnery Windows [v další vydané verzi](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Nástroje pro správu Service Fabric jsou následující:

-   [Portál Azure portal pro Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal) operace související s clusterem (vytvoření/aktualizace/odstranění) clusteru nebo nakonfigurovat svou infrastrukturu (virtuální počítače, nástroj pro vyrovnávání zatížení, sítě atd.)

-   [Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) je nástroj specializované webové uživatelské rozhraní, které poskytují přehledy a určité operace v clusteru Service Fabric z hlediska uzly nebo virtuální počítače a z aplikace a služby pohledu.


>[!div class="step-by-step"]
[Předchozí](run-microservices-based-applications-in-production.md)
[další](monitor-containerized-application-services.md)
