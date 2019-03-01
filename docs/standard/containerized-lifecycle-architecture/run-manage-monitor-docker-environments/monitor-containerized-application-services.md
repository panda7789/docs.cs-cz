---
title: Monitorování kontejnerizovaných aplikačních služeb
description: Přečtěte si některé klíčové aspekty monitorování kontejneru architektury
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 925db543617deb28590cf6631ebbda3ee96836c4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975742"
---
# <a name="monitor-containerized-application-services"></a>Monitorování kontejnerizovaných aplikačních služeb

Je velmi důležité pro aplikace rozdělit do několika kontejnery a mikroslužby způsob, jak monitorovat a analyzovat chování celou aplikaci.

## <a name="microsoft-application-insights"></a>Microsoft Application Insights

[Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview) je rozšiřitelnou analytickou službu, která monitoruje vaše živé aplikace. Pomáhá detekovat a diagnostikovat problémy s výkonem a pochopit, co uživatelé dělají s vaší aplikací. Je určená pro vývojáře se záměrem pomáhá průběžně zlepšit výkon a použitelnost služby nebo aplikace. Application Insights pracuje s webovou nebo služeb Team Foundation a samostatné aplikace na různých platformách jako .NET, Java, Node.js a mnoho dalších platforem hostovaný místně nebo v cloudu.

### <a name="analyzing-docker-apps-in-qa-environments-using-application-insights"></a>Analýza aplikací Dockeru v prostředí QA pomocí Application Insights

Protože se týkají Dockeru, můžete graf události životního cyklu a čítače výkonu z kontejnerů Dockeru v Application Insights. Stačí spustit [image Dockeru Application Insights](https://hub.docker.com/r/microsoft/applicationinsights/) jako kontejner v hostiteli který se zobrazí čítače výkonu pro hostitele stejně jako u jiných Image Dockeru. Tato image Dockeru Application Insights (obrázek 6 - 1) vám umožní monitorovat své kontejnerizované aplikace pomocí shromažďování telemetrických dat o výkonu a aktivitu (to znamená, že vaše virtuální počítače s Linuxem) hostitele Docker, kontejnery Docker a aplikace běžící v nich.

![příklad](./media/image1.png)

**Obrázek 6-1**. Application Insights, monitorování hostitelů Docker a kontejnery

Při spuštění [image Dockeru Application Insights](https://hub.docker.com/r/microsoft/applicationinsights/) na hostiteli Dockeru, můžete využívat následující:

- Životní cyklus telemetrická data o všechny kontejnery běží na hostiteli, spuštění, zastavení a tak dále.

- Čítače výkonu pro všechny kontejnery: Procesoru, paměti, využití sítě a další.

- Pokud jste nainstalovali také [Application Insights SDK](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net) v aplikace spuštěné v kontejnerech, bude mít veškerá telemetrická data těchto aplikací další vlastnosti identifikující kontejner a hostitele počítače. Ano například pokud máte instancí aplikace běžící ve více než jednoho hostitele, snadno budete mít k filtrování telemetrie vaší aplikace hostitel.

### <a name="setting-up-application-insights-to-monitor-docker-applications-and-docker-hosts"></a>Nastavení Application Insights pro monitorování aplikací Dockeru a hostitelů Docker

Vytvořte prostředek Application Insights, postupujte podle pokynů v článcích, které jsou uvedeny v následujícím seznamu. Azure portal vytvoří nezbytné skript za vás.

- **Monitorování aplikací Dockeru ve službě Application Insights:** \
  <https://docs.microsoft.com/azure/application-insights/app-insights-docker>

- **Aplikace Insights Docker image v Docker Hubu a Githubu:** \
  <https://hub.docker.com/r/microsoft/applicationinsights/> a \
  <https://github.com/Microsoft/ApplicationInsights-Docker>

- **Nastavení Application Insights pro webové aplikace ASP.NET a ASP.NET Core:** \
  <https://docs.microsoft.com/azure/application-insights/app-insights-asp-net>

- **Application Insights pro webové stránky:**  
  <https://docs.microsoft.com/azure/application-insights/app-insights-javascript>

## <a name="security-backup-and-monitoring-services"></a>Zabezpečení, zálohování a monitorování služeb

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

- **Monitorování**. S [monitorování Azure](https://azure.microsoft.com/solutions/monitoring/), [Log Analytics](https://azure.microsoft.com/services/log-analytics/), a [Application Insights](https://azure.microsoft.com/services/application-insights/).
  - Umožňuje získáte úplný přehled o stavu a výkonu vašich úloh v Azure, aplikací a infrastruktury.
  - Shromažďování dat z libovolného zdroje a získat detailní přehled o vašich virtuálních počítačů, kontejnery a aplikace.
  - Najdete informace, které potřebujete, pomocí interaktivních dotazů a fulltextového vyhledávání. 
  - Proveďte analýzu hlavní příčiny pomocí pokročilých analýz, včetně algoritmů strojového učení.

- **Místní prostředky**. S [skutečně konsistentní hybridní cloud](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).

>[!div class="step-by-step"]
>[Předchozí](manage-production-docker-environments.md)
>[další](../key-takeaways/index.md)
