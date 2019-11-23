---
title: Monitorování ve službě Azure Kubernetes Service
description: Monitorování ve službě Azure Kubernetes Service
ms.date: 09/23/2019
ms.openlocfilehash: 71192601eac2169db188b25da3dc91b71b860903
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184986"
---
# <a name="monitoring-in-azure-kubernetes-services"></a>Monitorování ve službě Azure Kubernetes Service

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Integrované protokolování v Kubernetes je primitivní. Existují však skvělé možnosti pro získání protokolů z Kubernetes a na místo, kde je lze správně analyzovat. Pokud potřebujete monitorovat clustery AKS, je ideálním řešením konfigurace elastického zásobníku pro Kubernetes.

## <a name="elastic-stack"></a>Elastický zásobník

Elastický zásobník je efektivní možností pro shromažďování informací z clusteru Kubernetes. Kubernetes podporuje odesílání protokolů do koncového bodu Elasticsearch a ve [většině případů](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/)je potřeba začít s nastavením proměnných prostředí, jak je znázorněno na obrázku 7-5:

```kubernetes
KUBE_LOGGING_DESTINATION=elasticsearch
KUBE_ENABLE_NODE_LOGGING=true
```

**Obrázek 7-5** – proměnné konfigurace pro Kubernetes

Tím se do clusteru nainstaluje Elasticsearch a do něj budou odesílány všechny protokoly clusteru.

![příklad řídicího panelu Kibana ukazující výsledky dotazu na protokoly ingestované z Kubernetes](./media/kibana-dashboard.png)
**obrázek 7-6**. Příklad řídicího panelu Kibana znázorňující výsledky dotazu proti protokolům, které jsou ingestované z Kubernetes

## <a name="azure-container-monitoring"></a>Monitorování kontejnerů Azure

Azure Container monitor podporuje využívání protokolů nejenom Kubernetes, ale také z jiných modulů orchestrace, jako jsou DC/OS, Docker Swarm a Red Hat OpenShift.

![využívání protokolů z různých kontejnerů](./media/containers-diagram.png)
**obrázek 7-7**.  Využívání protokolů z různých kontejnerů

Informace o protokolu a metrikě se shromažďují nejen z kontejnerů spuštěných v clusteru, ale také z hostitelů clusteru. Umožňuje korelační informace protokolu z obou dvou, což znamená, že je mnohem jednodušší sledovat chybu.

Instalace sběračů protokolů se liší v clusterech se [systémy Windows](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes) a [Linux](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes) . V obou případech je však kolekce protokolů implementována jako Kubernetes [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/), což znamená, že kolektor protokolů je spuštěn jako kontejner na každém uzlu.

Bez ohledu na to, který Orchestrator nebo operační systém spouští démon Azure Monitor, jsou informace protokolu předávány stejným Azure Monitor nástrojům, se kterými se uživatelé znají. Tím se zajistí paralelní prostředí v prostředích, která jsou kombinací různých zdrojů protokolů, jako je hybridní Kubernetes nebo Azure Functions prostředí.

![ukázkový řídicí panel, který zobrazuje informace o protokolování a metrikě z řady spuštěných kontejnerů.](./media/containers-dashboard.png)
**obrázek 7-8**. Vzorový řídicí panel, který zobrazuje informace o protokolování a metrikách z řady spuštěných kontejnerů.

## <a name="logfinalize"></a>Log. Finalize ()

Protokolování je jedním z nejoblíbenějších a ještě nejdůležitějších součástí nasazení libovolné aplikace ve velkém měřítku. Jak se zvyšuje velikost a složitost aplikací, pak je obtížné je ladit. Díky dostupným protokolům nejvyšší kvality je ladění mnohem jednodušší a přesune je ze sféry "skoro nemožné" na "příjemný zážitek".

>[!div class="step-by-step"]
>[Předchozí](logging-with-elastic-stack.md)
>[Další](azure-monitor.md)
