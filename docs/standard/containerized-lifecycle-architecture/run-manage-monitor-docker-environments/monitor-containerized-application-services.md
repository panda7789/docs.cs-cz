---
title: Monitorování kontejnerizované aplikačních služeb
description: Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b3ffa6c230176e1de6269ed0b30d05711ff78704
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="monitor-containerized-application-services"></a>Monitorování kontejnerizované aplikačních služeb

Je důležité pro aplikace, rozdělte do více kontejnerů a mikroslužeb tak, aby měl způsob, jak monitorovat a analyzovat chování aplikace.

## <a name="microsoft-application-insights"></a>Microsoft Application Insights

[Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview) je rozšiřitelnou analytickou službu, která monitoruje vaše živé aplikace. Umožňuje najít a diagnostikovat problémy s výkonem a pochopit, co uživatelé ve skutečnosti dělat s vaší aplikací. Je určený pro vývojáře, s cílem vám pomáhá s neustále průběžně zlepšují výkon a použitelnost ze služeb nebo aplikací. Application Insights funguje s webové nebo služby a samostatné aplikace na řadě různých platforem, jako jsou .NET, Java, Node.js a mnoho dalších platformy hostovaný místně nebo v cloudu.

### <a name="analyzing-docker-apps-in-qa-environments-using-application-insights"></a>Analýza aplikace Docker v prostředí QA pomocí Application Insights

