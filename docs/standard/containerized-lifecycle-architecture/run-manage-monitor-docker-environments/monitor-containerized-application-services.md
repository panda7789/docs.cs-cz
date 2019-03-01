---
title: Monitorování kontejnerizovaných aplikačních služeb
description: Přečtěte si některé klíčové aspekty monitorování kontejneru architektury
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 925db543617deb28590cf6631ebbda3ee96836c4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975742"
---
# <a name="monitor-containerized-application-services"></a><span data-ttu-id="15efc-103">Monitorování kontejnerizovaných aplikačních služeb</span><span class="sxs-lookup"><span data-stu-id="15efc-103">Monitor containerized application services</span></span>

<span data-ttu-id="15efc-104">Je velmi důležité pro aplikace rozdělit do několika kontejnery a mikroslužby způsob, jak monitorovat a analyzovat chování celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="15efc-104">It's critical for applications split into multiple containers and microservices to have a way to monitor and analyze the behavior of the whole application.</span></span>

## <a name="microsoft-application-insights"></a><span data-ttu-id="15efc-105">Microsoft Application Insights</span><span class="sxs-lookup"><span data-stu-id="15efc-105">Microsoft Application Insights</span></span>

<span data-ttu-id="15efc-106">[Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview) je rozšiřitelnou analytickou službu, která monitoruje vaše živé aplikace.</span><span class="sxs-lookup"><span data-stu-id="15efc-106">[Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview) is an extensible analytics service that monitors your live application.</span></span> <span data-ttu-id="15efc-107">Pomáhá detekovat a diagnostikovat problémy s výkonem a pochopit, co uživatelé dělají s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="15efc-107">It helps you to detect and diagnose performance issues and to understand what users actually do with your app.</span></span> <span data-ttu-id="15efc-108">Je určená pro vývojáře se záměrem pomáhá průběžně zlepšit výkon a použitelnost služby nebo aplikace.</span><span class="sxs-lookup"><span data-stu-id="15efc-108">It's designed for developers, with the intent of helping you to continuously improve the performance and usability of your services or applications.</span></span> <span data-ttu-id="15efc-109">Application Insights pracuje s webovou nebo služeb Team Foundation a samostatné aplikace na různých platformách jako .NET, Java, Node.js a mnoho dalších platforem hostovaný místně nebo v cloudu.</span><span class="sxs-lookup"><span data-stu-id="15efc-109">Application Insights works with both web/services and standalone apps on a wide variety of platforms like .NET, Java, Node.js and many other platforms, hosted on-premises or in the cloud.</span></span>

### <a name="analyzing-docker-apps-in-qa-environments-using-application-insights"></a><span data-ttu-id="15efc-110">Analýza aplikací Dockeru v prostředí QA pomocí Application Insights</span><span class="sxs-lookup"><span data-stu-id="15efc-110">Analyzing Docker apps in QA environments using Application Insights</span></span>

