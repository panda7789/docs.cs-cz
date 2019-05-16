---
title: Monitorování kontejnerizovaných aplikačních služeb
description: Přečtěte si některé klíčové aspekty monitorování kontejneru architektury
ms.date: 02/15/2019
ms.openlocfilehash: e14553d510751d8a75020a1b6beb9fd7bc29596e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641225"
---
# <a name="monitor-containerized-application-services"></a>Monitorování kontejnerizovaných aplikačních služeb

Je velmi důležité pro aplikace rozdělit do několika kontejnery a mikroslužby způsob, jak monitorovat a analyzovat chování celou aplikaci.

## <a name="azure-monitor"></a>Azure Monitor

[Azure Monitor](https://azure.microsoft.com/services/monitor/) je rozšiřitelnou analytickou službu, která monitoruje vaše živé aplikace. Pomáhá detekovat a diagnostikovat problémy s výkonem a pochopit, co uživatelé dělají s vaší aplikací. Je určená pro vývojáře se záměrem pomáhá průběžně zlepšit výkon a použitelnost služby nebo aplikace. Azure Monitor spolupracuje s webovou nebo služeb Team Foundation a samostatné aplikace na různých platformách jako .NET, Java, Node.js a mnoho dalších platforem hostovaný místně nebo v cloudu.

### <a name="additional-resources"></a>Další zdroje

- **Přehled služby Azure Monitor** \
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- **Co je Application Insights?** \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **Co je monitorování metrik Azure?** \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- **Řešení pro monitorování kontejnerů ve službě Azure Monitor** \
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a>Zabezpečení a zálohování služby

Existuje mnoho podporu vás ujmeme rutinních úkolů s velkým množstvím podrobnosti, které je potřeba zpracovat zajistit, že vaše aplikace a infrastrukturu jsou v podmínce nejvyšší stupeň pro podporu obchodních potřeb a situace však začíná komplikovat více ve sféře, mikroslužby, takže potřebujete způsob, jak Pokud potřebujete provést akci, mají vysoké úrovně a podrobné zobrazení.

Azure nabízí nástroje pro správu a poskytují jednotný přehled o čtyři důležité aspekty cloudových a místních prostředků:

- **Zabezpečení.** S [Azure Security Center](https://azure.microsoft.com/services/security-center/).
  - Získejte kompletní přehled a kontrolu nad zabezpečením všech vašich virtuálních počítačů, aplikací a úloh.
  - Centralizujte si správu zásad zabezpečení a integraci stávajících procesů a nástrojů.
  - Detekujte reálné hrozby pomocí pokročilých analýz.

- **Zálohování**. S [Azure Backup](https://azure.microsoft.com/services/backup/).
  - Vyhnout se nákladnému přerušení služeb, splnit cíle dodržování předpisů a chránit vaše data před ransomwarem a lidskou chybou.
  - Zachovejte si svá záložní data přenášená i v klidovém stavu zašifrovaná.
  - Zajištění přístupu na základě vícefaktorového ověřování, abyste zabránili neoprávněnému používání.

- **Místní prostředky**. S [skutečně konsistentní hybridní cloud](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).

>[!div class="step-by-step"]
>[Předchozí](manage-production-docker-environments.md)
>[další](../key-takeaways/index.md)
