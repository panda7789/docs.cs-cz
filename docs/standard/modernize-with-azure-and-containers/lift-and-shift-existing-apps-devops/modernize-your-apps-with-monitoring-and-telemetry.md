---
title: "Modernizovat aplikace s monitorování a telemetrie"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Modernizovat aplikace s monitorování a telemetrie"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3caeb60cf0107aaf5413d935f3bde11863561c7d
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2018
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a>Modernizovat aplikace s monitorování a telemetrie

Když spustíte aplikaci v produkčním prostředí, je důležité, abyste měli přehled o tom, jak je provádění vaší aplikace. Je její výkon na vysoké úrovni? Jsou uživatelé dochází k chybám, nebo je aplikace stabilní a spolehlivá? Budete potřebovat bohaté performance monitoring pro aplikace, výkonné výstrahy a řídicí panely, abyste zajistili, že aplikace je k dispozici a provádění podle očekávání. Potřebujete mít možnost rychle zjistit, zda je problém, určit, kolik zákazníkům ovlivněných a provést analýzu hlavní příčiny najít a opravit potíže.

## <a name="monitor-your-application-with-application-insights"></a>Monitorování vaší aplikace pomocí Application Insights

Application Insights je rozšiřitelnou službu Správa výkonu aplikace (APM) pro vývojářům webů, kteří pracují ve více platformách. Použijte jej k monitorování provozu webové aplikace. Application Insights automaticky rozpozná anomálie výkonu. Obsahuje nástroje výkonné analytics při diagnostice problémů a které vám pomohou pochopit, co uživatelé ve skutečnosti dělat s vaší aplikací. Application Insights je navržená tak, abyste neustále průběžně zlepšují výkon a použitelnost. Funguje pro aplikace v celé řadě platforem, včetně .NET, Node.js a J2EE, ať hostovaný místně nebo v cloudu. Application Insights se integruje s procesy vaší DevOps a má spojovací body na celou řadu nástrojů pro vývoj.

Obrázek 4 – 10 ukazuje příklad jak Application Insights monitoruje vaše aplikace a jak ho na řídicí panel poskytuje tyto přehledy.

![Application Insights řídicí panel monitorování.](./media/image10.png)

> **Obrázek 4-10.** Application Insights řídicí panel monitorování.

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a>Monitorování infrastruktury Docker s analýzy protokolů a jeho řešení monitorování kontejneru

[Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) je součástí [Microsoft Azure celkového řešení monitorování](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview). Je také služba v [Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview). Analýzy protokolů monitoruje cloudové a místní prostředí (OMS pro místní) Chcete-li usnadnit zachování dostupnosti a výkonu. Shromáždí data generována prostředky ve vašich cloudových a místních prostředích a z dalších nástrojů pro monitorování poskytnout analýzu napříč více zdrojů.

Ve vztahu k protokoly infrastrukturu Azure Log Analytics jako služby Azure ingestuje protokolu a metriku, data z jiných služeb systému Azure (prostřednictvím [Azure monitorování](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), virtuální počítače Azure, Docker kontejnery a místní nebo jiných cloudových infrastruktur. Analýzy protokolů nabízí flexibilní protokol hledání a analýzy na více systémů v poli nad tato data. Nabízí bohaté nástroje, můžete použít k analýze dat napříč zdroje, umožňuje komplexní dotazy mezi všechny protokoly a proaktivně můžete výstrahy na základě zadaných podmínek. Můžete dokonce shromáždění vlastních dat v centrálním úložišti analýzy protokolů, kde se můžete dotazovat a vizualizovat ho. Také můžete využít výhod integrované řešení analýzy protokolů a okamžitě získáte přehled o zabezpečení a funkce vaší infrastruktury.

Můžete přistupovat prostřednictvím portálu OMS nebo portálu Azure, který spustit v libovolném prohlížeči, analýzy protokolů a poskytnout vám přístup k nastavení konfigurace a několik nástrojů k analýze a fungovat na shromážděná data.

[Řešením pro monitorování kontejneru](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) v analýzy protokolů pomáhá zobrazení a správa hostitelů Docker a kontejneru systému Windows na jednom místě. Řešení ukazuje jsou kontejnery, které běží, jaké kontejneru image se používáte, a kde kontejnery běží. Můžete zobrazit podrobné informace auditu, včetně příkazů, které se používají s kontejnery. Kontejnery také můžete řešit pomocí zobrazení a hledání centralizované protokoly, bez nutnosti Chcete-li zobrazit hostitelů Docker nebo Windows. Můžete najít kontejnery, které může být aktivní nebo využívání nadbytečné prostředky na hostiteli. Kromě toho můžete zobrazit centralizované procesoru, paměti, úložiště a síťového využití a informace o výkonu pro kontejnery. V počítačích se systémem Windows, můžete centralizovat a porovnání protokoly ze systému Windows Server, technologie Hyper-V a Docker kontejnerů. Řešení podporuje následující orchestrators kontejneru:

-   Docker Swarm

-   DC/OS

-   Kubernetes

-   Service Fabric

-   Red Hat OpenShift

Obrázek 4 – 11 znázorňuje vztahy mezi různými hostiteli kontejneru a agentů a OMS.

![Řešení monitorování kontejneru analýzy protokolů](./media/image11.png)

> **Obrázek 4-11.** Řešení monitorování kontejneru analýzy protokolů

Můžete použít řešení monitorování protokolu analýzy kontejneru:

-   Zobrazit informace o všech hostitelů kontejneru na jednom místě.

-   Vědět, se kterou kontejnery běží, jaké bitové kopie se používáte, a pokud používáte systém.

-   O kontejnery naleznete v protokolu auditu pro akce.

-   Vyřešte potíže se zobrazením a hledání centralizované protokoly bez vzdálené přihlášení k hostitelů Docker.

-   Najít kontejnery, které může být "aktivní okolí" a pracovat s prostředky nadbytečné na hostiteli.

-   Zobrazte centralizované procesoru, paměti, úložiště a síťového využití a informace o výkonu pro kontejnery.

### <a name="additional-resources"></a>Další zdroje

-   **Přehled monitorování v Microsoft Azure**

[https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview)

-   **Co je Application Insights?**

[https://docs.microsoft.com/azure/application-insights/app-insights-overview](https://docs.microsoft.com/azure/application-insights/app-insights-overview)

-   **Co je Log Analytics?**

[https://docs.microsoft.com/azure/log-analytics/log-analytics-overview](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview)

-   **Řešení monitorování kontejneru v analýzy protokolů**

[https://docs.microsoft.com/azure/log-analytics/log-analytics-containers](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers)

-   **Přehled Azure monitorování**

[https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)

-   **Co je Operations Management Suite (OMS)?**

[https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview)

-   **Monitorování systému Windows Server kontejnery v Service Fabric s OMS**

[https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver](https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver)

>[!div class="step-by-step"]
[Předchozí](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
[další](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
