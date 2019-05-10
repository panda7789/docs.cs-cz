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
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a><span data-ttu-id="080da-103">Modernizace aplikací pomocí monitorování a telemetrie</span><span class="sxs-lookup"><span data-stu-id="080da-103">Modernize your apps with monitoring and telemetry</span></span>

<span data-ttu-id="080da-104">Když spustíte aplikaci v produkčním prostředí, je velmi důležité, abyste měli přehled o výkonu vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="080da-104">When you run an application in production, it's critical that you have insights about how your application is performing.</span></span> <span data-ttu-id="080da-105">Je provádění na vysoké úrovni?</span><span class="sxs-lookup"><span data-stu-id="080da-105">Is it performing at a high level?</span></span> <span data-ttu-id="080da-106">Se uživatelé chyby, nebo pokud je aplikace stabilní a spolehlivá?</span><span class="sxs-lookup"><span data-stu-id="080da-106">Are users getting errors, or is the application stable and reliable?</span></span> <span data-ttu-id="080da-107">Potřebujete bohaté performance monitoring pro aplikace, výkonné upozorňování a řídicí panely, abyste zajistili, že aplikace je k dispozici a provádí podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="080da-107">You need rich performance monitoring, powerful alerting, and dashboards to help ensure that your application is available and performing as expected.</span></span> <span data-ttu-id="080da-108">Musíte také mít možnost rychle zobrazit, pokud je nějaký problém, určit, kolik zákazníků se to týká a provádět analýzy původních příčin vyhledat a opravit tento problém.</span><span class="sxs-lookup"><span data-stu-id="080da-108">You also need to be able to see quickly if there's a problem, determine how many customers are affected, and perform a root-cause analysis to find and fix the issue.</span></span>

## <a name="monitor-your-application-with-application-insights"></a><span data-ttu-id="080da-109">Můžete monitorovat své aplikace pomocí Application Insights</span><span class="sxs-lookup"><span data-stu-id="080da-109">Monitor your application with Application Insights</span></span>

<span data-ttu-id="080da-110">Application Insights je rozšiřitelná služba správu výkonu aplikací (APM) pro webové vývojáře, kteří pracují na různých platformách.</span><span class="sxs-lookup"><span data-stu-id="080da-110">Application Insights is an extensible Application Performance Management (APM) service for web developers who work on multiple platforms.</span></span> <span data-ttu-id="080da-111">Použijte ho k monitorování živé webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="080da-111">Use it to monitor your live web application.</span></span> <span data-ttu-id="080da-112">Application Insights automaticky zjišťuje anomálie výkonu.</span><span class="sxs-lookup"><span data-stu-id="080da-112">Application Insights automatically detects performance anomalies.</span></span> <span data-ttu-id="080da-113">Obsahuje výkonné analytické nástroje můžete diagnostikovat problémy a které vám pomohou pochopit, co uživatelé dělají s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="080da-113">It includes powerful analytics tools to help you diagnose issues, and to help you understand what users actually do with your app.</span></span> <span data-ttu-id="080da-114">Application Insights je určena k pomáhala průběžně vylepšovat výkon a použitelnost.</span><span class="sxs-lookup"><span data-stu-id="080da-114">Application Insights is designed to help you continuously improve performance and usability.</span></span> <span data-ttu-id="080da-115">Funguje pro aplikace na nejrůznějších platformách, včetně .NET, Node.js a J2EE, ať už hostovaný místně nebo v cloudu.</span><span class="sxs-lookup"><span data-stu-id="080da-115">It works for apps on a wide variety of platforms, including .NET, Node.js, and J2EE, whether hosted on-premises or in the cloud.</span></span> <span data-ttu-id="080da-116">Application Insights integruje do svých procesů DevOps a má spojovací body s celou řadu nástrojů pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="080da-116">Application Insights integrates with your DevOps processes, and has connection points to a variety of development tools.</span></span>

<span data-ttu-id="080da-117">Obrázek 4 – 10 ukazuje příklad, jak Application Insights monitoruje vaše aplikace a jak zobrazí tyto přehledy na řídicí panel.</span><span class="sxs-lookup"><span data-stu-id="080da-117">Figure 4-10 shows an example of how Application Insights monitors your application and how it surfaces those insights to a dashboard.</span></span>

