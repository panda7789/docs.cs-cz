---
title: Technologie Microsoft v aplikace optimalizované pro Cloud
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a Windows kontejnery | Technologie Microsoft v aplikace optimalizované pro Cloud
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 21ba318c3a59175dadde86ff247c6e41e7f85c0b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64627285"
---
# <a name="microsoft-technologies-in-cloud-optimized-applications"></a>Technologie Microsoft v aplikace optimalizované pro cloud

Následující seznam popisuje nástroje, technologie a řešení, které jsou rozpoznány jako požadavky pro Cloud optimalizovaný aplikací. Optimalizované pro Cloud prvky můžete přijmout selektivně nebo postupně, v závislosti na vašich priorit.

- **Cloudová Infrastruktura**: Infrastrukturu, která poskytuje výpočetní platforma, operačního systému, sítě a úložiště. Microsoft Azure je umístěn na této úrovni.

- **Modul runtime**: Tato vrstva nabízí prostředí pro spuštění aplikace. Pokud používáte kontejnery, tuto vrstvu obvykle je na základě [modul Docker](https://docs.docker.com/engine/); běží na hostiteli systému Linux nebo na hostitelích s Windows. ([Kontejnery Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) jsou podporované od verze Windows serveru 2016. Kontejnery Windows je nejlepší volbou pro existující aplikace .NET Framework, které běží na Windows).

- **Spravované cloudové**: Když zvolíte možnost spravovaného cloudu, můžete vyhnout nákladům a správa a podpora základního oprav operačního systému virtuálních počítačích, infrastruktury a konfiguraci sítě. Pokud budete chtít migrovat pomocí IaaS, budete muset pro všechny tyto úlohy a související náklady. V spravované cloudové možnosti spravovat jenom aplikace a služby, které vyvíjíte. Poskytovatel cloudové služby obvykle spravuje všechno ostatní. Příklady spravované cloudové služby v Azure [Azure SQL Database](https://azure.microsoft.com/services/sql-database), [Azure Redis Cache](https://azure.microsoft.com/services/cache/), [služby Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/), [služby Azure Storage](https://azure.microsoft.com/services/storage/), [– Azure Database for MySQL](https://azure.microsoft.com/services/mysql/), [– Azure Database for PostgreSQL](https://azure.microsoft.com/services/postgresql/), [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)a spravovat výpočetních služeb, jako je [škálování virtuálního počítače Nastaví](https://azure.microsoft.com/services/virtual-machine-scale-sets/), [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/), [služby Azure App Service](https://azure.microsoft.com/services/app-service/), a [Azure Kubernetes Service](https://azure.microsoft.com/services/container-service/).

- **Vývoj aplikací**: Při sestavování aplikace, které běží v kontejnerech, můžete vybrat z mnoha jazyků. Tato příručka se zaměřuje na [.NET](https://www.microsoft.com/net), ale můžete vyvíjet aplikace založené na kontejnerech s použitím jiných jazycích, jako je Java nebo Node.js, Python, Spring, nebo se vrátit.

- **Monitorování telemetrických dat, protokolování a auditování**: Umožňuje sledovat a auditovat aplikací a kontejnerů, které běží v cloudu je zásadní pro všechny aplikace optimalizované pro Cloud. [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) a [Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite) jsou hlavní nástroje Microsoft, které umožňují sledování a auditování pro Cloud optimalizovaný aplikací.

- **Zřizování**: Automatizační nástroje vám pomůžou zřízení infrastruktury a nasadit aplikaci do více prostředí (výrobu, testovací, přípravné). Nástroje, jako je Chef nebo Puppet můžete použít ke správě prostředí a konfigurace aplikací. Tuto vrstvu můžete implementovat také pomocí jednodušeji a přístupy. Například můžete nasadit přímo pomocí rozhraní příkazového řádku Azure (Azure CLI) nástroje a pak použijte průběžné nasazování a vydávání kanálů správy v [Azure DevOps služby](https://azure.microsoft.com/services/devops/).

- **Životní cyklus aplikace**: [Služby Azure DevOps](https://azure.microsoft.com/services/devops/) a další nástroje, jako je Jenkins, jsou sestavené automatizační servery, které vám pomohou implementovat kanálů CI/CD, včetně produktu release management.

Další části této kapitole a souvisejících návodů, konkrétně zaměřit podrobnosti o modulu runtime vrstvy (kontejnery Windows). Návod popisuje způsoby, kterými můžete nasadit kontejnery Windows ve Windows serveru 2016 (a novějších verzích) virtuálních počítačů a Azure Container Instances. Věnuje se také pokročilejší platformy PaaS, jako je Azure App Service a orchestrátor, jako je Azure Service Fabric a službě Azure Kubernetes.

## <a name="monolithic-applications-can-be-cloud-optimized"></a>Monolitické aplikace *můžete* být optimalizované pro Cloud

Je důležité, abyste měli na očích monolitických aplikací (aplikace, které nejsou založené na mikroslužbách) *můžete* být aplikace optimalizované pro Cloud. Můžete vytvářet a provozovat monolitické aplikace, které budou využívat cloud computingu modelu s použitím kombinace kontejnerů, průběžné doručování a DevOps. Pokud stávající monolitické aplikace hodí pro vaše obchodní cíle, můžete ji modernizovat a nastavte ji optimalizovaných pro Cloud.

Podobně pokud monolitické aplikace mohou být aplikace optimalizované pro Cloud, jiné, složitější architektury, jako je N-vrstvé aplikace může také být modernizovala jako aplikace optimalizované pro Cloud.

>[!div class="step-by-step"]
>[Předchozí](reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md)
>[další](what-about-cloud-native-applications.md)