<span data-ttu-id="15efc-111">Protože se týkají Dockeru, můžete graf události životního cyklu a čítače výkonu z kontejnerů Dockeru v Application Insights.</span><span class="sxs-lookup"><span data-stu-id="15efc-111">As it pertains to Docker, you can chart life-cycle events and performance counters from Docker containers on Application Insights.</span></span> <span data-ttu-id="15efc-112">Stačí spustit [image Dockeru Application Insights](https://hub.docker.com/r/microsoft/applicationinsights/) jako kontejner v hostiteli který se zobrazí čítače výkonu pro hostitele stejně jako u jiných Image Dockeru.</span><span class="sxs-lookup"><span data-stu-id="15efc-112">You just need to run the [Application Insights Docker image](https://hub.docker.com/r/microsoft/applicationinsights/) as a container in your host, and it will display performance counters for the host as well as for the other Docker images.</span></span> <span data-ttu-id="15efc-113">Tato image Dockeru Application Insights (obrázek 6 - 1) vám umožní monitorovat své kontejnerizované aplikace pomocí shromažďování telemetrických dat o výkonu a aktivitu (to znamená, že vaše virtuální počítače s Linuxem) hostitele Docker, kontejnery Docker a aplikace běžící v nich.</span><span class="sxs-lookup"><span data-stu-id="15efc-113">This Application Insights Docker image (Figure 6-1) helps you to monitor your containerized applications by collecting telemetry about the performance and activity of your Docker host (that is, your Linux VMs), Docker containers and the applications running within them.</span></span>

![příklad](./media/image1.png)

<span data-ttu-id="15efc-115">**Obrázek 6-1**.</span><span class="sxs-lookup"><span data-stu-id="15efc-115">**Figure 6-1**.</span></span> <span data-ttu-id="15efc-116">Application Insights, monitorování hostitelů Docker a kontejnery</span><span class="sxs-lookup"><span data-stu-id="15efc-116">Application Insights monitoring Docker hosts and containers</span></span>

<span data-ttu-id="15efc-117">Při spuštění [image Dockeru Application Insights](https://hub.docker.com/r/microsoft/applicationinsights/) na hostiteli Dockeru, můžete využívat následující:</span><span class="sxs-lookup"><span data-stu-id="15efc-117">When you run the [Application Insights Docker image](https://hub.docker.com/r/microsoft/applicationinsights/) on your Docker host, you benefit from the following:</span></span>

- <span data-ttu-id="15efc-118">Životní cyklus telemetrická data o všechny kontejnery běží na hostiteli, spuštění, zastavení a tak dále.</span><span class="sxs-lookup"><span data-stu-id="15efc-118">Life-cycle telemetry about all the containers running on the host—start, stop, and so on.</span></span>

- <span data-ttu-id="15efc-119">Čítače výkonu pro všechny kontejnery: Procesoru, paměti, využití sítě a další.</span><span class="sxs-lookup"><span data-stu-id="15efc-119">Performance counters for all the containers: CPU, memory, network usage, and more.</span></span>

- <span data-ttu-id="15efc-120">Pokud jste nainstalovali také [Application Insights SDK](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net) v aplikace spuštěné v kontejnerech, bude mít veškerá telemetrická data těchto aplikací další vlastnosti identifikující kontejner a hostitele počítače.</span><span class="sxs-lookup"><span data-stu-id="15efc-120">If you also installed [Application Insights SDK](https://docs.microsoft.com/azure/application-insights/app-insights-asp-net) in the apps running in the containers, all the telemetry of those apps will have additional properties identifying the container and host machine.</span></span> <span data-ttu-id="15efc-121">Ano například pokud máte instancí aplikace běžící ve více než jednoho hostitele, snadno budete mít k filtrování telemetrie vaší aplikace hostitel.</span><span class="sxs-lookup"><span data-stu-id="15efc-121">So, for example, if you have instances of an app running in more than one host, you'll easily be able to filter your app telemetry by host.</span></span>

### <a name="setting-up-application-insights-to-monitor-docker-applications-and-docker-hosts"></a><span data-ttu-id="15efc-122">Nastavení Application Insights pro monitorování aplikací Dockeru a hostitelů Docker</span><span class="sxs-lookup"><span data-stu-id="15efc-122">Setting up Application Insights to monitor Docker applications and Docker hosts</span></span>

<span data-ttu-id="15efc-123">Vytvořte prostředek Application Insights, postupujte podle pokynů v článcích, které jsou uvedeny v následujícím seznamu.</span><span class="sxs-lookup"><span data-stu-id="15efc-123">To create an Application Insights resource, follow the instructions in the articles presented in the list that follows.</span></span> <span data-ttu-id="15efc-124">Azure portal vytvoří nezbytné skript za vás.</span><span class="sxs-lookup"><span data-stu-id="15efc-124">Azure portal will create the necessary script for you.</span></span>

- <span data-ttu-id="15efc-125">**Monitorování aplikací Dockeru ve službě Application Insights:** \\</span><span class="sxs-lookup"><span data-stu-id="15efc-125">**Monitor Docker applications in Application Insights:** \\</span></span>
  <https://docs.microsoft.com/azure/application-insights/app-insights-docker>

- <span data-ttu-id="15efc-126">**Aplikace Insights Docker image v Docker Hubu a Githubu:** \\</span><span class="sxs-lookup"><span data-stu-id="15efc-126">**Application Insights Docker image at Docker Hub and GitHub:** \\</span></span>
  <span data-ttu-id="15efc-127"><https://hub.docker.com/r/microsoft/applicationinsights/> a \\</span><span class="sxs-lookup"><span data-stu-id="15efc-127"><https://hub.docker.com/r/microsoft/applicationinsights/> and \\</span></span>
  <https://github.com/Microsoft/ApplicationInsights-Docker>

- <span data-ttu-id="15efc-128">**Nastavení Application Insights pro webové aplikace ASP.NET a ASP.NET Core:** \\</span><span class="sxs-lookup"><span data-stu-id="15efc-128">**Set up Application Insights for ASP.NET web apps and ASP.NET Core:** \\</span></span>
  <https://docs.microsoft.com/azure/application-insights/app-insights-asp-net>

- <span data-ttu-id="15efc-129">**Application Insights pro webové stránky:**</span><span class="sxs-lookup"><span data-stu-id="15efc-129">**Application Insights for web pages:**</span></span>  
  <https://docs.microsoft.com/azure/application-insights/app-insights-javascript>

## <a name="security-backup-and-monitoring-services"></a><span data-ttu-id="15efc-130">Zabezpečení, zálohování a monitorování služeb</span><span class="sxs-lookup"><span data-stu-id="15efc-130">Security, backup, and monitoring services</span></span>

<span data-ttu-id="15efc-131">Existuje mnoho podporu vás ujmeme rutinních úkolů s velkým množstvím podrobnosti, které je potřeba zpracovat zajistit, že vaše aplikace a infrastrukturu jsou v podmínce nejvyšší stupeň pro podporu obchodních potřeb a situace však začíná komplikovat více ve sféře, mikroslužby, takže potřebujete způsob, jak Pokud potřebujete provést akci, mají vysoké úrovně a podrobné zobrazení.</span><span class="sxs-lookup"><span data-stu-id="15efc-131">There are many support chores with lots of details that you have to handle to ensure your applications and infrastructure are in top notch condition to support business needs, and the situation becomes more complicated in the microservices realm, so you need a way to have both high-level and detailed views when you need to take action.</span></span>

<span data-ttu-id="15efc-132">Azure nabízí nástroje pro správu a poskytují jednotný přehled o čtyři důležité aspekty cloudových a místních prostředků:</span><span class="sxs-lookup"><span data-stu-id="15efc-132">Azure has the tools to manage and provide a unified view of four critical aspects of both your cloud and on-premises resources:</span></span>

- <span data-ttu-id="15efc-133">**Zabezpečení.**</span><span class="sxs-lookup"><span data-stu-id="15efc-133">**Security**.</span></span> <span data-ttu-id="15efc-134">S [Azure Security Center](https://azure.microsoft.com/services/security-center/).</span><span class="sxs-lookup"><span data-stu-id="15efc-134">With [Azure Security Center](https://azure.microsoft.com/services/security-center/).</span></span>
  - <span data-ttu-id="15efc-135">Získejte kompletní přehled a kontrolu nad zabezpečením všech vašich virtuálních počítačů, aplikací a úloh.</span><span class="sxs-lookup"><span data-stu-id="15efc-135">Get full visibility and control over the security of your virtual machines, apps, and workloads.</span></span>
  - <span data-ttu-id="15efc-136">Centralizujte si správu zásad zabezpečení a integraci stávajících procesů a nástrojů.</span><span class="sxs-lookup"><span data-stu-id="15efc-136">Centralize the management of your security policies and integrate existing processes and tools.</span></span>
  - <span data-ttu-id="15efc-137">Detekujte reálné hrozby pomocí pokročilých analýz.</span><span class="sxs-lookup"><span data-stu-id="15efc-137">Detect real threats with advanced analytics.</span></span>

- <span data-ttu-id="15efc-138">**Zálohování**.</span><span class="sxs-lookup"><span data-stu-id="15efc-138">**Backup**.</span></span> <span data-ttu-id="15efc-139">S [Azure Backup](https://azure.microsoft.com/services/backup/).</span><span class="sxs-lookup"><span data-stu-id="15efc-139">With [Azure Backup](https://azure.microsoft.com/services/backup/).</span></span>
  - <span data-ttu-id="15efc-140">Vyhnout se nákladnému přerušení služeb, splnit cíle dodržování předpisů a chránit vaše data před ransomwarem a lidskou chybou.</span><span class="sxs-lookup"><span data-stu-id="15efc-140">Avoid costly business disruptions, meet compliance goals, and protect your data against ransomware and human errors.</span></span>
  - <span data-ttu-id="15efc-141">Zachovejte si svá záložní data přenášená i v klidovém stavu zašifrovaná.</span><span class="sxs-lookup"><span data-stu-id="15efc-141">Keep your backup data encrypted in transit and at rest.</span></span>
  - <span data-ttu-id="15efc-142">Zajištění přístupu na základě vícefaktorového ověřování, abyste zabránili neoprávněnému používání.</span><span class="sxs-lookup"><span data-stu-id="15efc-142">Ensure access based on multifactor authentication to prevent unauthorized use.</span></span>

- <span data-ttu-id="15efc-143">**Monitorování**.</span><span class="sxs-lookup"><span data-stu-id="15efc-143">**Monitoring**.</span></span> <span data-ttu-id="15efc-144">S [monitorování Azure](https://azure.microsoft.com/solutions/monitoring/), [Log Analytics](https://azure.microsoft.com/services/log-analytics/), a [Application Insights](https://azure.microsoft.com/services/application-insights/).</span><span class="sxs-lookup"><span data-stu-id="15efc-144">With [Azure monitoring](https://azure.microsoft.com/solutions/monitoring/), [Log Analytics](https://azure.microsoft.com/services/log-analytics/), and [Application Insights](https://azure.microsoft.com/services/application-insights/).</span></span>
  - <span data-ttu-id="15efc-145">Umožňuje získáte úplný přehled o stavu a výkonu vašich úloh v Azure, aplikací a infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="15efc-145">Get full visibility into the health and performance of your Azure workloads, apps, and infrastructure.</span></span>
  - <span data-ttu-id="15efc-146">Shromažďování dat z libovolného zdroje a získat detailní přehled o vašich virtuálních počítačů, kontejnery a aplikace.</span><span class="sxs-lookup"><span data-stu-id="15efc-146">Collect data from any source and get rich insights into your virtual machines, containers, and applications.</span></span>
  - <span data-ttu-id="15efc-147">Najdete informace, které potřebujete, pomocí interaktivních dotazů a fulltextového vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="15efc-147">Find the information you need using interactive queries and full-text search.</span></span> 
  - <span data-ttu-id="15efc-148">Proveďte analýzu hlavní příčiny pomocí pokročilých analýz, včetně algoritmů strojového učení.</span><span class="sxs-lookup"><span data-stu-id="15efc-148">Perform root-cause analysis with advanced analytics, including machine learning algorithms.</span></span>

- <span data-ttu-id="15efc-149">**Místní prostředky**.</span><span class="sxs-lookup"><span data-stu-id="15efc-149">**On-premises resources**.</span></span> <span data-ttu-id="15efc-150">S [skutečně konsistentní hybridní cloud](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).</span><span class="sxs-lookup"><span data-stu-id="15efc-150">With [a truly consistent hybrid cloud](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="15efc-151">[Předchozí](manage-production-docker-environments.md)
>[další](../key-takeaways/index.md)</span><span class="sxs-lookup"><span data-stu-id="15efc-151">[Previous](manage-production-docker-environments.md)
[Next](../key-takeaways/index.md)</span></span>