![Monitorování řídicího panelu služby Application Insights](./media/image10.png)

> <span data-ttu-id="080da-119">**Obrázek 4 – 10.**</span><span class="sxs-lookup"><span data-stu-id="080da-119">**Figure 4-10.**</span></span> <span data-ttu-id="080da-120">Monitorování řídicího panelu služby Application Insights</span><span class="sxs-lookup"><span data-stu-id="080da-120">Application Insights monitoring dashboard</span></span>

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a><span data-ttu-id="080da-121">Monitorování infrastruktury Dockeru s Log Analytics a jeho řešení pro monitorování kontejnerů</span><span class="sxs-lookup"><span data-stu-id="080da-121">Monitor your Docker infrastructure with Log Analytics and its Container Monitoring solution</span></span>

<span data-ttu-id="080da-122">[Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) je součástí [celkového monitorovacího řešení Microsoft Azure](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview).</span><span class="sxs-lookup"><span data-stu-id="080da-122">[Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) is part of the [Microsoft Azure overall monitoring solution](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview).</span></span> <span data-ttu-id="080da-123">Je také služby [Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview).</span><span class="sxs-lookup"><span data-stu-id="080da-123">It's also a service in [Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview).</span></span> <span data-ttu-id="080da-124">Log Analytics monitoruje Cloudová a místní prostředí (OMS pro místní), který pomáhá zajistit dostupnost a výkon.</span><span class="sxs-lookup"><span data-stu-id="080da-124">Log Analytics monitors cloud and on-premises environments (OMS for on-premises) to help maintain availability and performance.</span></span> <span data-ttu-id="080da-125">Shromažďuje data generovaná prostředky ve vašem cloudovém a místním prostředí a také data z dalších nástrojů pro monitorování a poskytuje analýzy napříč zdroji.</span><span class="sxs-lookup"><span data-stu-id="080da-125">It collects data generated by resources in your cloud and on-premises environments and from other monitoring tools to provide analysis across multiple sources.</span></span>

