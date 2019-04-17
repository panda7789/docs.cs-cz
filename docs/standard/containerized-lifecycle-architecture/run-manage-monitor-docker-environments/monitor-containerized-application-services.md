---
title: Monitorování kontejnerizovaných aplikačních služeb
description: Přečtěte si některé klíčové aspekty monitorování kontejneru architektury
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 4553a35c8db6cfc46187525ef2ffc65cb3ba07c9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2019
ms.locfileid: "59672045"
---
# <a name="monitor-containerized-application-services"></a><span data-ttu-id="cbe86-103">Monitorování kontejnerizovaných aplikačních služeb</span><span class="sxs-lookup"><span data-stu-id="cbe86-103">Monitor containerized application services</span></span>

<span data-ttu-id="cbe86-104">Je velmi důležité pro aplikace rozdělit do několika kontejnery a mikroslužby způsob, jak monitorovat a analyzovat chování celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cbe86-104">It's critical for applications split into multiple containers and microservices to have a way to monitor and analyze the behavior of the whole application.</span></span>

## <a name="azure-monitor"></a><span data-ttu-id="cbe86-105">Azure Monitor</span><span class="sxs-lookup"><span data-stu-id="cbe86-105">Azure Monitor</span></span>

<span data-ttu-id="cbe86-106">[Azure Monitor](https://azure.microsoft.com/services/monitor/) je rozšiřitelnou analytickou službu, která monitoruje vaše živé aplikace.</span><span class="sxs-lookup"><span data-stu-id="cbe86-106">[Azure Monitor](https://azure.microsoft.com/services/monitor/) is an extensible analytics service that monitors your live application.</span></span> <span data-ttu-id="cbe86-107">Pomáhá detekovat a diagnostikovat problémy s výkonem a pochopit, co uživatelé dělají s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="cbe86-107">It helps you to detect and diagnose performance issues and to understand what users actually do with your app.</span></span> <span data-ttu-id="cbe86-108">Je určená pro vývojáře se záměrem pomáhá průběžně zlepšit výkon a použitelnost služby nebo aplikace.</span><span class="sxs-lookup"><span data-stu-id="cbe86-108">It's designed for developers, with the intent of helping you to continuously improve the performance and usability of your services or applications.</span></span> <span data-ttu-id="cbe86-109">Azure Monitor spolupracuje s webovou nebo služeb Team Foundation a samostatné aplikace na různých platformách jako .NET, Java, Node.js a mnoho dalších platforem hostovaný místně nebo v cloudu.</span><span class="sxs-lookup"><span data-stu-id="cbe86-109">Azure Monitor works with both web/services and standalone apps on a wide variety of platforms like .NET, Java, Node.js and many other platforms, hosted on-premises or in the cloud.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="cbe86-110">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="cbe86-110">Additional resources</span></span>

- <span data-ttu-id="cbe86-111">**Přehled služby Azure Monitor** \\</span><span class="sxs-lookup"><span data-stu-id="cbe86-111">**Overview of Azure Monitor** \\</span></span>
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="cbe86-112">**Co je Application Insights?**</span><span class="sxs-lookup"><span data-stu-id="cbe86-112">**What is Application Insights?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- <span data-ttu-id="cbe86-113">**Co je monitorování metrik Azure?**</span><span class="sxs-lookup"><span data-stu-id="cbe86-113">**What is Azure Monitor Metrics?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- <span data-ttu-id="cbe86-114">**Řešení pro monitorování kontejnerů ve službě Azure Monitor** \\</span><span class="sxs-lookup"><span data-stu-id="cbe86-114">**Container Monitoring solution in Azure Monitor** \\</span></span>
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a><span data-ttu-id="cbe86-115">Zabezpečení a zálohování služby</span><span class="sxs-lookup"><span data-stu-id="cbe86-115">Security and backup services</span></span>

<span data-ttu-id="cbe86-116">Existuje mnoho podporu vás ujmeme rutinních úkolů s velkým množstvím podrobnosti, které je potřeba zpracovat zajistit, že vaše aplikace a infrastrukturu jsou v podmínce nejvyšší stupeň pro podporu obchodních potřeb a situace však začíná komplikovat více ve sféře, mikroslužby, takže potřebujete způsob, jak Pokud potřebujete provést akci, mají vysoké úrovně a podrobné zobrazení.</span><span class="sxs-lookup"><span data-stu-id="cbe86-116">There are many support chores with lots of details that you have to handle to ensure your applications and infrastructure are in top notch condition to support business needs, and the situation becomes more complicated in the microservices realm, so you need a way to have both high-level and detailed views when you need to take action.</span></span>

<span data-ttu-id="cbe86-117">Azure nabízí nástroje pro správu a poskytují jednotný přehled o čtyři důležité aspekty cloudových a místních prostředků:</span><span class="sxs-lookup"><span data-stu-id="cbe86-117">Azure has the tools to manage and provide a unified view of four critical aspects of both your cloud and on-premises resources:</span></span>

- <span data-ttu-id="cbe86-118">**Zabezpečení.**</span><span class="sxs-lookup"><span data-stu-id="cbe86-118">**Security**.</span></span> <span data-ttu-id="cbe86-119">S [Azure Security Center](https://azure.microsoft.com/services/security-center/).</span><span class="sxs-lookup"><span data-stu-id="cbe86-119">With [Azure Security Center](https://azure.microsoft.com/services/security-center/).</span></span>
  - <span data-ttu-id="cbe86-120">Získejte kompletní přehled a kontrolu nad zabezpečením všech vašich virtuálních počítačů, aplikací a úloh.</span><span class="sxs-lookup"><span data-stu-id="cbe86-120">Get full visibility and control over the security of your virtual machines, apps, and workloads.</span></span>
  - <span data-ttu-id="cbe86-121">Centralizujte si správu zásad zabezpečení a integraci stávajících procesů a nástrojů.</span><span class="sxs-lookup"><span data-stu-id="cbe86-121">Centralize the management of your security policies and integrate existing processes and tools.</span></span>
  - <span data-ttu-id="cbe86-122">Detekujte reálné hrozby pomocí pokročilých analýz.</span><span class="sxs-lookup"><span data-stu-id="cbe86-122">Detect real threats with advanced analytics.</span></span>

- <span data-ttu-id="cbe86-123">**Zálohování**.</span><span class="sxs-lookup"><span data-stu-id="cbe86-123">**Backup**.</span></span> <span data-ttu-id="cbe86-124">S [Azure Backup](https://azure.microsoft.com/services/backup/).</span><span class="sxs-lookup"><span data-stu-id="cbe86-124">With [Azure Backup](https://azure.microsoft.com/services/backup/).</span></span>
  - <span data-ttu-id="cbe86-125">Vyhnout se nákladnému přerušení služeb, splnit cíle dodržování předpisů a chránit vaše data před ransomwarem a lidskou chybou.</span><span class="sxs-lookup"><span data-stu-id="cbe86-125">Avoid costly business disruptions, meet compliance goals, and protect your data against ransomware and human errors.</span></span>
  - <span data-ttu-id="cbe86-126">Zachovejte si svá záložní data přenášená i v klidovém stavu zašifrovaná.</span><span class="sxs-lookup"><span data-stu-id="cbe86-126">Keep your backup data encrypted in transit and at rest.</span></span>
  - <span data-ttu-id="cbe86-127">Zajištění přístupu na základě vícefaktorového ověřování, abyste zabránili neoprávněnému používání.</span><span class="sxs-lookup"><span data-stu-id="cbe86-127">Ensure access based on multifactor authentication to prevent unauthorized use.</span></span>

- <span data-ttu-id="cbe86-128">**Místní prostředky**.</span><span class="sxs-lookup"><span data-stu-id="cbe86-128">**On-premises resources**.</span></span> <span data-ttu-id="cbe86-129">S [skutečně konsistentní hybridní cloud](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).</span><span class="sxs-lookup"><span data-stu-id="cbe86-129">With [a truly consistent hybrid cloud](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="cbe86-130">[Předchozí](manage-production-docker-environments.md)
>[další](../key-takeaways/index.md)</span><span class="sxs-lookup"><span data-stu-id="cbe86-130">[Previous](manage-production-docker-environments.md)
[Next](../key-takeaways/index.md)</span></span>
