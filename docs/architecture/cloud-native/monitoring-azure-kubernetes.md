---
title: Monitorování ve službě Azure Kubernetes Service
description: Monitorování ve službě Azure Kubernetes Service
ms.date: 09/23/2019
ms.openlocfilehash: fc9d84fd738ff1c40d25860680e14313c9323517
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711646"
---
# <a name="monitoring-in-azure-kubernetes-services"></a><span data-ttu-id="ce846-103">Monitorování ve službě Azure Kubernetes Service</span><span class="sxs-lookup"><span data-stu-id="ce846-103">Monitoring in Azure Kubernetes Services</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="ce846-104">Integrované protokolování v Kubernetes je primitivní.</span><span class="sxs-lookup"><span data-stu-id="ce846-104">The built-in logging in Kubernetes is primitive.</span></span> <span data-ttu-id="ce846-105">Existují však skvělé možnosti pro získání protokolů z Kubernetes a na místo, kde je lze správně analyzovat.</span><span class="sxs-lookup"><span data-stu-id="ce846-105">However, there are some great options for getting the logs out of Kubernetes and into a place where they can be properly analyzed.</span></span> <span data-ttu-id="ce846-106">Pokud potřebujete monitorovat clustery AKS, je ideálním řešením konfigurace elastického zásobníku pro Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="ce846-106">If you need to monitor your AKS clusters, configuring Elastic Stack for Kubernetes is a great solution.</span></span>

## <a name="elastic-stack"></a><span data-ttu-id="ce846-107">Elastický zásobník</span><span class="sxs-lookup"><span data-stu-id="ce846-107">Elastic Stack</span></span>

