---
title: Monitorování kontejnerizovaných aplikačních služeb
description: Seznamte se s klíčovými aspekty monitorování architektur kontejnerů
ms.date: 02/15/2019
ms.openlocfilehash: e41df53ad94784436442c3cf7defed3fab510455
ms.sourcegitcommit: e7748001b1cee80ced691d8a76ca814c0b02dd9b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2020
ms.locfileid: "86374439"
---
# <a name="monitor-containerized-application-services"></a><span data-ttu-id="c6885-103">Monitorování kontejnerizovaných aplikačních služeb</span><span class="sxs-lookup"><span data-stu-id="c6885-103">Monitor containerized application services</span></span>

<span data-ttu-id="c6885-104">Je důležité pro aplikace rozdělené do několika kontejnerů a mikroslužeb, aby měly možnost monitorovat a analyzovat chování celé aplikace.</span><span class="sxs-lookup"><span data-stu-id="c6885-104">It's critical for applications split into multiple containers and microservices to have a way to monitor and analyze the behavior of the whole application.</span></span>

## <a name="azure-monitor"></a><span data-ttu-id="c6885-105">Azure Monitor</span><span class="sxs-lookup"><span data-stu-id="c6885-105">Azure Monitor</span></span>

<span data-ttu-id="c6885-106">[Azure monitor](https://azure.microsoft.com/services/monitor/) je rozšiřitelná analytická služba, která monitoruje vaši živou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c6885-106">[Azure Monitor](https://azure.microsoft.com/services/monitor/) is an extensible analytics service that monitors your live application.</span></span> <span data-ttu-id="c6885-107">Pomáhá detekovat a diagnostikovat problémy s výkonem a pochopit, co uživatelé s vaší aplikací skutečně dělají.</span><span class="sxs-lookup"><span data-stu-id="c6885-107">It helps you to detect and diagnose performance issues and to understand what users actually do with your app.</span></span> <span data-ttu-id="c6885-108">Je navržená pro vývojáře s cílem pomoci při neustálém vylepšování výkonu a použitelnosti služeb nebo aplikací.</span><span class="sxs-lookup"><span data-stu-id="c6885-108">It's designed for developers, with the intent of helping you to continuously improve the performance and usability of your services or applications.</span></span> <span data-ttu-id="c6885-109">Azure Monitor spolupracuje s webovými i službami a samostatnými aplikacemi na nejrůznějších platformách, jako je .NET, Java, Node.js a spousta dalších platforem, které jsou hostované místně nebo v cloudu.</span><span class="sxs-lookup"><span data-stu-id="c6885-109">Azure Monitor works with both web/services and standalone apps on a wide variety of platforms like .NET, Java, Node.js and many other platforms, hosted on-premises or in the cloud.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c6885-110">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="c6885-110">Additional resources</span></span>

- <span data-ttu-id="c6885-111">**Přehled Azure Monitor** </span><span class="sxs-lookup"><span data-stu-id="c6885-111">**Overview of Azure Monitor** </span></span>\
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="c6885-112">**Co je Application Insights?**</span><span class="sxs-lookup"><span data-stu-id="c6885-112">**What is Application Insights?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- <span data-ttu-id="c6885-113">**Co je Azure Monitor metriky?**</span><span class="sxs-lookup"><span data-stu-id="c6885-113">**What is Azure Monitor Metrics?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- <span data-ttu-id="c6885-114">**Řešení pro monitorování kontejnerů v Azure Monitor** </span><span class="sxs-lookup"><span data-stu-id="c6885-114">**Container Monitoring solution in Azure Monitor** </span></span>\
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a><span data-ttu-id="c6885-115">Služby zabezpečení a zálohování</span><span class="sxs-lookup"><span data-stu-id="c6885-115">Security and backup services</span></span>

<span data-ttu-id="c6885-116">Existuje mnoho rutinní podpory s mnoha podrobnostmi, které je třeba zvládnout, abyste zajistili, že vaše aplikace a infrastruktura jsou ve stavu nejvyšší úrovně, aby podporovaly obchodní potřeby, a situace se ve sféře mikroslužeb bude složitá, takže potřebujete způsob, jak mít jak zobrazení vysoké úrovně, tak podrobné zobrazení, pokud potřebujete provést akci.</span><span class="sxs-lookup"><span data-stu-id="c6885-116">There are many support chores with lots of details that you have to handle to ensure your applications and infrastructure are in top notch condition to support business needs, and the situation becomes more complicated in the microservices realm, so you need a way to have both high-level and detailed views when you need to take action.</span></span>

<span data-ttu-id="c6885-117">Azure má nástroje pro správu a nabízí jednotný přehled čtyř důležitých aspektů cloudových i místních prostředků:</span><span class="sxs-lookup"><span data-stu-id="c6885-117">Azure has the tools to manage and provide a unified view of four critical aspects of both your cloud and on-premises resources:</span></span>

- <span data-ttu-id="c6885-118">**Zabezpečení**.</span><span class="sxs-lookup"><span data-stu-id="c6885-118">**Security**.</span></span> <span data-ttu-id="c6885-119">S [Azure Security Center](https://azure.microsoft.com/services/security-center/).</span><span class="sxs-lookup"><span data-stu-id="c6885-119">With [Azure Security Center](https://azure.microsoft.com/services/security-center/).</span></span>
  - <span data-ttu-id="c6885-120">Získejte úplnou viditelnost a kontrolu nad zabezpečením vašich virtuálních počítačů, aplikací a úloh.</span><span class="sxs-lookup"><span data-stu-id="c6885-120">Get full visibility and control over the security of your virtual machines, apps, and workloads.</span></span>
  - <span data-ttu-id="c6885-121">Soustřeďte správu zásad zabezpečení a integrujte stávající procesy a nástroje.</span><span class="sxs-lookup"><span data-stu-id="c6885-121">Centralize the management of your security policies and integrate existing processes and tools.</span></span>
  - <span data-ttu-id="c6885-122">Detekuje reálné hrozby pomocí pokročilých analýz.</span><span class="sxs-lookup"><span data-stu-id="c6885-122">Detect real threats with advanced analytics.</span></span>

- <span data-ttu-id="c6885-123">**Zálohování**.</span><span class="sxs-lookup"><span data-stu-id="c6885-123">**Backup**.</span></span> <span data-ttu-id="c6885-124">S [Azure Backup](https://azure.microsoft.com/services/backup/).</span><span class="sxs-lookup"><span data-stu-id="c6885-124">With [Azure Backup](https://azure.microsoft.com/services/backup/).</span></span>
  - <span data-ttu-id="c6885-125">Vyhněte se nákladným výpadkům podniku, doplněním cílů dodržování předpisů a ochraně vašich dat před ransomwarem a lidskou chybou.</span><span class="sxs-lookup"><span data-stu-id="c6885-125">Avoid costly business disruptions, meet compliance goals, and protect your data against ransomware and human errors.</span></span>
  - <span data-ttu-id="c6885-126">Zajistěte, aby byla zálohovaná data šifrovaná při přenosu a v klidovém stavu.</span><span class="sxs-lookup"><span data-stu-id="c6885-126">Keep your backup data encrypted in transit and at rest.</span></span>
  - <span data-ttu-id="c6885-127">Zajistěte přístup na základě vícefaktorového ověřování, abyste zabránili neoprávněnému použití.</span><span class="sxs-lookup"><span data-stu-id="c6885-127">Ensure access based on multifactor authentication to prevent unauthorized use.</span></span>

- <span data-ttu-id="c6885-128">**Místní prostředky**.</span><span class="sxs-lookup"><span data-stu-id="c6885-128">**On-premises resources**.</span></span> <span data-ttu-id="c6885-129">Pomocí [hybridních cloudových řešení](https://azure.microsoft.com/solutions/hybrid-cloud-app/).</span><span class="sxs-lookup"><span data-stu-id="c6885-129">With [hybrid cloud solutions](https://azure.microsoft.com/solutions/hybrid-cloud-app/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c6885-130">[Předchozí](manage-production-docker-environments.md) 
> [Další](../key-takeaways/index.md)</span><span class="sxs-lookup"><span data-stu-id="c6885-130">[Previous](manage-production-docker-environments.md)
[Next](../key-takeaways/index.md)</span></span>
