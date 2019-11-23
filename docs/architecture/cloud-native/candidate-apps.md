---
title: Kandidátské aplikace pro cloudové nativní
description: Seznamte se s typy aplikací, které využívají nativní přístup z cloudu.
author: robvet
ms.date: 08/20/2019
ms.openlocfilehash: 328af4081d830cf1a7959a37c2155090ec4da3ff
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968299"
---
# <a name="candidate-apps-for-cloud-native"></a><span data-ttu-id="1ae98-103">Kandidátské aplikace pro cloudové nativní</span><span class="sxs-lookup"><span data-stu-id="1ae98-103">Candidate apps for cloud native</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="1ae98-104">Podívejte se na aplikace v portfoliu.</span><span class="sxs-lookup"><span data-stu-id="1ae98-104">Look at the apps in your portfolio.</span></span> <span data-ttu-id="1ae98-105">Kolik z nich splňuje podmínky pro nativní cloudovou architekturu?</span><span class="sxs-lookup"><span data-stu-id="1ae98-105">How many of them qualify for a cloud-native architecture?</span></span> <span data-ttu-id="1ae98-106">Všechny?</span><span class="sxs-lookup"><span data-stu-id="1ae98-106">All of them?</span></span> <span data-ttu-id="1ae98-107">Možná nějaké?</span><span class="sxs-lookup"><span data-stu-id="1ae98-107">Perhaps some?</span></span>

<span data-ttu-id="1ae98-108">Když použijete analýzu nákladů a přínosů, je velmi pravděpodobné, že nebudete mít k dispozici Hefty cenové značky, která se vyžaduje pro cloudovou nativní podporu.</span><span class="sxs-lookup"><span data-stu-id="1ae98-108">Applying a cost/benefit analysis, there's a good chance that most wouldn't support the hefty price tag required to be cloud native.</span></span> <span data-ttu-id="1ae98-109">Náklady na cloudový Native by daleko překročily obchodní hodnotu aplikace.</span><span class="sxs-lookup"><span data-stu-id="1ae98-109">The cost of being cloud native would far exceed the business value of the application.</span></span>

<span data-ttu-id="1ae98-110">Jaký typ aplikace může být kandidátem na nativní Cloud?</span><span class="sxs-lookup"><span data-stu-id="1ae98-110">What type of application might be a candidate for cloud native?</span></span>

- <span data-ttu-id="1ae98-111">Velký strategický podnikový systém, který potřebuje neustále vyvíjet obchodní možnosti/funkce</span><span class="sxs-lookup"><span data-stu-id="1ae98-111">A large, strategic enterprise system that needs to constantly evolve business capabilities/features</span></span>

- <span data-ttu-id="1ae98-112">Aplikace, která vyžaduje vysokou rychlost vydání verze – s vysokou jistotou</span><span class="sxs-lookup"><span data-stu-id="1ae98-112">An application that requires a high release velocity - with high confidence</span></span>

- <span data-ttu-id="1ae98-113">Systém, ve kterém musí jednotlivé funkce vydávat *bez* úplného opětovného nasazení celého systému</span><span class="sxs-lookup"><span data-stu-id="1ae98-113">A system with where individual features must release *without* a full redeployment of the entire system</span></span>

- <span data-ttu-id="1ae98-114">Aplikace vyvinutá týmy s odbornými znalostmi různých technologických zásobníků</span><span class="sxs-lookup"><span data-stu-id="1ae98-114">An application developed by teams with expertise in different technology stacks</span></span>

- <span data-ttu-id="1ae98-115">Aplikace s komponentami, které se musí nezávisle škálovat</span><span class="sxs-lookup"><span data-stu-id="1ae98-115">An application with components that must scale independently</span></span>

<span data-ttu-id="1ae98-116">Pak jsou starší verze systémů.</span><span class="sxs-lookup"><span data-stu-id="1ae98-116">Then there are legacy systems.</span></span> <span data-ttu-id="1ae98-117">I když bychom chtěli vytvářet nové aplikace, často zodpovídáme za modernizaci starší verze úloh, které jsou pro firmu zásadní.</span><span class="sxs-lookup"><span data-stu-id="1ae98-117">While we'd all like to build new applications, we're often responsible for modernizing legacy workloads that are critical to the business.</span></span> <span data-ttu-id="1ae98-118">V průběhu času může být starší verze aplikace rozdělená do mikroslužeb, kontejnerů a nakonec "navýšení" na nativní cloudovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="1ae98-118">Over time, a legacy application could be decomposed into microservices, containerized, and ultimately "replatformed" into a cloud-native architecture.</span></span>

