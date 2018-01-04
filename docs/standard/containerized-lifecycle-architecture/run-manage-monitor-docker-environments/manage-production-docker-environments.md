---
title: "Spravovat produkční prostředí Docker"
description: "Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c962543004c88b0a6413cc22d8bdddf954af66f8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="manage-production-docker-environments"></a>Spravovat produkční prostředí Docker

Správa clusteru a orchestration je proces řízení skupinu hostitelů. To může zahrnovat přidání a odebrání hostitele z clusteru, získání informací o aktuálním stavu hostitelů a kontejnerů a spuštění a zastavení procesy. Správa clusteru a orchestraci jsou úzce svázané s plánování, protože plánovač musí mít přístup na každém hostiteli. v clusteru, aby bylo možné naplánovat služby. Z tohoto důvodu se často používá stejný nástroj pro oba účely.

## <a name="container-service-and-management-tools"></a>Kontejner služby a nástroje pro správu

Container Service umožňuje rychlé nasazení oblíbených open-source kontejneru clustering a orchestraci řešení. Zajistěte, aby vaše kontejnery aplikace plně přenositelné pomocí imagí Dockeru. Pomocí Container Service můžete nasadit (používá technologii Mesosphere a Apache Mesos) DC/OS a Docker Swarm clustery s šablon Azure Resource Manageru nebo portálu Azure k zajištění, že je možné škálovat tyto aplikace k tisícům – včetně desetitisíce – nástroje kontejnery.

Tyto clustery nasadíte pomocí sady škálování virtuálního počítače Azure, a clustery využívat nabídky Azure sítě a úložiště. K Container Service potřebujete předplatné Azure. S Container Service můžete využít výhod podnikové úrovni funkce Azure současně se zachovává přenositelnost aplikace, včetně na vrstvy orchestration.

Tabulka 6-1 jsou uvedeny běžné nástroje pro správu související s jejich orchestrators, plánovače a clustering platformy.

Nástroje pro správu Docker Tabulka 6-1:


| Nástroje pro správu      | Popis           | Související orchestrators |
|-----------------------|-----------------------|-----------------------|
| Container Service\(správu uživatelského rozhraní na portálu Azure) | [Službu kontejneru](https://azure.microsoft.com/en-us/services/container-service/) poskytuje snadno získat spuštění způsob, jak [nasadit cluster kontejneru ve službě Azure](https://docs.microsoft.com/azure/container-service/dcos-swarm/container-service-deployment) podle oblíbených orchestrators jako Mesosphere DC/OS, Kubernetes a Docker Swarm. <br /><br /> Container Service optimalizuje konfiguraci tyto platformy. Stačí vybrat velikost, počtu hostitelů a volba nástroje orchestrator a kontejner služba zpracovává nic jiného. | Mesosphere DC/OS <br /><br /> Kubernetes <br /><br /> Docker Swarm |
| Univerzální rovině řízení docker\(na pracovišti nebo v cloudu) | [Univerzální rovině řízení docker](https://docs.docker.com/v1.11/ucp/overview/) je řešení pro správu podnikové úrovni clusteru z Docker. Pomáhá spravovat celý cluster z jednoho místa. <br /><br /> Je součástí komerční produktu Docker datacentru, což poskytuje Docker Swarm, Docker Universal řídicí a Docker důvěryhodné registru s názvem docker Universal rovině řízení. <br /><br /> Docker Datacenter může být nainstalované místně nebo zajištěného z veřejného cloudu, jako je například Azure. | Docker Swarm\(nepodporuje Container Service) |
| Docker Cloud\(také označované jako Tutum; cloudu SaaS) | [Docker Cloud](https://docs.docker.com/docker-cloud/) je hostované správu služba (SaaS), která poskytuje funkce orchestration a Docker registru sestavení a testování zařízení pro Image aplikací Dockerized, nástroje vám pomůžou nastavit a spravovat infrastrukturu hostitele a nasazení funkce, které vám pomůžou automatizovat nasazení bitové kopie k infrastruktuře konkrétní. Váš účet SaaS Docker cloudu může připojit k vaší infrastruktury v kontejneru služby spuštěné clusteru Docker Swarm. | Docker Swarm\(nepodporuje Container Service) |
| Mesosphere Marathon\(na pracovišti nebo v cloudu) | [Marathon](https://mesosphere.github.io/marathon/docs/marathon-ui.html) je platforma orchestration a scheduler kontejneru produkční úrovni pro DC/OS a Apache Mesos Mesosphere společnosti. <br /><br /> Funguje s Mesos (DC/OS je založené na Apache Mesos) na ovládací prvek dlouhodobé služby a poskytuje [webové uživatelské rozhraní pro správu procesu a kontejner](https://mesosphere.github.io/marathon/docs/marathon-ui.html). Poskytuje nástroj pro správu webového uživatelského rozhraní | Mesosphere DC/OS\(podle Apache Mesos; nepodporuje Container Service) |
| Google Kubernetes | [Kubernetes](http://kubernetes.io/docs/user-guide/ui/#dashboard-access) zahrnuje Orchestrace, plánování a infrastruktura clusteru. Je open-source platformu pro automatizaci nasazení, škálování a operace kontejnery aplikací napříč clustery hostitelů, poskytuje zaměřené na kontejner infrastruktury. | Google Kubernetes\(nepodporuje Container Service) |

## <a name="azure-service-fabric"></a>Azure Service Fabric

Další možnost pro správu a nasazení clusteru je Azure Service Fabric. [Service Fabric](https://azure.microsoft.com/en-us/services/service-fabric/) je mikroslužeb platformu Microsoft, která zahrnuje kontejneru orchestration, jakož i vývojáře programovací modely k vytváření vysoce škálovatelných mikroslužeb aplikací. Service Fabric podporuje Docker v aktuální verze preview Linux, jako v [preview Service Fabric v systému Linux](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere)a pro Windows kontejnery [v příštím vydání](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Toto jsou nástroje pro správu Service Fabric:

-   [Portál Azure pro Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal) operací souvisejících s clusteru (vytvoření, aktualizace nebo odstranění) clusteru nebo nakonfigurovat svou infrastrukturu (virtuální počítače, nástroj pro vyrovnávání zatížení sítě, atd.)

-   [Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) je nástroj uživatelského rozhraní specializované web, který poskytuje přehled a určité operace na clusteru Service Fabric z hlediska uzly nebo virtuální počítače a z aplikace a služby hlediska.


>[!div class="step-by-step"]
[Předchozí] (run-microservices-based-applications-in-production.md) [Další] (monitorování kontejnerizované aplikace services.md)
