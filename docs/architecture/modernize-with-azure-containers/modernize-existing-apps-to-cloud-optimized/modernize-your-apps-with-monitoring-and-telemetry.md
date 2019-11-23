---
title: Modernizace aplikací pomocí monitorování a telemetrie
description: Modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows | Modernizovat své aplikace s využitím monitorování a telemetrie
ms.date: 04/30/2018
ms.openlocfilehash: 3d629e89a73c870d4b6396c6b1d0ecbe95b79ead
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/08/2019
ms.locfileid: "72393852"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a>Modernizace aplikací pomocí monitorování a telemetrie

Když spustíte aplikaci v produkčním prostředí, je důležité, abyste měli přehled o tom, jak vaše aplikace funguje. Provádí se na vysoké úrovni? Získávají uživatelé chyby nebo je aplikace stabilní a spolehlivá? Abyste měli jistotu, že vaše aplikace bude dostupná a funguje podle očekávání, budete potřebovat kvalitní monitorování výkonu, výkonné upozorňování a řídicí panely. Pokud dojde k potížím, je potřeba, abyste mohli rychle zjistit, kolik zákazníků to ovlivnilo, a provést analýzu původní příčiny, která tento problém najde a opravíte.

## <a name="monitor-your-application-with-application-insights"></a>Monitorujte svoji aplikaci pomocí Application Insights

Application Insights je rozšiřitelná služba správy výkonu aplikací (APM) pro webové vývojáře, kteří pracují na různých platformách. Použijte ho k monitorování živé webové aplikace. Application Insights automaticky detekuje anomálie výkonu. Obsahuje výkonné analytické nástroje, které vám pomůžou s diagnostikou problémů a které vám pomůžou pochopit, co uživatelé ve vaší aplikaci skutečně dělají. Application Insights je navržený tak, aby vám pomohla průběžně zlepšovat výkon a použitelnost. Funguje pro aplikace na nejrůznějších platformách, včetně .NET, Node. js a J2EE, ať už hostovaných místně nebo v cloudu. Application Insights se integruje s vašimi procesy DevOps a má spojovací body pro celou řadu vývojářských nástrojů.

Obrázek 4-10 ukazuje příklad toho, jak Application Insights monitoruje aplikaci a jak se tyto přehledy dovádí na řídicí panel.

![Snímek obrazovky řídicího panelu monitorování Application Insights](./media/modernize-your-apps-with-monitoring-and-telemetry/application-insights-monitoring-dashboard.png)

**Obrázek 4-10.** Řídicí panel monitorování Application Insights

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a>Monitorujte infrastrukturu Docker pomocí Log Analytics a jejího řešení pro monitorování kontejnerů.

[Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) je součástí [Microsoft Azure celkového řešení monitorování](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview). Je to také služba v [Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview). Log Analytics monitoruje cloudová a místní prostředí (OMS pro místní prostředí), aby se zajistila údržba a výkon. Shromažďuje data generovaná prostředky ve vašem cloudovém a místním prostředí a také data z dalších nástrojů pro monitorování a poskytuje analýzy napříč zdroji.

Ve vztahu k protokolům infrastruktury Azure Log Analytics jako služba Azure ingestuje data protokolů a metrik z jiných služeb Azure (prostřednictvím [Azure monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), virtuálních počítačů Azure, kontejnerů Docker a místních nebo jiných cloudových infrastruktur. Log Analytics nabízí flexibilní prohledávání protokolů a předem připravené analýzy dat nad těmito daty. Poskytuje bohatých nástrojů, které můžete použít k analýze dat napříč zdroji, umožňuje komplexní dotazy ve všech protokolech a může proaktivní výstrahy na základě zadaných podmínek. Můžete dokonce shromažďovat vlastní data v úložišti centrálního Log Analytics, kde se můžete dotazovat a vizualizovat. Můžete také využít výhod Log Analytics integrovaných řešení a okamžitě získat přehled o zabezpečení a funkcích vaší infrastruktury.

K Log Analytics můžete přistupovat prostřednictvím portálu OMS nebo Azure Portal, který se spouští v jakémkoli prohlížeči, a poskytuje přístup k nastavení konfigurace a několika nástrojům pro analýzy shromážděných dat a práci s nimi.

[Řešení pro monitorování kontejnerů](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) v Log Analytics vám pomůže zobrazit a spravovat hostitele kontejnerů pro Docker a Windows v jednom umístění. Toto řešení ukazuje, které kontejnery jsou spuštěny, jaká image kontejneru je spuštěná a kde jsou spuštěné kontejnery. Můžete zobrazit podrobné informace o auditu, včetně příkazů, které se používají s kontejnery. Problémy s kontejnery můžete také řešit zobrazením a prohledáváním centralizovaných protokolů, aniž byste museli vzdáleně zobrazovat hostitele Docker nebo Windows. Můžete najít kontejnery, které by mohly být v hostiteli na vysokou úroveň a spotřebovávat nadbytečné prostředky. Kromě toho můžete zobrazit centralizovaný procesor, paměť, úložiště a využití sítě a informace o výkonu pro kontejnery. V počítačích se systémem Windows, můžete centralizovat a porovnat protokoly ze systému Windows Server Hyper-V a kontejnery Dockeru. Řešení podporuje následující orchestrátorů kontejnerů:

- Docker Swarm

- DC/OS

- Kubernetes

- Red Hat OpenShift

Obrázek 4-11 ukazuje vztahy mezi různými hostiteli a agenty kontejnerů a OMS.

![Snímek obrazovky s Log Analytics řešení pro monitorování kontejnerů](./media/modernize-your-apps-with-monitoring-and-telemetry/log-analytics-container-monitoring-solution.png)

**Obrázek 4-11.** Log Analytics řešení pro monitorování kontejnerů

Řešení monitorování kontejnerů Log Analytics můžete použít k těmto akcím:

- Podívejte se na informace o všech hostitelích kontejnerů v jednom umístění.

- Zjistěte, které kontejnery jsou spuštěné, jakou image jsou spuštěné a kde jsou spuštěné.

- Podívejte se na záznam auditu pro akce na kontejnerech.

- Řešení potíží díky zobrazení a prohledávání centralizovaných protokolů bez vzdáleného přihlášení k hostitelům Docker.

- Najděte kontejnery, které by mohly být "objekty okolí s vysokou úrovní šumu" a spotřebovávají na hostiteli nadbytečné prostředky.

- Zobrazení centralizovaného procesoru, paměti, úložiště a využití sítě a informací o výkonu pro kontejnery.

### <a name="additional-resources"></a>Další materiály a zdroje informací

- **Přehled monitorování v Microsoft Azure**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **Co je Application Insights?**

<https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **Co je Log Analytics?**

<https://docs.microsoft.com/azure/log-analytics/log-analytics-overview>

- **Řešení pro monitorování kontejnerů v Azure Monitor**

<https://docs.microsoft.com/azure/azure-monitor/insights/containers>

- **Přehled Azure Monitor**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **Co je Operations Management Suite (OMS)?**

<https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview>

>[!div class="step-by-step"]
>[Předchozí](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
>[Další](life-cycle-ci-cd-pipelines-devops-tools.md)
