---
title: Monitorování kontejnerizovaných aplikačních služeb
description: Seznamte se s některými klíčovými aspekty monitorování architektury kontejnerů
ms.date: 02/15/2019
ms.openlocfilehash: e14553d510751d8a75020a1b6beb9fd7bc29596e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295619"
---
# <a name="monitor-containerized-application-services"></a>Monitorování kontejnerizovaných aplikačních služeb

Je důležité pro aplikace rozdělené do více kontejnerů a mikroslužeb mít způsob, jak sledovat a analyzovat chování celé aplikace.

## <a name="azure-monitor"></a>Azure Monitor

[Azure Monitor](https://azure.microsoft.com/services/monitor/) je rozšiřitelná analytická služba, která monitoruje vaši živou aplikaci. Pomáhá vám odhalit a diagnostikovat problémy s výkonem a pochopit, co uživatelé skutečně dělají s vaší aplikací. Je určen pro vývojáře s cílem pomoci vám neustále zlepšovat výkon a použitelnost vašich služeb nebo aplikací. Azure Monitor funguje s webovými a samostatnými aplikacemi na široké škále platforem, jako jsou .NET, Java, Node.js a mnoho dalších platforem, hostované místně nebo v cloudu.

### <a name="additional-resources"></a>Další zdroje

- **Přehled Azure Monitoru** \
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- **Co je Application Insights?** \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **Co je metriky Azure Monitor?** \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- **Řešení monitorování kontejnerů ve službě Azure Monitor** \
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a>Zabezpečení a zálohování

Existuje mnoho podpůrných činností se spoustou detailů, které musíte zvládnout, abyste zajistili, že vaše aplikace a infrastruktura jsou v špičkovém stavu pro podporu obchodních potřeb a situace se stává složitější v oblasti mikroslužeb, takže potřebujete způsob, jak mají jak na vysoké úrovni, tak podrobné pohledy, když potřebujete jednat.

Azure má nástroje pro správu a poskytování jednotného zobrazení čtyř důležitých aspektů cloudových i místních prostředků:

- **Bezpečnost**. S [Azure Security Center](https://azure.microsoft.com/services/security-center/).
  - Získejte plnou viditelnost a kontrolu nad zabezpečením vašich virtuálních počítačů, aplikací a úloh.
  - Centralizujte správu svých zásad zabezpečení a integrujte stávající procesy a nástroje.
  - Detekujte skutečné hrozby pomocí pokročilých analýz.

- **Zálohování**. S [Azure Backup](https://azure.microsoft.com/services/backup/).
  - Vyhněte se nákladným narušením podnikání, splníte cíle dodržování předpisů a chraňte svá data před ransomwarem a lidskými chybami.
  - Uchovávejte záložní data šifrovaná při přenosu a v klidovém stavu.
  - Zajistěte přístup na základě vícefaktorového ověřování, abyste zabránili neoprávněnému použití.

- **Místní prostředky**. S [opravdu konzistentním hybridním cloudem](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).

>[!div class="step-by-step"]
>[Předchozí](manage-production-docker-environments.md)
>[další](../key-takeaways/index.md)
