---
title: Monitorování kontejnerizovaných aplikačních služeb
description: Životní cyklus aplikace kontejnerizovaných Dockeru s platformou a nástroji Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 4bdc4470624ce6e905ab858a2bd8b607c8d3d646
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46698529"
---
# <a name="monitor-containerized-application-services"></a>Monitorování kontejnerizovaných aplikačních služeb

Je velmi důležité pro aplikace rozdělit do několika kontejnery a mikroslužby způsob, jak monitorovat a analyzovat chování aplikace.

## <a name="microsoft-application-insights"></a>Microsoft Application Insights

[Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview) je rozšiřitelnou analytickou službu, která monitoruje vaše živé aplikace. Pomáhá detekovat a diagnostikovat problémy s výkonem a pochopit, co uživatelé dělají s vaší aplikací. Je určená pro vývojáře se záměrem pomáhá průběžně zlepšit výkon a použitelnost služby nebo aplikace. Application Insights pracuje s webovou nebo služeb Team Foundation a samostatné aplikace na různých platformách jako .NET, Java, Node.js a mnoho dalších platforem hostovaný místně nebo v cloudu.

### <a name="analyzing-docker-apps-in-qa-environments-using-application-insights"></a>Analýza aplikací Dockeru v prostředí QA pomocí Application Insights

