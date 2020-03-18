---
title: Monitorování kontejnerizovaných aplikačních služeb
description: Seznamte se s některými klíčovými aspekty monitorování architektury kontejnerů
ms.date: 02/15/2019
ms.openlocfilehash: e14553d510751d8a75020a1b6beb9fd7bc29596e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295619"
---
# <a name="monitor-containerized-application-services"></a><span data-ttu-id="bc400-103">Monitorování kontejnerizovaných aplikačních služeb</span><span class="sxs-lookup"><span data-stu-id="bc400-103">Monitor containerized application services</span></span>

<span data-ttu-id="bc400-104">Je důležité pro aplikace rozdělené do více kontejnerů a mikroslužeb mít způsob, jak sledovat a analyzovat chování celé aplikace.</span><span class="sxs-lookup"><span data-stu-id="bc400-104">It's critical for applications split into multiple containers and microservices to have a way to monitor and analyze the behavior of the whole application.</span></span>

## <a name="azure-monitor"></a><span data-ttu-id="bc400-105">Azure Monitor</span><span class="sxs-lookup"><span data-stu-id="bc400-105">Azure Monitor</span></span>

<span data-ttu-id="bc400-106">[Azure Monitor](https://azure.microsoft.com/services/monitor/) je rozšiřitelná analytická služba, která monitoruje vaši živou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bc400-106">[Azure Monitor](https://azure.microsoft.com/services/monitor/) is an extensible analytics service that monitors your live application.</span></span> <span data-ttu-id="bc400-107">Pomáhá vám odhalit a diagnostikovat problémy s výkonem a pochopit, co uživatelé skutečně dělají s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="bc400-107">It helps you to detect and diagnose performance issues and to understand what users actually do with your app.</span></span> <span data-ttu-id="bc400-108">Je určen pro vývojáře s cílem pomoci vám neustále zlepšovat výkon a použitelnost vašich služeb nebo aplikací.</span><span class="sxs-lookup"><span data-stu-id="bc400-108">It's designed for developers, with the intent of helping you to continuously improve the performance and usability of your services or applications.</span></span> <span data-ttu-id="bc400-109">Azure Monitor funguje s webovými a samostatnými aplikacemi na široké škále platforem, jako jsou .NET, Java, Node.js a mnoho dalších platforem, hostované místně nebo v cloudu.</span><span class="sxs-lookup"><span data-stu-id="bc400-109">Azure Monitor works with both web/services and standalone apps on a wide variety of platforms like .NET, Java, Node.js and many other platforms, hosted on-premises or in the cloud.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="bc400-110">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="bc400-110">Additional resources</span></span>

- <span data-ttu-id="bc400-111">**Přehled Azure Monitoru** </span><span class="sxs-lookup"><span data-stu-id="bc400-111">**Overview of Azure Monitor** </span></span>\
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="bc400-112">**Co je Application Insights?**</span><span class="sxs-lookup"><span data-stu-id="bc400-112">**What is Application Insights?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- <span data-ttu-id="bc400-113">**Co je metriky Azure Monitor?**</span><span class="sxs-lookup"><span data-stu-id="bc400-113">**What is Azure Monitor Metrics?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- <span data-ttu-id="bc400-114">**Řešení monitorování kontejnerů ve službě Azure Monitor** </span><span class="sxs-lookup"><span data-stu-id="bc400-114">**Container Monitoring solution in Azure Monitor** </span></span>\
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a><span data-ttu-id="bc400-115">Zabezpečení a zálohování</span><span class="sxs-lookup"><span data-stu-id="bc400-115">Security and backup services</span></span>

<span data-ttu-id="bc400-116">Existuje mnoho podpůrných činností se spoustou detailů, které musíte zvládnout, abyste zajistili, že vaše aplikace a infrastruktura jsou v špičkovém stavu pro podporu obchodních potřeb a situace se stává složitější v oblasti mikroslužeb, takže potřebujete způsob, jak mají jak na vysoké úrovni, tak podrobné pohledy, když potřebujete jednat.</span><span class="sxs-lookup"><span data-stu-id="bc400-116">There are many support chores with lots of details that you have to handle to ensure your applications and infrastructure are in top notch condition to support business needs, and the situation becomes more complicated in the microservices realm, so you need a way to have both high-level and detailed views when you need to take action.</span></span>

<span data-ttu-id="bc400-117">Azure má nástroje pro správu a poskytování jednotného zobrazení čtyř důležitých aspektů cloudových i místních prostředků:</span><span class="sxs-lookup"><span data-stu-id="bc400-117">Azure has the tools to manage and provide a unified view of four critical aspects of both your cloud and on-premises resources:</span></span>

- <span data-ttu-id="bc400-118">**Bezpečnost**.</span><span class="sxs-lookup"><span data-stu-id="bc400-118">**Security**.</span></span> <span data-ttu-id="bc400-119">S [Azure Security Center](https://azure.microsoft.com/services/security-center/).</span><span class="sxs-lookup"><span data-stu-id="bc400-119">With [Azure Security Center](https://azure.microsoft.com/services/security-center/).</span></span>
  - <span data-ttu-id="bc400-120">Získejte plnou viditelnost a kontrolu nad zabezpečením vašich virtuálních počítačů, aplikací a úloh.</span><span class="sxs-lookup"><span data-stu-id="bc400-120">Get full visibility and control over the security of your virtual machines, apps, and workloads.</span></span>
  - <span data-ttu-id="bc400-121">Centralizujte správu svých zásad zabezpečení a integrujte stávající procesy a nástroje.</span><span class="sxs-lookup"><span data-stu-id="bc400-121">Centralize the management of your security policies and integrate existing processes and tools.</span></span>
  - <span data-ttu-id="bc400-122">Detekujte skutečné hrozby pomocí pokročilých analýz.</span><span class="sxs-lookup"><span data-stu-id="bc400-122">Detect real threats with advanced analytics.</span></span>

- <span data-ttu-id="bc400-123">**Zálohování**.</span><span class="sxs-lookup"><span data-stu-id="bc400-123">**Backup**.</span></span> <span data-ttu-id="bc400-124">S [Azure Backup](https://azure.microsoft.com/services/backup/).</span><span class="sxs-lookup"><span data-stu-id="bc400-124">With [Azure Backup](https://azure.microsoft.com/services/backup/).</span></span>
  - <span data-ttu-id="bc400-125">Vyhněte se nákladným narušením podnikání, splníte cíle dodržování předpisů a chraňte svá data před ransomwarem a lidskými chybami.</span><span class="sxs-lookup"><span data-stu-id="bc400-125">Avoid costly business disruptions, meet compliance goals, and protect your data against ransomware and human errors.</span></span>
  - <span data-ttu-id="bc400-126">Uchovávejte záložní data šifrovaná při přenosu a v klidovém stavu.</span><span class="sxs-lookup"><span data-stu-id="bc400-126">Keep your backup data encrypted in transit and at rest.</span></span>
  - <span data-ttu-id="bc400-127">Zajistěte přístup na základě vícefaktorového ověřování, abyste zabránili neoprávněnému použití.</span><span class="sxs-lookup"><span data-stu-id="bc400-127">Ensure access based on multifactor authentication to prevent unauthorized use.</span></span>

- <span data-ttu-id="bc400-128">**Místní prostředky**.</span><span class="sxs-lookup"><span data-stu-id="bc400-128">**On-premises resources**.</span></span> <span data-ttu-id="bc400-129">S [opravdu konzistentním hybridním cloudem](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).</span><span class="sxs-lookup"><span data-stu-id="bc400-129">With [a truly consistent hybrid cloud](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="bc400-130">[Předchozí](manage-production-docker-environments.md)
>[další](../key-takeaways/index.md)</span><span class="sxs-lookup"><span data-stu-id="bc400-130">[Previous](manage-production-docker-environments.md)
[Next](../key-takeaways/index.md)</span></span>
