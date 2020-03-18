---
title: Modernizace aplikací pomocí monitorování a telemetrie
description: Modernizace stávajících aplikací .NET pomocí Azure Cloudu a kontejnerů Windows | Modernizujte své aplikace pomocí monitorování a telemetrie
ms.date: 04/30/2018
ms.openlocfilehash: 3d629e89a73c870d4b6396c6b1d0ecbe95b79ead
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393852"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a>Modernizace aplikací pomocí monitorování a telemetrie

Při spuštění aplikace v produkčním prostředí je důležité, abyste měli přehledo tom, jak si vaše aplikace vede. Vystupuje na vysoké úrovni? Jsou uživatelé stále chyby, nebo je aplikace stabilní a spolehlivé? Potřebujete bohaté monitorování výkonu, výkonné výstrahy a řídicí panely, které vám pomohou zajistit, aby vaše aplikace byla dostupná a fungovala podle očekávání. Musíte také rychle zjistit, zda došlo k potížím, určit, kolik zákazníků je ovlivněno, a provést analýzu hlavní příčiny, abyste problém našli a opravili.

## <a name="monitor-your-application-with-application-insights"></a>Sledování aplikace pomocí application insights

Application Insights je rozšiřitelná služba Správy výkonu aplikací (APM) pro webové vývojáře, kteří pracují na více platformách. Slouží k monitorování živé webové aplikace. Application Insights automaticky detekuje anomálie výkonu. Obsahuje výkonné analytické nástroje, které vám pomohou diagnostikovat problémy a pochopit, co uživatelé s vaší aplikací skutečně dělají. Application Insights je navržen tak, aby vám pomohl neustále zlepšovat výkon a použitelnost. Funguje pro aplikace na široké škále platforem, včetně .NET, Node.js a J2EE, ať už hostované místně nebo v cloudu. Application Insights se integruje s vašimi procesy DevOps a má spojovací body k různým vývojovým nástrojům.

Obrázek 4-10 ukazuje příklad toho, jak Application Insights monitoruje vaši aplikaci a jak tyto přehledy zobrazuje na řídicím panelu.

![Snímek obrazovky řídicího panelu monitorování Application Insights](./media/modernize-your-apps-with-monitoring-and-telemetry/application-insights-monitoring-dashboard.png)

**Obrázek 4-10.** Řídicí panel monitorování Přehledy aplikací

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a>Monitorování infrastruktury Dockeru pomocí Log Analytics a jejího řešení monitorování kontejnerů

[Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) je součástí [celkového monitorování řešení Microsoft Azure](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview). Je to také služba v [Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview). Log Analytics monitoruje cloudová a místní prostředí (OMS pro místní) a pomáhá udržovat dostupnost a výkon. Shromažďuje data generovaná prostředky ve vašem cloudovém a místním prostředí a také data z dalších nástrojů pro monitorování a poskytuje analýzy napříč zdroji.

Ve vztahu k protokolům infrastruktury Azure, Log Analytics, jako služba Azure, ingestuje data protokolu a metriky z jiných služeb Azure (přes [Azure Monitor),](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)virtuální počítače Azure, kontejnery Dockeru a místní nebo jiné cloudové infrastruktury. Log Analytics nabízí flexibilní vyhledávání protokolů a analýzy po vybalení z krabice nad tato data. Poskytuje bohaté nástroje, které můžete použít k analýze dat napříč zdroji, umožňuje složité dotazy ve všech protokolech a může proaktivně výstrahovat na základě zadaných podmínek. Můžete dokonce shromažďovat vlastní data v centrálním úložišti Log Analytics, kde je můžete dotazovat a vizualizovat. Můžete také využít integrované řešení Log Analytics a okamžitě získat přehled o zabezpečení a funkcích vaší infrastruktury.

K Log Analytics můžete přistupovat prostřednictvím portálu OMS nebo portálu Azure, které běží v libovolném prohlížeči a poskytují vám přístup k nastavení konfigurace a více nástrojů pro analýzu a činnost na shromážděná data.

[Řešení monitorování kontejnerů](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) v Log Analytics vám pomůže zobrazit a spravovat hostitele Dockeru a Windows Container na jednom místě. Řešení ukazuje, které kontejnery jsou spuštěny, jaké image kontejneru jsou spuštěny a kde kontejnery jsou spuštěny. Můžete zobrazit podrobné informace o auditu, včetně příkazů, které jsou používány s kontejnery. Kontejnery můžete také řešit zobrazením a prohledáváním centralizovaných protokolů, aniž byste museli vzdáleně zobrazovat hostitele Dockeru nebo Windows. Můžete najít kontejnery, které mohou být hlučné a spotřebovávají přebytečné prostředky na hostiteli. Kromě toho můžete zobrazit centralizované procesoru, paměti, úložiště a využití sítě a informace o výkonu pro kontejnery. V počítačích se systémem Windows můžete centralizovat a porovnávat protokoly z kontejnerů Windows Server, Hyper-V a Docker. Řešení podporuje následující kontejnerové orchestrátory:

- Docker Swarm

- DC/OS

- Kubernetes

- Red Hat OpenShift

Obrázek 4-11 znázorňuje vztahy mezi různými hostiteli kontejneru a agenty a OMS.

![Snímek obrazovky s řešením monitorování kontejnerů analýzy protokolů](./media/modernize-your-apps-with-monitoring-and-telemetry/log-analytics-container-monitoring-solution.png)

**Obrázek 4-11.** Řešení monitorování kontejnerů analýzy protokolů

Pomocí řešení monitorování kontejnerů analýzy protokolů můžete:

- Zobrazení informací o všech hostitelích kontejnerů na jednom místě.

- Zjistěte, které kontejnery běží, jakou image používají a kde běží.

- Podívejte se na záznam auditu pro akce na kontejnery.

- Poradce při potížích zobrazením a prohledáváním centralizovaných protokolů bez vzdáleného přihlášení k hostitelům Dockeru.

- Najít kontejnery, které mohou být "hlučné sousedy" a spotřebovávají přebytečné prostředky na hostiteli.

- Zobrazení centralizovaného procesoru, paměti, úložiště a využití sítě a informací o výkonu pro kontejnery.

### <a name="additional-resources"></a>Další zdroje

- **Přehled monitorování v Microsoft Azure**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **Co je Application Insights?**

<https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **Co je služba Log Analytics?**

<https://docs.microsoft.com/azure/log-analytics/log-analytics-overview>

- **Řešení monitorování kontejnerů ve službě Azure Monitor**

<https://docs.microsoft.com/azure/azure-monitor/insights/containers>

- **Přehled služby Azure Monitor**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **Co je Operations Management Suite (OMS)?**

<https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview>

>[!div class="step-by-step"]
>[Předchozí](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
>[další](life-cycle-ci-cd-pipelines-devops-tools.md)
