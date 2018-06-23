---
title: Technologie Microsoftu v aplikacích optimalizovaných Cloudů
description: Modernizovat existující aplikace .NET s kontejnery cloudu Azure a Windows | Technologie Microsoftu v aplikacích optimalizovaných Cloudů
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 3c5886dc3583a5d4a6cc9566556edbe1822ad6d1
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2018
ms.locfileid: "36315177"
---
# <a name="microsoft-technologies-in-cloud-optimized-applications"></a>Technologie Microsoftu v aplikacích optimalizovaných cloudů

Následující seznam popisuje nástroje, technologií a řešení, které jsou rozpoznána jako požadavky optimalizovaný pro cloudové aplikace. Elementy optimalizovaných Cloudů může přijmout selektivně nebo postupně, v závislosti na vašich priorit.

-   **Infrastruktura cloudu**: infrastruktury, který poskytuje výpočetní platforma, operačního systému, sítě a úložiště. Microsoft Azure je nastavený na této úrovni.

-   **Modul runtime**: Tato vrstva nabízí prostředí pro spuštění aplikace. Pokud používáte kontejnery, tato vrstva obvykle podle [modulu Docker](https://docs.docker.com/engine/), spuštěné v hostitelích Linux nebo na hostitelích systému Windows. ([Windows kontejnery](https://docs.microsoft.com/virtualization/windowscontainers/about/) jsou podporované od verze systému Windows Server 2016. Kontejnery Windows je nejlepší volbou pro existující aplikace rozhraní .NET Framework, které běží v systému Windows.)

-   **Spravované cloudové**: Pokud si zvolíte možnost spravovanou cloudovou, se můžete vyhnout se nákladům a složitým Správa a podpora základní infrastrukturu, virtuální počítače, opravy operačního systému a konfiguraci sítě. Pokud si zvolíte migrace pomocí IaaS, jste odpovědni pro všechny tyto úlohy a souvisejících nákladů. V možnosti spravované cloudu spravovat jenom aplikace a služby, které vyvíjíte. Poskytovatel cloudové služby obvykle spravuje nic jiného. Examples of managed cloud services in Azure include [Azure SQL Database](https://azure.microsoft.com/services/sql-database), [Azure Redis Cache](https://azure.microsoft.com/services/cache/), [Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/), [Azure Storage](https://azure.microsoft.com/services/storage/), [Azure Database for MySQL](https://azure.microsoft.com/services/mysql/), [Azure Database for PostgreSQL](https://azure.microsoft.com/services/postgresql/), [Azure Active Directory](https://azure.microsoft.com/services/active-directory/), and managed compute services like [VM scale sets](https://azure.microsoft.com/services/virtual-machine-scale-sets/), [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/), [Azure App Service](https://azure.microsoft.com/services/app-service/), and [Azure Kubernetes Service](https://azure.microsoft.com/services/container-service/).

-   **Vývoj aplikací**: můžete vybrat z mnoha jazycích při sestavování aplikací, které běží v kontejnerech. Tato příručka se zaměřuje na [.NET](https://www.microsoft.com/net), ale můžete vyvíjet aplikace založené na kontejneru pomocí jiných jazyků, jako je pružiny Node.js, Python, nebo Java, nebo přejděte.

-   **Monitorování, telemetrie, protokolování a auditování**: možnost sledování a audit aplikací a kontejnerů, které běží v cloudu je důležité pro každou aplikaci, optimalizovaných Cloudů. [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) a [Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite) hlavní nástroje Microsoft, které poskytují sledování a auditování pro optimalizovaný pro cloudové aplikace.

-   **Zřizování**: nástrojům pro automatizaci můžete zřídit infrastruktury a nasadit aplikace do prostředí s více (produkční, testování, pracovní). Nástroje jako Chef nebo Puppet slouží ke správě konfigurace a prostředí dané aplikace. Tuto vrstvu lze také implementovat pomocí jednodušší a více direct přístupy. Například můžete nasadit přímo pomocí rozhraní příkazového řádku Azure (Azure CLI) nástrojů a pak použijte průběžné nasazování a release management kanály v [Visual Studio Team Services](https://visualstudio.microsoft.com/team-services/).

-   **Životní cyklus aplikace**: [Visual Studio Team Services](https://visualstudio.microsoft.com/team-services/) a dalších nástrojů, jako je volaných, jsou integrované automatizační servery, které vám pomohou implementovat CI/CD kanály, včetně správy verzí.

V dalších částech této kapitoly a související návody zaměřuje konkrétně na podrobnosti o vrstvě runtime (Windows kontejnery). Pokyny popisuje způsoby, jak můžete nasadit kontejnery Windows na Windows Server 2016 (nebo novější verze) virtuálních počítačů a instancí Azure kontejneru. Také vysvětluje pokročilejší PaaS platformách, jako je Azure App Service a orchestrator jako Azure Service Fabric a Kubernetes služby Azure.

## <a name="monolithic-applications-can-be-cloud-optimized"></a>Monolitický aplikace *můžete* být optimalizovaných Cloudů

Je důležité, abyste měli na očích které monolitický aplikace (aplikace, které nejsou založené na mikroslužeb) *můžete* optimalizovaných Cloudů aplikacemi. Můžete sestavit a pracovat monolitický aplikací využívajících cloud computing modelu pomocí kombinace kontejnery, nastavené průběžné doručování a DevOps. Pokud stávající aplikaci monolitický správné pro obchodní cíle, můžete ho modernizovat a nastavit jej jako optimalizovaných Cloudů.

Podobně pokud monolitický aplikace mohou být optimalizované cloudové aplikace, architektury, které složitější jako vícevrstvé aplikace může také být modernized jako optimalizovaný pro cloudové aplikace.

>[!div class="step-by-step"]
[Předchozí](reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md)
[další](what-about-cloud-native-applications.md)
