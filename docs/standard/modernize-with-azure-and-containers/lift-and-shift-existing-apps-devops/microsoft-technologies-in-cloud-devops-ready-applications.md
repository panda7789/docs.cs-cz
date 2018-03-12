---
title: "Technologie Microsoftu v cloudové aplikace devops připravené pro použití"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Technologie Microsoftu v DevOps připravené pro cloudové aplikace"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 66579905ad2694cf08950d0c0a69e2405ab2c1ee
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2018
---
# <a name="microsoft-technologies-in-cloud-devops-ready-applications"></a>Technologie Microsoftu v cloudové aplikace devops připravené pro použití

Následující seznam popisuje nástroje, technologií a řešení, které jsou rozpoznána jako požadavky aplikace připravené pro DevOps cloudu. Aplikace připravené pro Cloud DevOps může přijmout selektivně nebo postupně, v závislosti na vašich priorit.

-   **Infrastruktura cloudu**: infrastruktury, který poskytuje výpočetní platforma, operačního systému, sítě a úložiště. Microsoft Azure je nastavený na této úrovni.

-   **Modul runtime**: Tato vrstva nabízí prostředí pro spuštění aplikace. Pokud používáte kontejnery, tato vrstva obvykle podle [modulu Docker](https://docs.docker.com/engine/), spuštěné v hostitelích Linux nebo na hostitelích systému Windows. ([Windows kontejnery](https://docs.microsoft.com/virtualization/windowscontainers/about/) jsou podporované od verze systému Windows Server 2016. Kontejnery Windows je nejlepší volbou pro existující aplikace rozhraní .NET Framework, které běží v systému Windows.)

-   **Spravované cloudové**: Pokud si zvolíte možnost spravovanou cloudovou, se můžete vyhnout se nákladům a složitým Správa a podpora základní infrastrukturu, virtuální počítače, opravy operačního systému a konfiguraci sítě. Pokud si zvolíte migrace pomocí IaaS, jste odpovědni pro všechny tyto úlohy a souvisejících nákladů. V možnosti spravované cloudu spravovat jenom aplikace a služby, které vyvíjíte. Poskytovatel cloudové služby obvykle spravuje nic jiného. Příklady spravované cloudové služby v Azure [Azure SQL Database](https://azure.microsoft.com/services/sql-database), [Azure Redis Cache](https://azure.microsoft.com/services/cache/), [Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/), [Azure Storage](https://azure.microsoft.com/services/storage/), [Azure Database pro databázi MySQL](https://azure.microsoft.com/services/mysql/), [databáze Azure pro PostgreSQL](https://azure.microsoft.com/services/postgresql/), [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)a spravovat výpočetní služby, jako je [škálování virtuálních počítačů Nastaví](https://azure.microsoft.com/services/virtual-machine-scale-sets/), [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/), [Azure App Service](https://azure.microsoft.com/services/app-service/), a [Azure Container Service](https://azure.microsoft.com/services/container-service/).

-   **Vývoj aplikací**: můžete vybrat z mnoha jazycích při sestavování aplikací, které běží v kontejnerech. V této příručce se zaměříme na [.NET](https://www.microsoft.com/net), ale vyvíjíte aplikace založené na kontejneru pomocí jiných jazyků, jako je Node.js, Python, pružiny nebo Java nebo GoLang.

-   **Monitorování, telemetrie, protokolování a auditování**: je důležité pro každou aplikaci, DevOps Cloud-Ready umožňuje sledování a audit aplikací a kontejnerů, které běží v cloudu. [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) a [Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite) hlavní nástroje Microsoft, které poskytují sledování a auditování pro aplikace připravené pro DevOps cloudu.

-   **Zřizování**: nástrojům pro automatizaci můžete zřídit infrastruktury a nasadit aplikace do prostředí s více (produkční, testování, pracovní). Nástroje jako Chef nebo Puppet slouží ke správě konfigurace a prostředí dané aplikace. Tuto vrstvu lze také implementovat pomocí jednodušší a více direct přístupy. Například můžete nasadit přímo pomocí rozhraní příkazového řádku Azure (Azure CLI) nástrojů a pak použijte průběžné nasazování a release management kanály v [Visual Studio Team Services](https://www.visualstudio.com/team-services/).

-   **Životní cyklus aplikace**: [Visual Studio Team Services](https://www.visualstudio.com/team-services/) a dalších nástrojů, jako je volaných, jsou sestavení automatizační servery, které vám pomohou implementovat CI/CD kanály, včetně správy verzí.

V dalších částech této kapitoly a související návody zaměřuje konkrétně na podrobnosti o vrstvě runtime (Windows kontejnery). Pokyny popisuje způsoby, jak můžete nasadit virtuální počítače Windows kontejnery na Windows Server 2016 (nebo novější verze). Popisuje také pokročilejší orchestrator vrstvy, jako je Azure Service Fabric, Kubernetes a Azure Container Service. Nastavení vrstvy orchestrator je základní požadavek pro modernizace existující rozhraní .NET Framework () aplikace pro systém Windows jako DevOps připravené pro cloudové aplikace.

## <a name="monolithic-applications-can-be-cloud-devops-ready"></a>Monolitický aplikace *můžete* DevOps připraví cloudu

Je důležité, abyste měli na očích které monolitický aplikace (aplikace, které nejsou založené na mikroslužeb) *můžete* DevOps Cloud-Ready aplikacemi. Můžete sestavit a pracovat monolitický aplikací využívajících cloud computing modelu pomocí kombinace kontejnery, nastavené průběžné doručování a DevOps. Pokud stávající aplikaci monolitický správné pro obchodní cíle, můžete ho modernizovat a nastavit jej jako DevOps Cloud-Ready.

Podobně pokud monolitický aplikace mohou být DevOps připravené pro cloudové aplikace, architektury, které složitější jako vícevrstvé aplikace také může být modernized jako DevOps připravené pro cloudové aplikace.

>[!div class="step-by-step"]
[Předchozí](reasons-to-lift-and-shift-existing-net-apps-to-cloud-devops-ready-applications.md)
[další](what-about-cloud-optimized-applications.md)
