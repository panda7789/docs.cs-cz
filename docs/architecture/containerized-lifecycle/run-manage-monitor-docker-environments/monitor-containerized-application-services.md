---
title: Monitorování kontejnerizovaných aplikačních služeb
description: Seznamte se s klíčovými aspekty monitorování architektur kontejnerů
ms.date: 08/06/2020
ms.openlocfilehash: 5fcb5065d02018ab3c2d3ad71cf507bd43b53446
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87914941"
---
# <a name="monitor-containerized-application-services"></a>Monitorování kontejnerizovaných aplikačních služeb

Je důležité pro aplikace rozdělené do několika kontejnerů a mikroslužeb, aby měly možnost monitorovat a analyzovat chování celé aplikace.

## <a name="azure-monitor"></a>Azure Monitor

[Azure monitor](https://azure.microsoft.com/services/monitor/) je rozšiřitelná analytická služba, která monitoruje vaši živou aplikaci. Pomáhá detekovat a diagnostikovat problémy s výkonem a pochopit, co uživatelé s vaší aplikací skutečně dělají. Je navržená pro vývojáře s cílem pomoci při neustálém vylepšování výkonu a použitelnosti služeb nebo aplikací. Azure Monitor spolupracuje s webovými i službami a samostatnými aplikacemi na nejrůznějších platformách, jako je .NET, Java, Node.js a spousta dalších platforem, které jsou hostované místně nebo v cloudu.

### <a name="additional-resources"></a>Další zdroje

- **Přehled Azure Monitor** \
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- **Co je Application Insights?** \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **Co je Azure Monitor metriky?** \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- **Řešení pro monitorování kontejnerů v Azure Monitor** \
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a>Služby zabezpečení a zálohování

Existuje mnoho rutinní podpory s mnoha podrobnostmi, které je třeba zvládnout, abyste zajistili, že vaše aplikace a infrastruktura jsou ve stavu nejvyšší úrovně, aby podporovaly obchodní potřeby, a situace se ve sféře mikroslužeb bude složitá, takže potřebujete způsob, jak mít jak zobrazení vysoké úrovně, tak podrobné zobrazení, pokud potřebujete provést akci.

Azure má nástroje pro správu a nabízí jednotný přehled čtyř důležitých aspektů cloudových i místních prostředků:

- **Zabezpečení**. S [Azure Security Center](https://azure.microsoft.com/services/security-center/).
  - Získejte úplnou viditelnost a kontrolu nad zabezpečením vašich virtuálních počítačů, aplikací a úloh.
  - Soustřeďte správu zásad zabezpečení a integrujte stávající procesy a nástroje.
  - Detekuje reálné hrozby pomocí pokročilých analýz.

- **Zálohování**. S [Azure Backup](https://azure.microsoft.com/services/backup/).
  - Vyhněte se nákladným výpadkům podniku, doplněním cílů dodržování předpisů a ochraně vašich dat před ransomwarem a lidskou chybou.
  - Zajistěte, aby byla zálohovaná data šifrovaná při přenosu a v klidovém stavu.
  - Zajistěte přístup na základě vícefaktorového ověřování, abyste zabránili neoprávněnému použití.

- **Místní prostředky**. Pomocí [hybridních cloudových řešení](https://azure.microsoft.com/solutions/hybrid-cloud-app/).

>[!div class="step-by-step"]
>[Předchozí](manage-production-docker-environments.md) 
> [Další](../key-takeaways/index.md)
