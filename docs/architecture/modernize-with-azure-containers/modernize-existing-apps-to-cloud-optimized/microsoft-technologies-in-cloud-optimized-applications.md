---
title: Technologie Microsoftu v aplikacích optimalizovaných pro cloud
description: Modernizace stávajících aplikací .NET pomocí Azure Cloudu a kontejnerů Windows | Technologie Microsoftu v aplikacích optimalizovaných pro cloud
ms.date: 04/28/2018
ms.openlocfilehash: c5222ba13258f9c8a40ca3b9ce240aeb9f41da63
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546507"
---
# <a name="microsoft-technologies-in-cloud-optimized-applications"></a>Technologie Microsoftu v cloudových aplikacích

Následující seznam popisuje nástroje, technologie a řešení, které jsou rozpoznány jako požadavky na aplikace optimalizované pro cloud. V závislosti na vašich prioritách můžete přijímat prvky optimalizované pro cloud selektivně nebo postupně.

- **Cloudová infrastruktura**: Infrastruktura, která poskytuje výpočetní platformu, operační systém, síť a úložiště. Microsoft Azure je umístěn na této úrovni.

- **Runtime**: Tato vrstva poskytuje prostředí pro spuštění aplikace. Pokud používáte kontejnery, tato vrstva je obvykle založena na [Docker Engine](https://docs.docker.com/engine/), běží buď na linuxových hostitelích nebo na hostitelích systému Windows. ([Kontejnery systému Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) jsou podporovány počínaje windows serverem 2016. Kontejnery systému Windows jsou nejlepší volbou pro existující aplikace rozhraní .NET Framework, které běží v systému Windows.)

- **Spravovaný cloud**: Když zvolíte možnost spravovaného cloudu, můžete se vyhnout nákladům a složitosti správy a podpory základní infrastruktury, virtuálních počítačů, oprav operačních systémů a konfigurace sítě. Pokud se rozhodnete migrovat pomocí služby IaaS, jste zodpovědní za všechny tyto úkoly a za související náklady. V možnosti spravovaného cloudu spravujete jenom aplikace a služby, které vyvíjíte. Poskytovatel cloudových služeb obvykle spravuje vše ostatní. Příklady spravovaných cloudových služeb v Azure zahrnují [Azure SQL Database](https://azure.microsoft.com/services/sql-database), Azure [Redis Cache](https://azure.microsoft.com/services/cache/), Azure [Cosmos DB](https://azure.microsoft.com/services/cosmos-db/), Azure [Storage](https://azure.microsoft.com/services/storage/), Azure Database [for MySQL](https://azure.microsoft.com/services/mysql/), [Azure Database for PostgreSQL](https://azure.microsoft.com/services/postgresql/), [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)a spravované výpočetní služby, jako jsou [škálovací sady virtuálních montoslužeb](https://azure.microsoft.com/services/virtual-machine-scale-sets/)pro virtuální počítače , [Azure App Service](https://azure.microsoft.com/services/app-service/)a [Azure Kubernetes Service](https://azure.microsoft.com/services/container-service/).

- **Vývoj aplikací**: Můžete si vybrat z mnoha jazyků při vytváření aplikací, které běží v kontejnerech. Tato příručka se zaměřuje na [rozhraní .NET](https://dotnet.microsoft.com), ale můžete vyvíjet aplikace založené na kontejnerech pomocí jiných jazyků, jako je Node.js, Python, Jaro/Java nebo Go.

- **Monitorování, telemetrie, protokolování a auditování**: Možnost monitorování a auditování aplikací a kontejnerů spuštěných v cloudu je důležitá pro všechny aplikace optimalizované pro cloud. [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) a [Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite) jsou hlavní nástroje Microsoftu, které poskytují monitorování a auditování aplikací optimalizovaných pro cloud.

- **Zřizování**: Nástroje automatizace vám pomohou zřídit infrastrukturu a nasadit aplikaci do více prostředí (výroba, testování, pracovní). Pomocí nástrojů, jako je Chef a Puppet, můžete spravovat konfiguraci a prostředí aplikace. Tato vrstva může být také implementována pomocí jednodušších a přímějších přístupů. Můžete například nasadit přímo pomocí nástrojů rozhraní příkazového řádku Azure (Azure CLI) a potom použít kanály pro průběžné nasazení a správu verzí ve [službách Azure DevOps](https://azure.microsoft.com/services/devops/)Services .

- **Životní cyklus aplikací**: [Azure DevOps Services](https://azure.microsoft.com/services/devops/) a další nástroje, jako je Jenkins, jsou integrované automatizační servery, které vám pomohou implementovat kanály CI/CD, včetně správy verzí.

Další části této kapitoly a související návody se zaměřují konkrétně na podrobnosti o vrstvě runtime (kontejnery systému Windows). Pokyny popisují způsoby nasazení kontejnerů Windows na virtuálních počítačích Windows Server 2016 (a novějších verzích) a instanci kontejnerů Azure. Zahrnuje také pokročilejší platformy PaaS, jako je Služba Azure App Service a orchestrator, jako je služba Azure Kubernetes.

## <a name="monolithic-applications-can-be-cloud-optimized"></a>Monolitické aplikace *mohou* být optimalizovány pro cloud

Je důležité zdůraznit, že monolitické aplikace (aplikace, které nejsou založeny na mikroslužbách) *mohou* být aplikace optimalizované pro cloud. Můžete vytvářet a provozovat monolitické aplikace, které využívají výhod modelu cloud computingu pomocí kombinace kontejnerů, nepřetržitého doručování a DevOps. Pokud je stávající monolitická aplikace vhodná pro vaše obchodní cíle, můžete ji modernizovat a optimalizovat cloudem.

Podobně pokud monolitické aplikace mohou být aplikace optimalizované pro cloud, jiné, složitější architektury, jako jsou n-vrstvé aplikace, mohou být také modernizovány jako aplikace optimalizované pro cloud.

>[!div class="step-by-step"]
>[Předchozí](reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md)
>[další](what-about-cloud-native-applications.md)