### <a name="modernizing-legacy-apps"></a><span data-ttu-id="1ae98-119">Modernizaci starší verze aplikací</span><span class="sxs-lookup"><span data-stu-id="1ae98-119">Modernizing legacy apps</span></span>

<span data-ttu-id="1ae98-120">Bezplatná elektronická kniha Microsoftu [modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) poskytuje pokyny pro migraci místních úloh do cloudu.</span><span class="sxs-lookup"><span data-stu-id="1ae98-120">The free Microsoft e-book [Modernize existing .NET applications with Azure cloud and Windows Containers](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) provides guidance for migrating on-premises workloads into cloud.</span></span> <span data-ttu-id="1ae98-121">Obrázek 1-10 ukazuje, že pro modernizaci starší verze aplikací není k dispozici jedna strategie pro všechny velikosti.</span><span class="sxs-lookup"><span data-stu-id="1ae98-121">Figure 1-10 shows that there isn't a single, one-size-fits-all strategy for modernizing legacy applications.</span></span>

![Strategie migrace starších verzí úloh](./media/strategies-for-migrating-legacy-workloads.png)

<span data-ttu-id="1ae98-123">**Obrázek 1-10**.</span><span class="sxs-lookup"><span data-stu-id="1ae98-123">**Figure 1-10**.</span></span> <span data-ttu-id="1ae98-124">Strategie migrace starších verzí úloh</span><span class="sxs-lookup"><span data-stu-id="1ae98-124">Strategies for migrating legacy workloads</span></span>