Protože se týkají Dockeru, můžete graf události životního cyklu a čítače výkonu z kontejnerů Dockeru v Application Insights. Stačí spustit [image Dockeru Application Insights](https://hub.docker.com/r/microsoft/applicationinsights/) jako kontejner v hostiteli který se zobrazí čítače výkonu pro hostitele stejně jako u jiných Image Dockeru. Tato image Dockeru Application Insights (obrázek 6 - 1) vám umožní monitorovat své kontejnerizované aplikace pomocí shromažďování telemetrických dat o výkonu a aktivitu (to znamená, že vaše virtuální počítače s Linuxem) hostitele Docker, kontejnery Docker a aplikace běžící v nich.

![příklad](./media/image1.png)

Obrázek 6-1: Application Insights, monitorování hostitelů Docker a kontejnery

Při spuštění [image Dockeru Application Insights](https://hub.docker.com/r/microsoft/applicationinsights/) na hostiteli Dockeru, můžete využívat následující:

-   Životní cyklus telemetrická data o všechny kontejnery běží na hostiteli, spuštění, zastavení a tak dále.

-   Čítače výkonu pro všechny kontejnery: procesoru, paměti, využití sítě a další.

-   Pokud jste nainstalovali také [Application Insights SDK](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net) v aplikace spuštěné v kontejnerech, bude mít veškerá telemetrická data těchto aplikací další vlastnosti identifikující kontejner a hostitele počítače. Ano například pokud máte instancí aplikace běžící ve více než jednoho hostitele, snadno budete mít k filtrování telemetrie vaší aplikace hostitel.

### <a name="setting-up-application-insights-to-monitor-docker-applications-and-docker-hosts"></a>Nastavení Application Insights pro monitorování aplikací Dockeru a hostitelů Docker

Vytvořte prostředek Application Insights, postupujte podle pokynů v článcích, které jsou uvedeny v následujícím seznamu. Azure Portal vytvoří nezbytné skript za vás.

-   **Monitorování aplikací Dockeru ve službě Application Insights:**  [https://docs.microsoft.com/azure/application-insights/app-insights-docker](https://docs.microsoft.com/azure/application-insights/app-insights-docker)

-   **Aplikace Insights Docker image v Docker Hubu a Githubu:**  
[https://hub.docker.com/r/microsoft/applicationinsights/](https://hub.docker.com/r/microsoft/applicationinsights/) a <https://github.com/Microsoft/ApplicationInsights-Docker>

-   **Nastavení Application Insights pro ASP.NET:**  
[https://docs.microsoft.com/azure/application-insights/app-insights-asp-net](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net)

-   **Application Insights pro webové stránky:**  
<https://docs.microsoft.com/azure/application-insights/app-insights-javascript>

## <a name="microsoft-operations-management-suite"></a>Microsoft Operations Management Suite

[Operations Management Suite](https://microsoft.com/oms) je zjednodušené řešení správy IT, které nabízí log analytics, automation, backup a site recovery. Na základě [dotazy](https://blogs.technet.microsoft.com/msoms/2016/01/21/easy-microsoft-operations-management-suite-search-queries/) v Operations Management Suite, můžete zvýšit [výstrahy](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-monitoring-alerts) a nápravu prostřednictvím [Azure Automation](https://docs.microsoft.com/azure/automation/). I hladce integrují s vaší stávající řešení pro správu pro poskytovat jednotné zobrazení podokně ze skla. Operations Management Suite vám umožní spravovat a chránit svoje místní a cloudovou infrastrukturu.

### <a name="operations-management-suitehttpsmicrosoftcomoms-container-solution-for-docker"></a>[Operations Management Suite](https://microsoft.com/oms) řešení kontejnerů pro Docker

Kromě poskytování přínosných služeb sama o sobě, kontejner řešení Operations Management Suite můžete sledovat a spravovat hostitele Dockeru a kontejnerech tím, že zobrazuje informace o tom, kde jsou kontejnery a hostitelích kontejnerů, které jsou spuštěné kontejnery nebo ve stavu selhání a protokoly démonu a kontejneru Dockeru odesílat *stdout* a *stderr*. Také ukazuje metriky výkonu, jako je například procesoru, paměti, sítě a úložiště pro kontejner a hostitele při řešení potíží a najít hlučného souseda kontejnery.

![](./media/image2.png)

Obrázek 6 – 2: informace o kontejnerech Dockeru zobrazené Operations Management Suite

Application Insights a Operations Management Suite zaměřit na monitorování aktivit; ale Application Insights se zaměřuje více o sledování aplikací sami díky jeho SDK v rámci aplikace. Ale Operations Management Suite se mnohem více zaměřuje na infrastruktuře kolem hostitele, a navíc nabízí hloubkovou analýzu protokolů ve velkém měřítku současně poskytují velmi flexibilní řízené daty hledání nebo dotaz systému.

Protože Operations Management Suite je implementovaná jako cloudová služba, můžete mít ji zprovoznit rychle s minimálními investicemi do infrastrukturních služeb. Nové funkce jsou doručovány pravidelně, ušetříte z průběžnou údržbu a upgrade náklady.

Pomocí řešení Operations Management Suite kontejnerů, můžete provést následující:

-   Centralizovat a korelovat miliony protokoly z kontejnerů Dockeru ve velkém měřítku

-   Zobrazit informace o všech hostitelích kontejnerů na jednom místě

-   Zjistit, které kontejnery jsou spuštěná, jaké image spuštěnými a ve kterém běží

-   Rychle Diagnostikujte "hlučného souseda" kontejnery, které mohou způsobovat problémy na hostitelích kontejnerů

-   V kontejnerech najdete v protokolu auditu pro akce

-   Řešení potíží zobrazením a hledání centralizované protokoly bez vzdálené komunikace na hostitele Docker

-   Najít kontejnery, které mohou být "" hlučným sousedům"" a využívání nadbytečné prostředků na hostiteli

-   Zobrazit centralizované procesoru, paměti, úložiště a využití a výkonu informace o síti pro kontejnery

-   Generování testu kontejnerů Dockeru pomocí Azure Automation

Zobrazí se informace o výkonu spouštěním dotazů, jako je typ = Perf, jak je znázorněno v obrázek 6 – 3.

![DockerPerfMetricsView](./media/image3.png){width = "5.78625 v" height = "3,25 v"}

Obrázek 6 – 3: metriky výkonu hostitele Docker zobrazené Operations Management Suite

Ukládání dotazů je také standardní funkce v Operations Management Suite a jak vám pomůže uchovávat dotazy připadají užitečné a zjišťovat tak trendy ve vašem systému.

**Další informace o** najdete informace o instalaci a konfiguraci Dockeru řešení kontejnerů v [Operations Management Suite](https://microsoft.com/oms), přejděte na stránku <https://docs.microsoft.com/azure/log-analytics/log-analytics-containers>.

>[!div class="step-by-step"]
[Předchozí](manage-production-docker-environments.md)
[další](../key-takeaways/index.md)
