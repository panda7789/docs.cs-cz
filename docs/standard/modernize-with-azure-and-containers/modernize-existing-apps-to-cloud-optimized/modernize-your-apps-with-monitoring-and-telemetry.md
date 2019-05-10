---
title: Modernizace aplikací pomocí monitorování a telemetrie
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a Windows kontejnery | Modernizace aplikací pomocí monitorování a telemetrie
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: a8135031d2879ff377881d246c532573a2149fe7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64611661"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a>Modernizace aplikací pomocí monitorování a telemetrie

Když spustíte aplikaci v produkčním prostředí, je velmi důležité, abyste měli přehled o výkonu vaší aplikace. Je provádění na vysoké úrovni? Se uživatelé chyby, nebo pokud je aplikace stabilní a spolehlivá? Potřebujete bohaté performance monitoring pro aplikace, výkonné upozorňování a řídicí panely, abyste zajistili, že aplikace je k dispozici a provádí podle očekávání. Musíte také mít možnost rychle zobrazit, pokud je nějaký problém, určit, kolik zákazníků se to týká a provádět analýzy původních příčin vyhledat a opravit tento problém.

## <a name="monitor-your-application-with-application-insights"></a>Můžete monitorovat své aplikace pomocí Application Insights

Application Insights je rozšiřitelná služba správu výkonu aplikací (APM) pro webové vývojáře, kteří pracují na různých platformách. Použijte ho k monitorování živé webové aplikace. Application Insights automaticky zjišťuje anomálie výkonu. Obsahuje výkonné analytické nástroje můžete diagnostikovat problémy a které vám pomohou pochopit, co uživatelé dělají s vaší aplikací. Application Insights je určena k pomáhala průběžně vylepšovat výkon a použitelnost. Funguje pro aplikace na nejrůznějších platformách, včetně .NET, Node.js a J2EE, ať už hostovaný místně nebo v cloudu. Application Insights integruje do svých procesů DevOps a má spojovací body s celou řadu nástrojů pro vývoj.

Obrázek 4 – 10 ukazuje příklad, jak Application Insights monitoruje vaše aplikace a jak zobrazí tyto přehledy na řídicí panel.

![Monitorování řídicího panelu služby Application Insights](./media/image10.png)

> **Obrázek 4 – 10.** Monitorování řídicího panelu služby Application Insights

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a>Monitorování infrastruktury Dockeru s Log Analytics a jeho řešení pro monitorování kontejnerů

[Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) je součástí [celkového monitorovacího řešení Microsoft Azure](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview). Je také služby [Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview). Log Analytics monitoruje Cloudová a místní prostředí (OMS pro místní), který pomáhá zajistit dostupnost a výkon. Shromažďuje data generovaná prostředky ve vašem cloudovém a místním prostředí a také data z dalších nástrojů pro monitorování a poskytuje analýzy napříč zdroji.

Ve vztahu k protokolů infrastruktury Azure Log Analytics jako služby Azure a ingestuje data protokolů a metrik z ostatních služeb Azure (prostřednictvím [Azure Monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), virtuální počítače Azure, kontejnery Docker a on-premises nebo jiných cloudových infrastruktur. Log Analytics nabízí flexibilní protokol vyhledávání a analýzy out-představené na tato data. Nabízí bohaté možnosti nástrojů, můžete použít k analýze dat napříč zdroji, umožňuje složitých dotazů ve všech protokolů a proaktivně může upozornit na základě zadaných podmínek. Můžete dokonce shromáždění vlastních dat do centrálního úložiště Log Analytics, kde se můžete dotazovat a vizualizovat. Také můžete využít výhod integrovaných řešení Log Analytics umožňuje získat okamžitý přehled o zabezpečení a funkce vaší infrastruktury.

Můžete používat Log Analytics na portálu OMS nebo webu Azure portal, který se spustit v jakémkoli prohlížeči, a poskytují přístup k nastavení konfigurace a několika nástrojům analyzovat a zpracovat shromážděná data.

[Řešení pro monitorování kontejnerů](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) v Log Analytics vám umožňuje zobrazit a spravovat hostitele Dockeru a kontejnerech Windows na jednom místě. Toto řešení ukazuje, které kontejnery jsou spuštěná, jaké image kontejnerů běží a kde kontejnery běží. Můžete zobrazit podrobné informace auditu, včetně příkazů, které se používají s kontejnery. Kontejnery také můžete řešit pomocí zobrazení a hledání centralizované protokoly, aniž byste museli vzdáleně zobrazení hostitele Docker nebo Windows. Můžete najít kontejnery, které mohou být na hostiteli hlučného a využívání nadbytečné prostředky. Kromě toho můžete zobrazit centralizované procesoru, paměti, úložiště a využití sítě a informace o výkonu pro kontejnery. V počítačích se systémem Windows, můžete centralizovat a porovnat protokoly ze systému Windows Server Hyper-V a kontejnery Dockeru. Řešení podporuje následující orchestrátorů kontejnerů:

- Docker Swarm

- DC/OS

- Kubernetes

- Service Fabric

- Red Hat OpenShift

Obrázek 4 – 11 znázorňuje vztahy mezi různými hostitelích kontejnerů a agentů a OMS.

![Řešení log Analytics monitorování kontejnerů](./media/image11.png)

> **Obrázek 4 – 11.** Řešení log Analytics monitorování kontejnerů

Řešení monitorování kontejnerů Log Analytics můžete použít:

- Zobrazit informace o všech hostitelích kontejnerů na jednom místě.

- Zjistit, které kontejnery jsou spuštěná, jaké image spuštěnými, a pokud máte spuštěnou.

- Najdete v protokolu auditu pro akce v kontejnerech.

- Řešení potíží zobrazením a hledání centralizované protokoly bez vzdálené přihlášení na hostitele Dockeru.

- Najdete kontejnerů, které mohou být "" hlučným sousedům"" a by spotřebovávalo nadbytečné prostředků na hostiteli.

- Zobrazte centralizované procesoru, paměti, úložiště a využití sítě a informace o výkonu pro kontejnery.

### <a name="additional-resources"></a>Další zdroje

- **Přehled monitorování v Microsoft Azure**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **Co je Application Insights?**

<https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **Co je služba Log Analytics?**

<https://docs.microsoft.com/azure/log-analytics/log-analytics-overview>

- **Řešení pro monitorování kontejnerů ve službě Azure Monitor**

<https://docs.microsoft.com/azure/azure-monitor/insights/containers>

- **Přehled služby Azure Monitor**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **Co je Operations Management Suite (OMS)?**

<https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview>

- **Monitorování kontejnerů Windows serveru v Service Fabric pomocí OMS**

<https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver>

>[!div class="step-by-step"]
>[Předchozí](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
>[další](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