<span data-ttu-id="1ae98-125">Monolitické aplikace, které jsou nepostradatelné, přináší z provozu rychlou migraci ([připravenou pro cloudovou infrastrukturu](https://docs.microsoft.com/dotnet/standard/modernize-with-azure-and-containers/lift-and-shift-existing-apps-azure-iaas)).</span><span class="sxs-lookup"><span data-stu-id="1ae98-125">Monolithic apps that are non-critical largely benefit from a quick lift-and-shift ([Cloud Infrastructure-Ready](https://docs.microsoft.com/dotnet/standard/modernize-with-azure-and-containers/lift-and-shift-existing-apps-azure-iaas)) migration.</span></span> <span data-ttu-id="1ae98-126">V tomto případě se místní úloha znovu hostuje na cloudový virtuální počítač beze změn.</span><span class="sxs-lookup"><span data-stu-id="1ae98-126">Here, the on-premises workload is rehosted to a cloud-based VM, without changes.</span></span> <span data-ttu-id="1ae98-127">Tento přístup používá [model IaaS (infrastruktura jako služba)](https://azure.microsoft.com/overview/what-is-iaas/).</span><span class="sxs-lookup"><span data-stu-id="1ae98-127">This approach uses the [IaaS (Infrastructure as a Service) model](https://azure.microsoft.com/overview/what-is-iaas/).</span></span> <span data-ttu-id="1ae98-128">Azure obsahuje několik nástrojů, jako je například ([Azure Migrate](https://aka.ms/azuremigrate), [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)a [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/)), aby bylo možné tento přesun usnadnit.</span><span class="sxs-lookup"><span data-stu-id="1ae98-128">Azure includes several tools such as ([Azure Migrate](https://aka.ms/azuremigrate), [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/), and [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/)) to make such a move easier.</span></span> <span data-ttu-id="1ae98-129">I když tato strategie může přinést určitou úsporu nákladů, takové aplikace se většinou nemusely rozdávat a využívat výhody cloud computingu.</span><span class="sxs-lookup"><span data-stu-id="1ae98-129">While this strategy can yield some cost savings, such applications typically weren't architected to unlock and leverage the benefits of cloud computing.</span></span>

<span data-ttu-id="1ae98-130">Monolitické aplikace, které jsou důležité pro obchodní často, využívají výhod vylepšené migrace za provozu a posunutí (*optimalizované pro Cloud*).</span><span class="sxs-lookup"><span data-stu-id="1ae98-130">Monolithic apps that are critical to the business oftentimes benefit from an enhanced lift-and-shift (*Cloud Optimized*) migration.</span></span> <span data-ttu-id="1ae98-131">Tento přístup zahrnuje optimalizace nasazení, které umožňují klíčovou službu Cloud Services – bez změny základní architektury aplikace.</span><span class="sxs-lookup"><span data-stu-id="1ae98-131">This approach includes deployment optimizations that enable key cloud services - without changing the core architecture of the application.</span></span> <span data-ttu-id="1ae98-132">Například můžete aplikaci [kontejnerizace](https://docs.microsoft.com/virtualization/windowscontainers/about/) a nasadit ji na produkt Orchestrator, jako je třeba [Služba Azure Kubernetes](https://azure.microsoft.com/services/kubernetes-service/), která je popsána dále v této příručce.</span><span class="sxs-lookup"><span data-stu-id="1ae98-132">For example, you might [containerize](https://docs.microsoft.com/virtualization/windowscontainers/about/) the application and deploy it to a container orchestrator, like [Azure Kubernetes Services](https://azure.microsoft.com/services/kubernetes-service/), discussed later in this book.</span></span> <span data-ttu-id="1ae98-133">V cloudu může aplikace využívat jiné cloudové služby, jako jsou databáze, fronty zpráv, monitorování a distribuované ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="1ae98-133">Once in the cloud, the application could consume other cloud services such as databases, message queues, monitoring, and distributed caching.</span></span>

<span data-ttu-id="1ae98-134">Aplikace monolitické, které provádějí strategické podnikové funkce, můžou nejlépe těžit z *cloudového nativního* přístupu, který je předmětem této knihy.</span><span class="sxs-lookup"><span data-stu-id="1ae98-134">Finally, monolithic apps that perform strategic enterprise functions might best benefit from a *Cloud-Native* approach, the subject of this book.</span></span> <span data-ttu-id="1ae98-135">Tento přístup poskytuje flexibilitu a rychlost.</span><span class="sxs-lookup"><span data-stu-id="1ae98-135">This approach provides agility and velocity.</span></span> <span data-ttu-id="1ae98-136">Ale přináší náklady na replatformování, rearchitekturu a přepis kódu.</span><span class="sxs-lookup"><span data-stu-id="1ae98-136">But, it comes at a cost of replatforming, rearchitecting, and rewriting code.</span></span>

<span data-ttu-id="1ae98-137">Pokud se vy a váš tým domníváte, že se jedná o cloudový nativní přístup, je vhodné, abyste s vaší organizací behooves racionalizovat rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="1ae98-137">If you and your team believe a cloud-native approach is appropriate, it behooves you to rationalize the decision with your organization.</span></span> <span data-ttu-id="1ae98-138">Jak přesně se jedná o obchodní problém, který vyřeší cloudový nativní přístup?</span><span class="sxs-lookup"><span data-stu-id="1ae98-138">What exactly is the business problem that a cloud-native approach will solve?</span></span> <span data-ttu-id="1ae98-139">Jak by to bylo v souladu s podnikovými požadavky?</span><span class="sxs-lookup"><span data-stu-id="1ae98-139">How would it align with business needs?</span></span>

- <span data-ttu-id="1ae98-140">Rychlé verze funkcí s větší jistotou?</span><span class="sxs-lookup"><span data-stu-id="1ae98-140">Rapid releases of features with increased confidence?</span></span>

- <span data-ttu-id="1ae98-141">Jemně odstupňovaná škálovatelnost – efektivnější využití prostředků?</span><span class="sxs-lookup"><span data-stu-id="1ae98-141">Fine-grained scalability - more efficient usage of resources?</span></span>

- <span data-ttu-id="1ae98-142">Zlepšila se odolnost systému?</span><span class="sxs-lookup"><span data-stu-id="1ae98-142">Improved system resiliency?</span></span>

- <span data-ttu-id="1ae98-143">Vylepšený výkon systému?</span><span class="sxs-lookup"><span data-stu-id="1ae98-143">Improved system performance?</span></span>

- <span data-ttu-id="1ae98-144">Máte lepší přehled o operacích?</span><span class="sxs-lookup"><span data-stu-id="1ae98-144">More visibility into operations?</span></span>

- <span data-ttu-id="1ae98-145">Vývojové platformy a úložiště dat pro vývoj v Blendu k dosažení nejlepšího nástroje pro úlohu?</span><span class="sxs-lookup"><span data-stu-id="1ae98-145">Blend development platforms and data stores to arrive at the best tool for the job?</span></span>

- <span data-ttu-id="1ae98-146">Budoucí investice do aplikace pro kontrolu pravopisu?</span><span class="sxs-lookup"><span data-stu-id="1ae98-146">Future-proof application investment?</span></span>

<span data-ttu-id="1ae98-147">Správná strategie migrace závisí na prioritách organizace a na systémech, které cílíte.</span><span class="sxs-lookup"><span data-stu-id="1ae98-147">The right migration strategy depends on organizational priorities and the systems you're targeting.</span></span> <span data-ttu-id="1ae98-148">V mnoha případech může být výhodnější zvýšit náklady na Cloud – optimalizuje aplikaci monolitické nebo do N-vrstvé aplikace přidat hrubě odstupňované služby.</span><span class="sxs-lookup"><span data-stu-id="1ae98-148">For many, it may be more cost effective to cloud-optimize a monolithic application or add coarse-grained services to an N-Tier app.</span></span> <span data-ttu-id="1ae98-149">V těchto případech můžete plně využívat možnosti cloudového PaaSu, jako jsou ty, které nabízí Azure App Service.</span><span class="sxs-lookup"><span data-stu-id="1ae98-149">In these cases, you can still make full use of cloud PaaS capabilities like the ones offered by Azure App Service.</span></span>

## <a name="summary"></a><span data-ttu-id="1ae98-150">Souhrn</span><span class="sxs-lookup"><span data-stu-id="1ae98-150">Summary</span></span>

<span data-ttu-id="1ae98-151">V této kapitole jsme představili výpočetní prostředí pro Cloud.</span><span class="sxs-lookup"><span data-stu-id="1ae98-151">In this chapter, we introduced cloud-native computing.</span></span> <span data-ttu-id="1ae98-152">Poskytli jsme definici společně s klíčovými možnostmi, které zajišťují cloudovou nativní aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1ae98-152">We provided a definition along with the key capabilities that drive a cloud-native application.</span></span> <span data-ttu-id="1ae98-153">Prohlédli jsme se na typech aplikací, které by mohly tuto investici a úsilí zdůvodnit.</span><span class="sxs-lookup"><span data-stu-id="1ae98-153">We looked at the types of applications that might justify this investment and effort.</span></span>

<span data-ttu-id="1ae98-154">V úvodu na pozadí jsme teď podrobněi mnohem podrobnější pohled na Cloud Native.</span><span class="sxs-lookup"><span data-stu-id="1ae98-154">With the introduction behind, we now dive into a much more detailed look at cloud native.</span></span>

### <a name="references"></a><span data-ttu-id="1ae98-155">Reference</span><span class="sxs-lookup"><span data-stu-id="1ae98-155">References</span></span>

- [<span data-ttu-id="1ae98-156">Cloud Native Computing Foundation</span><span class="sxs-lookup"><span data-stu-id="1ae98-156">Cloud Native Computing Foundation</span></span>](https://www.cncf.io/)

- [<span data-ttu-id="1ae98-157">Mikroslužby .NET: architektura pro kontejnerové aplikace .NET</span><span class="sxs-lookup"><span data-stu-id="1ae98-157">.NET Microservices: Architecture for Containerized .NET applications</span></span>](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [<span data-ttu-id="1ae98-158">Modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows</span><span class="sxs-lookup"><span data-stu-id="1ae98-158">Modernize existing .NET applications with Azure cloud and Windows Containers</span></span>](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)

- [<span data-ttu-id="1ae98-159">Nativní vzory cloudu podle Cornelia Davis</span><span class="sxs-lookup"><span data-stu-id="1ae98-159">Cloud Native Patterns by Cornelia Davis</span></span>](https://www.manning.com/books/cloud-native-patterns)

- [<span data-ttu-id="1ae98-160">Mimo aplikaci dvanáct-Factor</span><span class="sxs-lookup"><span data-stu-id="1ae98-160">Beyond the Twelve-Factor Application</span></span>](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)

- [<span data-ttu-id="1ae98-161">Co je infrastruktura jako kód</span><span class="sxs-lookup"><span data-stu-id="1ae98-161">What is Infrastructure as Code</span></span>](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)

- [<span data-ttu-id="1ae98-162">Micro Deploys v Uber Engineering: každodenní nasazení s jistotou</span><span class="sxs-lookup"><span data-stu-id="1ae98-162">Uber Engineering’s Micro Deploy: Deploying Daily with Confidence</span></span>](https://eng.uber.com/micro-deploy/)

- [<span data-ttu-id="1ae98-163">Jak Netflix nasazuje kód</span><span class="sxs-lookup"><span data-stu-id="1ae98-163">How Netflix Deploys Code</span></span>](https://www.infoq.com/news/2013/06/netflix/)

- [<span data-ttu-id="1ae98-164">Přetížení ovládacího prvku pro škálování mikroslužeb WeChat</span><span class="sxs-lookup"><span data-stu-id="1ae98-164">Overload Control for Scaling WeChat Microservices</span></span>](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf)

>[!div class="step-by-step"]
><span data-ttu-id="1ae98-165">[Předchozí](definition.md)
>[Další](introduce-eshoponcontainers-reference-app.md)</span><span class="sxs-lookup"><span data-stu-id="1ae98-165">[Previous](definition.md)
[Next](introduce-eshoponcontainers-reference-app.md)</span></span>
