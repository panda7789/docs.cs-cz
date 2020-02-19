---
title: Monitorování ve službě Azure Kubernetes Service
description: Monitorování ve službě Azure Kubernetes Service
ms.date: 02/05/2020
ms.openlocfilehash: 5c46b9e8599f70d430ad26cf1364343454d30a16
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450060"
---
# <a name="monitoring-in-azure-kubernetes-services"></a>Monitorování ve službě Azure Kubernetes Service

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Integrované protokolování v Kubernetes je primitivní. Existují však skvělé možnosti pro získání protokolů z Kubernetes a na místo, kde je lze správně analyzovat. Pokud potřebujete monitorovat clustery AKS, je ideálním řešením konfigurace elastického zásobníku pro Kubernetes.

## <a name="azure-monitor-for-containers"></a>Azure Monitor pro kontejnery

[Azure monitor for Containers](https://docs.microsoft.com/azure/azure-monitor/insights/container-insights-overview) podporuje využívání protokolů nejenom Kubernetes, ale také z jiných modulů orchestrace, jako jsou DC/OS, Docker Swarm a Red Hat OpenShift.

![využívání protokolů z různých kontejnerů](./media/containers-diagram.png)
**obrázek 7-10**. Využívání protokolů z různých kontejnerů

[Prometheus](https://prometheus.io/) je oblíbený open source řešení pro monitorování metrik. Je součástí cloudové nativní výpočetní platformy. Použití Prometheus obvykle vyžaduje správu serveru Prometheus s vlastním úložištěm. [Azure monitor for Containers ale poskytuje přímou integraci s koncovými body metrik Prometheus](https://docs.microsoft.com/azure/azure-monitor/insights/container-insights-prometheus-integration), takže se nevyžaduje samostatný server.

Informace o protokolu a metrikě se shromažďují nejen z kontejnerů spuštěných v clusteru, ale také z hostitelů clusteru. Umožňuje korelační informace protokolu z obou dvou, což znamená, že je mnohem jednodušší sledovat chybu.

Instalace sběračů protokolů se liší v clusterech se [systémy Windows](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes) a [Linux](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes) . V obou případech je však kolekce protokolů implementována jako Kubernetes [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/), což znamená, že kolektor protokolů je spuštěn jako kontejner na každém uzlu.

Bez ohledu na to, který Orchestrator nebo operační systém spouští démon Azure Monitor, jsou informace protokolu předávány stejným Azure Monitor nástrojům, se kterými se uživatelé znají. Tím se zajistí paralelní prostředí v prostředích, která jsou kombinací různých zdrojů protokolů, jako je hybridní Kubernetes nebo Azure Functions prostředí.

![ukázkový řídicí panel, který zobrazuje informace o protokolování a metrikě z řady spuštěných kontejnerů.](./media/containers-dashboard.png)
**obrázek 7-11**. Vzorový řídicí panel, který zobrazuje informace o protokolování a metrikách z řady spuštěných kontejnerů.

## <a name="logfinalize"></a>Log. Finalize ()

Protokolování je jedním z nejoblíbenějších a ještě nejdůležitějších součástí nasazení libovolné aplikace ve velkém měřítku. Jak se zvyšuje velikost a složitost aplikací, pak je obtížné je ladit. Díky dostupným protokolům nejvyšší kvality je ladění mnohem jednodušší a přesune je ze sféry "skoro nemožné" na "příjemný zážitek".

>[!div class="step-by-step"]
>[Předchozí](logging-with-elastic-stack.md)
>[Další](azure-monitor.md)