Jak se vztahuje k Docker, můžete grafu události životního cyklu a čítače výkonu z kontejnerů Docker v Application Insights. Stačí ke spuštění [Application Insights Docker image](https://hub.docker.com/r/microsoft/applicationinsights/) jako kontejner v hostiteli a zobrazí čítače výkonu pro hostitele a jako u jiných Docker obrázků. Tuto bitovou kopii Application Insights Docker (obrázek 6 - 1) pomáhá monitorovat aplikace kontejnerizované shromažďováním telemetrická data o výkonu a aktivity váš hostitel Docker (to znamená, že vaše virtuální počítače s Linuxem), Docker kontejnery a aplikace běžící v nich.

![příklad](./media/image1.png)

Obrázek 6-1: Application Insights monitorování hostitelů Docker a kontejnery

Při spuštění [Application Insights Docker image](https://hub.docker.com/r/microsoft/applicationinsights/) na hostiteli Docker, můžete využívat následující:

-   Životní cyklus telemetrii týkající se všechny kontejnery spuštěných na hostiteli – spuštění, zastavení a tak dále.

-   Čítače výkonu pro všechny kontejnery: procesoru, paměti, využití sítě a další.

-   Pokud jste nainstalovali také [Application Insights SDK](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net) ve aplikace běžící v kontejnerech, budou všechny telemetrická těchto aplikací mít další vlastnosti identifikace počítače kontejneru a hostitele. Ano například pokud máte instance aplikace spuštěná v hostiteli více než jeden, snadno budete moct filtrovat telemetrie aplikace hostitele.

### <a name="setting-up-application-insights-to-monitor-docker-applications-and-docker-hosts"></a>Nastavení Application Insights pro sledování aplikace Docker a hostitelů Docker

Vytvořte prostředek Application Insights, postupujte podle pokynů v článcích uvedené v následujícím seznamu. Portál Azure pro vytvoření nezbytné skriptu.

-   **Monitorování Docker aplikací ve službě Application Insights:**  [https://docs.microsoft.com/azure/application-insights/app-insights-docker](https://docs.microsoft.com/azure/application-insights/app-insights-docker)

-   **Aplikace bitovou kopii Insights Docker v Docker Hub a Githubu:**  
[https://hub.docker.com/r/microsoft/applicationinsights/](https://hub.docker.com/r/microsoft/applicationinsights/) A <https://github.com/Microsoft/ApplicationInsights-Docker>

-   **Nastavte Application Insights pro ASP.NET:**  
[https://docs.microsoft.com/azure/application-insights/app-insights-asp-net](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net)

-   **Application Insights pro webové stránky:**  
<https://docs.microsoft.com/azure/application-insights/app-insights-javascript>

## <a name="microsoft-operations-management-suite"></a>Microsoft Operations Management Suite

[Služby Operations Management Suite](http://microsoft.com/oms) je zjednodušená řešení správy IT, které poskytuje analýzy protokolů, automatizace, zálohování a obnovení lokality. Na základě [dotazy](https://blogs.technet.microsoft.com/msoms/2016/01/21/easy-microsoft-operations-management-suite-search-queries/) v Operations Management Suite, můžete zvýšit [výstrahy](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-monitoring-alerts) a nastavte nápravy prostřednictvím [Azure Automation](https://docs.microsoft.com/azure/automation/). Také bezproblémově integruje s vaší stávající řešení pro správu k poskytování jednoho podokně přehledné zobrazení. Služby Operations Management Suite umožňuje spravovat a chránit místní a cloudové infrastruktury.

### <a name="operations-management-suitehttpmicrosoftcomoms-container-solution-for-docker"></a>[Služby Operations Management Suite](http://microsoft.com/oms) kontejneru řešení pro Docker

Kromě poskytování služeb cenné svoje vlastní řešení kontejneru Operations Management Suite můžete spravovat a monitorovat hostitelů Docker a kontejnerů, tím, že zobrazuje informace o tom, kde jsou kontejnerů a kontejner hostitelů, která jsou spuštěna kontejnery nebo ve stavu selhání a protokoly démon a kontejner Docker posílá *stdout* a *stderr*. Také ukazuje metriky výkonu, jako je například procesoru, paměti, sítě a úložiště pro kontejner a hostitelů, které vám pomohou vyřešit a najít aktivní sousedním kontejnery.

![](./media/image2.png)

Obrázek 6-2: informace o Docker kontejnery zobrazí Operations Management Suite

Application Insights a Operations Management Suite soustředit na monitorování aktivit; však Application Insights se týká víc monitorování aplikací, sami díky její SDK spuštěné v aplikaci. Ale Operations Management Suite se víc zaměřuje na infrastrukturu kolem hostitelů plus nabízí hloubkovou analýzu na protokoly ve velkém měřítku při současném poskytování systému velmi flexibilní datové hledání nebo dotazu.

Protože Operations Management Suite je implementovaný jako cloudová služba, můžete jej budete mít spuštěný a funkční rychle s minimálním investice do infrastruktury služby. Nové funkce jsou automaticky doručit vyhnout se tak průběžnou údržbu a upgradovat náklady.

Pomocí řešení Operations Management Suite kontejneru, můžete provést následující:

-   Centralizovat a korelovat miliony protokoly z kontejnerů Docker ve velkém měřítku

-   Zobrazit informace o všech hostitelů kontejneru na jednom místě

-   Vědět, se kterou kontejnery běží, jaké bitové kopie budou používáte, a kde se systémem

-   Rychle diagnostikuje "aktivní sousedním" kontejnery, které může způsobit problémy na hostitelích kontejneru

-   Zobrazit protokol auditu pro akce na kontejnery

-   Řešení potíží zobrazením a hledání centralizované protokoly bez Vzdálená komunikace na hostitelů Docker

-   Najít kontejnery, které může být "aktivní okolí" a využívání nadbytečné prostředky na hostiteli

-   Zobrazit centralizované procesoru, paměti, úložiště a využití a výkonu informace o síti pro kontejnery

-   Generování testů Docker kontejnery s Azure Automation.

Zobrazí informace o výkonu spuštěním dotazy jako typ = výkonu, jak je znázorněno v obrázek 6-3.

![DockerPerfMetricsView](./media/image3.png){width = "5.78625 in" height = "3,25 in"}

Obrázek 6-3: metriky výkonu hostitelů Docker zobrazí Operations Management Suite

Uložení dotazů je také standardní funkce služby Operations Management Suite a mohou vám pomoci zachovat dotazů našli jste užitečné a zjistit trendy ve vašem systému.

**Další informace o** najít informace o instalaci a konfiguraci Docker kontejneru řešení v [Operations Management Suite](http://microsoft.com/oms), přejděte na <https://docs.microsoft.com/azure/log-analytics/log-analytics-containers>.

>[!div class="step-by-step"]
[Předchozí] (spravovat produkční docker-environments.md) [Další] (.. /Key-takeaways/index.MD)