<span data-ttu-id="ce846-108">Elastický zásobník je efektivní možností pro shromažďování informací z clusteru Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="ce846-108">The Elastic Stack is a powerful option for gathering information from a Kubernetes cluster.</span></span> <span data-ttu-id="ce846-109">Kubernetes podporuje odesílání protokolů do koncového bodu Elasticsearch a ve [většině případů](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/)je potřeba začít s nastavením proměnných prostředí, jak je znázorněno na obrázku 7-5:</span><span class="sxs-lookup"><span data-stu-id="ce846-109">Kubernetes supports sending logs to an Elasticsearch endpoint, and for the [most part](https://kubernetes.io/docs/tasks/debug-application-cluster/logging-elasticsearch-kibana/), all you need to get started is to set the environment variables as shown in Figure 7-5:</span></span>

```kubernetes
KUBE_LOGGING_DESTINATION=elasticsearch
KUBE_ENABLE_NODE_LOGGING=true
```

<span data-ttu-id="ce846-110">**Obrázek 7-5** – proměnné konfigurace pro Kubernetes</span><span class="sxs-lookup"><span data-stu-id="ce846-110">**Figure 7-5** - Configuration variables for Kubernetes</span></span>

<span data-ttu-id="ce846-111">Tím se do clusteru nainstaluje Elasticsearch a do něj budou odesílány všechny protokoly clusteru.</span><span class="sxs-lookup"><span data-stu-id="ce846-111">This will install Elasticsearch on the cluster and target sending all the cluster logs to it.</span></span>

<span data-ttu-id="ce846-112">![příklad řídicího panelu Kibana ukazující výsledky dotazu na protokoly ingestované z Kubernetes](./media/kibana-dashboard.png)
**obrázek 7-6**.</span><span class="sxs-lookup"><span data-stu-id="ce846-112">![An example of a Kibana dashboard showing the results of a query against logs ingested from Kubernetes](./media/kibana-dashboard.png)
**Figure 7-6**.</span></span> <span data-ttu-id="ce846-113">Příklad řídicího panelu Kibana znázorňující výsledky dotazu proti protokolům, které jsou ingestované z Kubernetes</span><span class="sxs-lookup"><span data-stu-id="ce846-113">An example of a Kibana dashboard showing the results of a query against logs that are ingested from Kubernetes</span></span>

## <a name="azure-container-monitoring"></a><span data-ttu-id="ce846-114">Monitorování kontejnerů Azure</span><span class="sxs-lookup"><span data-stu-id="ce846-114">Azure Container Monitoring</span></span>

<span data-ttu-id="ce846-115">Azure Container monitor podporuje využívání protokolů nejenom Kubernetes, ale také z jiných modulů orchestrace, jako jsou DC/OS, Docker Swarm a Red Hat OpenShift.</span><span class="sxs-lookup"><span data-stu-id="ce846-115">Azure Container Monitoring supports consuming logs from not just Kubernetes but also from other orchestration engines such as DC/OS, Docker Swarm, and Red Hat OpenShift.</span></span>

<span data-ttu-id="ce846-116">![využívání protokolů z různých kontejnerů](./media/containers-diagram.png)
**obrázek 7-7**.</span><span class="sxs-lookup"><span data-stu-id="ce846-116">![Consuming logs from various containers](./media/containers-diagram.png)
**Figure 7-7**.</span></span>  <span data-ttu-id="ce846-117">Využívání protokolů z různých kontejnerů</span><span class="sxs-lookup"><span data-stu-id="ce846-117">Consuming logs from various containers</span></span>

<span data-ttu-id="ce846-118">Informace o protokolu a metrikě se shromažďují nejen z kontejnerů spuštěných v clusteru, ale také z hostitelů clusteru.</span><span class="sxs-lookup"><span data-stu-id="ce846-118">Log and metric information is gathered not just from the containers running in the cluster but also from the cluster hosts themselves.</span></span> <span data-ttu-id="ce846-119">Umožňuje korelační informace protokolu z obou dvou, což znamená, že je mnohem jednodušší sledovat chybu.</span><span class="sxs-lookup"><span data-stu-id="ce846-119">It allows correlating log information from the two making it much easier to track down an error.</span></span>

<span data-ttu-id="ce846-120">Instalace sběračů protokolů se liší v clusterech se [systémy Windows](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes) a [Linux](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes) .</span><span class="sxs-lookup"><span data-stu-id="ce846-120">Installing the log collectors differs on [Windows](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-windows-agent-for-kubernetes) and [Linux](https://docs.microsoft.com/azure/azure-monitor/insights/containers#configure-a-log-analytics-linux-agent-for-kubernetes) clusters.</span></span> <span data-ttu-id="ce846-121">V obou případech je však kolekce protokolů implementována jako Kubernetes [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/), což znamená, že kolektor protokolů je spuštěn jako kontejner na každém uzlu.</span><span class="sxs-lookup"><span data-stu-id="ce846-121">But in both cases the log collection is implemented as a Kubernetes [DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/), meaning that the log collector is run as a container on each of the nodes.</span></span>

<span data-ttu-id="ce846-122">Bez ohledu na to, který Orchestrator nebo operační systém spouští démon Azure Monitor, jsou informace protokolu předávány stejným Azure Monitor nástrojům, se kterými se uživatelé znají.</span><span class="sxs-lookup"><span data-stu-id="ce846-122">No matter which orchestrator or operating system is running the Azure Monitor daemon, the log information is forwarded to the same Azure Monitor tools with which users are familiar.</span></span> <span data-ttu-id="ce846-123">Tím se zajistí paralelní prostředí v prostředích, která jsou kombinací různých zdrojů protokolů, jako je hybridní Kubernetes nebo Azure Functions prostředí.</span><span class="sxs-lookup"><span data-stu-id="ce846-123">This ensures a parallel experience in environments that mix different log sources such as a hybrid Kubernetes/Azure Functions environment.</span></span>

<span data-ttu-id="ce846-124">![ukázkový řídicí panel, který zobrazuje informace o protokolování a metrikě z řady spuštěných kontejnerů.](./media/containers-dashboard.png)
**obrázek 7-8**.</span><span class="sxs-lookup"><span data-stu-id="ce846-124">![A sample dashboard showing logging and metric information from a number of running containers.](./media/containers-dashboard.png)
**Figure 7-8**.</span></span> <span data-ttu-id="ce846-125">Vzorový řídicí panel, který zobrazuje informace o protokolování a metrikách z řady spuštěných kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="ce846-125">A sample dashboard showing logging and metric information from a number of running containers.</span></span>

## <a name="logfinalize"></a><span data-ttu-id="ce846-126">Log. Finalize ()</span><span class="sxs-lookup"><span data-stu-id="ce846-126">Log.Finalize()</span></span>

<span data-ttu-id="ce846-127">Protokolování je jedním z nejoblíbenějších a ještě nejdůležitějších součástí nasazení libovolné aplikace ve velkém měřítku.</span><span class="sxs-lookup"><span data-stu-id="ce846-127">Logging is one of the most overlooked and yet most important parts of deploying any application at scale.</span></span> <span data-ttu-id="ce846-128">Jak se zvyšuje velikost a složitost aplikací, pak je obtížné je ladit.</span><span class="sxs-lookup"><span data-stu-id="ce846-128">As the size and complexity of applications increase, then so does the difficulty of debugging them.</span></span> <span data-ttu-id="ce846-129">Díky dostupným protokolům nejvyšší kvality je ladění mnohem jednodušší a přesune je ze sféry "skoro nemožné" na "příjemný zážitek".</span><span class="sxs-lookup"><span data-stu-id="ce846-129">Having top quality logs available makes debugging much easier and moves it from the realm of "nearly impossible" to "a pleasant experience".</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ce846-130">[Předchozí](logging-with-elastic-stack.md)
>[Další](azure-monitor.md)</span><span class="sxs-lookup"><span data-stu-id="ce846-130">[Previous](logging-with-elastic-stack.md)
[Next](azure-monitor.md)</span></span>
