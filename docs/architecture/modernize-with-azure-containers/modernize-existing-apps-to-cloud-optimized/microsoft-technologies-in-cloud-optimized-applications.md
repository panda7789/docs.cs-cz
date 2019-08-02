---
title: Technologie Microsoftu v cloudově optimalizovaných aplikacích
description: Modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows | Technologie Microsoftu v cloudově optimalizovaných aplikacích
ms.date: 04/28/2018
ms.openlocfilehash: 915aa99d2331c5b9c46eabef3335fb809baa9370
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676994"
---
# <a name="microsoft-technologies-in-cloud-optimized-applications"></a>Technologie Microsoftu v cloudově optimalizovaných aplikacích

Následující seznam popisuje nástroje, technologie a řešení, které se rozpoznávají jako požadavky na aplikace optimalizované pro Cloud. V závislosti na vašich prioritách můžete v závislosti na svých prioritách přijmout selektivně nebo postupně optimalizované cloudové prvky.

- **Infrastruktura cloudu**: Infrastruktura, která poskytuje výpočetní platformu, operační systém, síť a úložiště. Microsoft Azure je umístěn na této úrovni.

- **Modul runtime**: Tato vrstva poskytuje prostředí, které má aplikace běžet. Pokud používáte kontejnery, tato vrstva je obvykle založená na [modulu Docker](https://docs.docker.com/engine/), který běží na hostitelích se systémem Linux nebo na hostitelích se systémem Windows. ([Kontejnery Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) se podporují od windows serveru 2016. Kontejnery Windows jsou nejlepší volbou pro existující aplikace .NET Framework spuštěné v systému Windows.)

- **Spravovaný Cloud**: Když zvolíte možnost spravovaného cloudu, můžete se vyhnout nákladům a složitosti správy a podpory základní infrastruktury, virtuálních počítačů, oprav operačního systému a konfigurace sítě. Pokud se rozhodnete migrovat pomocí IaaS, zodpovídáte za všechny tyto úkoly a pro související náklady. V případě možnosti spravovaného cloudu budete spravovat jenom aplikace a služby, které vyvíjíte. Poskytovatel cloudové služby obvykle spravuje všechno ostatní. Příklady spravovaných cloudových služeb v Azure zahrnují [Azure SQL Database](https://azure.microsoft.com/services/sql-database), [Azure Redis Cache](https://azure.microsoft.com/services/cache/), [Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/), [Azure Storage](https://azure.microsoft.com/services/storage/), [Azure Database for MySQL](https://azure.microsoft.com/services/mysql/), [Azure Database for PostgreSQL](https://azure.microsoft.com/services/postgresql/), [Azure Active. Adresář](https://azure.microsoft.com/services/active-directory/)a spravované výpočetní služby, jako jsou [VM Scale sets](https://azure.microsoft.com/services/virtual-machine-scale-sets/), [Azure App Service](https://azure.microsoft.com/services/app-service/)a [Azure Kubernetes Service](https://azure.microsoft.com/services/container-service/).

- **Vývoj aplikací**: Při sestavování aplikací, které běží v kontejnerech, si můžete vybrat z mnoha jazyků. Tato příručka se zaměřuje na [rozhraní .NET](https://www.microsoft.com/net), ale můžete vyvíjet aplikace založené na kontejnerech pomocí jiných jazyků, jako je Node. js, Python, pružina/Java nebo přejít.

- **Monitorování, telemetrie, protokolování a auditování**: Možnost monitorování a auditu aplikací a kontejnerů, které běží v cloudu, je zásadní pro libovolnou cloudově optimalizovanou aplikaci. [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) a [Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite) jsou hlavní nástroje Microsoftu, které poskytují monitorování a auditování pro cloudově optimalizované aplikace.

- **Zřizování**: Nástroje pro automatizaci vám pomůžou zřídit infrastrukturu a nasadit aplikaci do několika prostředí (produkční, testovací, fázování). Ke správě konfigurace a prostředí aplikace můžete použít nástroje, jako je třeba Puppet. Tato vrstva se dá implementovat taky pomocí jednodušších a přímých přístupů. Například můžete nasadit přímo pomocí nástrojů rozhraní příkazového řádku Azure (Azure CLI) a potom použít kanály pro průběžné nasazování a správu verzí v [Azure DevOps Services](https://azure.microsoft.com/services/devops/).

- **Životní cyklus aplikace**: [Azure DevOps Services](https://azure.microsoft.com/services/devops/) a další nástroje, jako je Jenkinse, jsou sestavené automatizační servery, které vám pomůžou s implementací kanálů CI/CD, včetně Release managementu.

V dalších částech této kapitoly a souvisejících návodech se zaměřujete konkrétně na podrobnosti o vrstvě prostředí runtime (kontejnery Windows). Pokyny popisují způsoby nasazení kontejnerů Windows na virtuální počítače s Windows serverem 2016 (a novějšími verzemi) a Azure Container Instances. Zahrnuje taky pokročilejší PaaS platformy, jako je Azure App Service a Orchestrator, jako je třeba služba Azure Kubernetes.

## <a name="monolithic-applications-can-be-cloud-optimized"></a>Aplikace monolitické *můžou* být optimalizované pro Cloud.

Je důležité zdůraznit, že aplikace monolitické (aplikace, které nejsou založené na mikroslužbách), *můžou* být cloudově optimalizované aplikace. Můžete vytvářet a provozovat monolitické aplikace, které využívají model cloud computingu, a to pomocí kombinace kontejnerů, průběžného doručování a DevOps. Pokud je existující aplikace monolitické vhodná pro vaše obchodní cíle, můžete ji modernizovat a zajistit její optimalizaci pro Cloud.

Podobně platí, že pokud aplikace monolitické můžou být cloudově optimalizované aplikace, jiné a složitější architektury, jako jsou N-vrstvé aplikace, je také možné moderní jako cloudově optimalizované aplikace.

>[!div class="step-by-step"]
>[Předchozí](reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md)Další
>[](what-about-cloud-native-applications.md)