<span data-ttu-id="080da-126">Ve vztahu k protokolů infrastruktury Azure Log Analytics jako služby Azure a ingestuje data protokolů a metrik z ostatních služeb Azure (prostřednictvím [Azure Monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), virtuální počítače Azure, kontejnery Docker a on-premises nebo jiných cloudových infrastruktur.</span><span class="sxs-lookup"><span data-stu-id="080da-126">In relation to Azure infrastructure logs, Log Analytics, as an Azure service, ingests log and metric data from other Azure services (via [Azure Monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), Azure VMs, Docker containers, and on-premises or other cloud infrastructures.</span></span> <span data-ttu-id="080da-127">Log Analytics nabízí flexibilní protokol vyhledávání a analýzy out-představené na tato data.</span><span class="sxs-lookup"><span data-stu-id="080da-127">Log Analytics offers flexible log search and out-of-the box analytics on top of this data.</span></span> <span data-ttu-id="080da-128">Nabízí bohaté možnosti nástrojů, můžete použít k analýze dat napříč zdroji, umožňuje složitých dotazů ve všech protokolů a proaktivně může upozornit na základě zadaných podmínek.</span><span class="sxs-lookup"><span data-stu-id="080da-128">It provides rich tools that you can use to analyze data across sources, it allows complex queries across all logs, and it can proactively alert based on specified conditions.</span></span> <span data-ttu-id="080da-129">Můžete dokonce shromáždění vlastních dat do centrálního úložiště Log Analytics, kde se můžete dotazovat a vizualizovat.</span><span class="sxs-lookup"><span data-stu-id="080da-129">You can even collect custom data in the central Log Analytics repository, where you can query and visualize it.</span></span> <span data-ttu-id="080da-130">Také můžete využít výhod integrovaných řešení Log Analytics umožňuje získat okamžitý přehled o zabezpečení a funkce vaší infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="080da-130">You also can take advantage of the Log Analytics built-in solutions to immediately gain insights into the security and functionality of your infrastructure.</span></span>

<span data-ttu-id="080da-131">Můžete používat Log Analytics na portálu OMS nebo webu Azure portal, který se spustit v jakémkoli prohlížeči, a poskytují přístup k nastavení konfigurace a několika nástrojům analyzovat a zpracovat shromážděná data.</span><span class="sxs-lookup"><span data-stu-id="080da-131">You can access Log Analytics through the OMS portal or the Azure portal, which run in any browser, and provide you with access to configuration settings and multiple tools to analyze and act on collected data.</span></span>

<span data-ttu-id="080da-132">[Řešení pro monitorování kontejnerů](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) v Log Analytics vám umožňuje zobrazit a spravovat hostitele Dockeru a kontejnerech Windows na jednom místě.</span><span class="sxs-lookup"><span data-stu-id="080da-132">The [Container Monitoring solution](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) in Log Analytics helps you view and manage your Docker and Windows Container hosts in a single location.</span></span> <span data-ttu-id="080da-133">Toto řešení ukazuje, které kontejnery jsou spuštěná, jaké image kontejnerů běží a kde kontejnery běží.</span><span class="sxs-lookup"><span data-stu-id="080da-133">The solution shows which containers are running, what container image they're running, and where containers are running.</span></span> <span data-ttu-id="080da-134">Můžete zobrazit podrobné informace auditu, včetně příkazů, které se používají s kontejnery.</span><span class="sxs-lookup"><span data-stu-id="080da-134">You can view detailed audit information, including commands that are being used with containers.</span></span> <span data-ttu-id="080da-135">Kontejnery také můžete řešit pomocí zobrazení a hledání centralizované protokoly, aniž byste museli vzdáleně zobrazení hostitele Docker nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="080da-135">You also can troubleshoot containers by viewing and searching centralized logs, without needing to remotely view Docker or Windows hosts.</span></span> <span data-ttu-id="080da-136">Můžete najít kontejnery, které mohou být na hostiteli hlučného a využívání nadbytečné prostředky.</span><span class="sxs-lookup"><span data-stu-id="080da-136">You can find containers that might be noisy and consuming excess resources on a host.</span></span> <span data-ttu-id="080da-137">Kromě toho můžete zobrazit centralizované procesoru, paměti, úložiště a využití sítě a informace o výkonu pro kontejnery.</span><span class="sxs-lookup"><span data-stu-id="080da-137">Additionally, you can view centralized CPU, memory, storage, and network usage, and performance information, for containers.</span></span> <span data-ttu-id="080da-138">V počítačích se systémem Windows, můžete centralizovat a porovnat protokoly ze systému Windows Server Hyper-V a kontejnery Dockeru.</span><span class="sxs-lookup"><span data-stu-id="080da-138">On computers running Windows, you can centralize and compare logs from Windows Server, Hyper-V, and Docker containers.</span></span> <span data-ttu-id="080da-139">Řešení podporuje následující orchestrátorů kontejnerů:</span><span class="sxs-lookup"><span data-stu-id="080da-139">The solution supports the following container orchestrators:</span></span>

- <span data-ttu-id="080da-140">Docker Swarm</span><span class="sxs-lookup"><span data-stu-id="080da-140">Docker Swarm</span></span>

- <span data-ttu-id="080da-141">DC/OS</span><span class="sxs-lookup"><span data-stu-id="080da-141">DC/OS</span></span>

- <span data-ttu-id="080da-142">Kubernetes</span><span class="sxs-lookup"><span data-stu-id="080da-142">Kubernetes</span></span>

- <span data-ttu-id="080da-143">Service Fabric</span><span class="sxs-lookup"><span data-stu-id="080da-143">Service Fabric</span></span>

- <span data-ttu-id="080da-144">Red Hat OpenShift</span><span class="sxs-lookup"><span data-stu-id="080da-144">Red Hat OpenShift</span></span>

<span data-ttu-id="080da-145">Obrázek 4 – 11 znázorňuje vztahy mezi různými hostitelích kontejnerů a agentů a OMS.</span><span class="sxs-lookup"><span data-stu-id="080da-145">Figure 4-11 shows the relationships between various container hosts and agents and OMS.</span></span>

![Řešení log Analytics monitorování kontejnerů](./media/image11.png)

> <span data-ttu-id="080da-147">**Obrázek 4 – 11.**</span><span class="sxs-lookup"><span data-stu-id="080da-147">**Figure 4-11.**</span></span> <span data-ttu-id="080da-148">Řešení log Analytics monitorování kontejnerů</span><span class="sxs-lookup"><span data-stu-id="080da-148">Log Analytics Container Monitoring solution</span></span>

<span data-ttu-id="080da-149">Řešení monitorování kontejnerů Log Analytics můžete použít:</span><span class="sxs-lookup"><span data-stu-id="080da-149">You can use the Log Analytics Container Monitoring solution to:</span></span>

- <span data-ttu-id="080da-150">Zobrazit informace o všech hostitelích kontejnerů na jednom místě.</span><span class="sxs-lookup"><span data-stu-id="080da-150">See information about all container hosts in a single location.</span></span>

- <span data-ttu-id="080da-151">Zjistit, které kontejnery jsou spuštěná, jaké image spuštěnými, a pokud máte spuštěnou.</span><span class="sxs-lookup"><span data-stu-id="080da-151">Know which containers are running, what image they're running, and where they're running.</span></span>

- <span data-ttu-id="080da-152">Najdete v protokolu auditu pro akce v kontejnerech.</span><span class="sxs-lookup"><span data-stu-id="080da-152">See an audit trail for actions on containers.</span></span>

- <span data-ttu-id="080da-153">Řešení potíží zobrazením a hledání centralizované protokoly bez vzdálené přihlášení na hostitele Dockeru.</span><span class="sxs-lookup"><span data-stu-id="080da-153">Troubleshoot by viewing and searching centralized logs without remote login to the Docker hosts.</span></span>

- <span data-ttu-id="080da-154">Najdete kontejnerů, které mohou být "" hlučným sousedům"" a by spotřebovávalo nadbytečné prostředků na hostiteli.</span><span class="sxs-lookup"><span data-stu-id="080da-154">Find containers that might be "noisy neighbors," and be consuming excess resources on a host.</span></span>

- <span data-ttu-id="080da-155">Zobrazte centralizované procesoru, paměti, úložiště a využití sítě a informace o výkonu pro kontejnery.</span><span class="sxs-lookup"><span data-stu-id="080da-155">View centralized CPU, memory, storage, and network usage, and performance information, for containers.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="080da-156">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="080da-156">Additional resources</span></span>

- <span data-ttu-id="080da-157">**Přehled monitorování v Microsoft Azure**</span><span class="sxs-lookup"><span data-stu-id="080da-157">**Overview of monitoring in Microsoft Azure**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="080da-158">**Co je Application Insights?**</span><span class="sxs-lookup"><span data-stu-id="080da-158">**What is Application Insights?**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- <span data-ttu-id="080da-159">**Co je služba Log Analytics?**</span><span class="sxs-lookup"><span data-stu-id="080da-159">**What is Log Analytics?**</span></span>

<https://docs.microsoft.com/azure/log-analytics/log-analytics-overview>

- <span data-ttu-id="080da-160">**Řešení pro monitorování kontejnerů ve službě Azure Monitor**</span><span class="sxs-lookup"><span data-stu-id="080da-160">**Container Monitoring solution in Azure Monitor**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/insights/containers>

- <span data-ttu-id="080da-161">**Přehled služby Azure Monitor**</span><span class="sxs-lookup"><span data-stu-id="080da-161">**Overview of Azure Monitor**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="080da-162">**Co je Operations Management Suite (OMS)?**</span><span class="sxs-lookup"><span data-stu-id="080da-162">**What is Operations Management Suite (OMS)?**</span></span>

<https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview>

- <span data-ttu-id="080da-163">**Monitorování kontejnerů Windows serveru v Service Fabric pomocí OMS**</span><span class="sxs-lookup"><span data-stu-id="080da-163">**Monitoring Windows Server containers in Service Fabric with OMS**</span></span>

<https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver>

>[!div class="step-by-step"]
><span data-ttu-id="080da-164">[Předchozí](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
>[další](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="080da-164">[Previous](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
[Next](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)</span></span>
