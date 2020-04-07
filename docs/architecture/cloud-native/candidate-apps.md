---
title: Kandidátské aplikace pro nativní cloud
description: Zjistěte, které typy aplikací využívají přístup založený na cloudu
author: robvet
ms.date: 03/31/2020
ms.openlocfilehash: 8e58f5bd3aa0a4503ea73ab454e42e863eb0bb5d
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805613"
---
# <a name="candidate-apps-for-cloud-native"></a><span data-ttu-id="0a600-103">Kandidátské aplikace pro nativní cloud</span><span class="sxs-lookup"><span data-stu-id="0a600-103">Candidate apps for cloud native</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="0a600-104">Podívejte se na aplikace ve svém portfoliu.</span><span class="sxs-lookup"><span data-stu-id="0a600-104">Look at the apps in your portfolio.</span></span> <span data-ttu-id="0a600-105">Kolik z nich má nárok na architekturu nativní pro cloud?</span><span class="sxs-lookup"><span data-stu-id="0a600-105">How many of them qualify for a cloud-native architecture?</span></span> <span data-ttu-id="0a600-106">Všechny?</span><span class="sxs-lookup"><span data-stu-id="0a600-106">All of them?</span></span> <span data-ttu-id="0a600-107">Možná nějaké?</span><span class="sxs-lookup"><span data-stu-id="0a600-107">Perhaps some?</span></span>

<span data-ttu-id="0a600-108">Použití analýzy nákladů a přínosů je velká šance, že většina z nich nebude podporovat statnou cenovku, která musí být nativní v cloudu.</span><span class="sxs-lookup"><span data-stu-id="0a600-108">Applying a cost/benefit analysis, there's a good chance that most wouldn't support the hefty price tag required to be cloud native.</span></span> <span data-ttu-id="0a600-109">Náklady na cloud nativní by daleko překročit obchodní hodnotu aplikace.</span><span class="sxs-lookup"><span data-stu-id="0a600-109">The cost of being cloud native would far exceed the business value of the application.</span></span>

<span data-ttu-id="0a600-110">Jaký typ aplikace může být kandidátem pro nativní cloud?</span><span class="sxs-lookup"><span data-stu-id="0a600-110">What type of application might be a candidate for cloud native?</span></span>

- <span data-ttu-id="0a600-111">Velký, strategický podnikový systém, který potřebuje neustále vyvíjet obchodní schopnosti/ funkce</span><span class="sxs-lookup"><span data-stu-id="0a600-111">A large, strategic enterprise system that needs to constantly evolve business capabilities/features</span></span>

- <span data-ttu-id="0a600-112">Aplikace, která vyžaduje vysokou rychlost uvolňování – s vysokou jistotou</span><span class="sxs-lookup"><span data-stu-id="0a600-112">An application that requires a high release velocity - with high confidence</span></span>

- <span data-ttu-id="0a600-113">Systém, ve kterém se musí jednotlivé funkce uvolnit *bez* úplného přerozdělení celého systému</span><span class="sxs-lookup"><span data-stu-id="0a600-113">A system with where individual features must release *without* a full redeployment of the entire system</span></span>

- <span data-ttu-id="0a600-114">Aplikace vyvinutá týmy s odbornými znalostmi v různých technologických hromádkách</span><span class="sxs-lookup"><span data-stu-id="0a600-114">An application developed by teams with expertise in different technology stacks</span></span>

- <span data-ttu-id="0a600-115">Aplikace s komponentami, které musí škálovat nezávisle</span><span class="sxs-lookup"><span data-stu-id="0a600-115">An application with components that must scale independently</span></span>

<span data-ttu-id="0a600-116">Pak jsou tu starší systémy.</span><span class="sxs-lookup"><span data-stu-id="0a600-116">Then there are legacy systems.</span></span> <span data-ttu-id="0a600-117">I když bychom všichni chtěli vytvářet nové aplikace, jsme často zodpovědní za modernizaci starších úloh, které jsou pro firmu klíčové.</span><span class="sxs-lookup"><span data-stu-id="0a600-117">While we'd all like to build new applications, we're often responsible for modernizing legacy workloads that are critical to the business.</span></span> <span data-ttu-id="0a600-118">V průběhu času může být starší aplikace rozložena na mikroslužby, kontejnerizovaná a nakonec "replatformed" do architektury nativní pro cloud.</span><span class="sxs-lookup"><span data-stu-id="0a600-118">Over time, a legacy application could be decomposed into microservices, containerized, and ultimately "replatformed" into a cloud-native architecture.</span></span>

### <a name="modernizing-legacy-apps"></a><span data-ttu-id="0a600-119">Modernizace starších aplikací</span><span class="sxs-lookup"><span data-stu-id="0a600-119">Modernizing legacy apps</span></span>

<span data-ttu-id="0a600-120">Bezplatná e-kniha Microsoft [modernizuje stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) poskytuje pokyny pro migraci místních úloh do cloudu.</span><span class="sxs-lookup"><span data-stu-id="0a600-120">The free Microsoft e-book [Modernize existing .NET applications with Azure cloud and Windows Containers](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook) provides guidance for migrating on-premises workloads into cloud.</span></span> <span data-ttu-id="0a600-121">Obrázek 1-10 ukazuje, že neexistuje jediná, jedna velikost pro všechny strategie pro modernizaci starších aplikací.</span><span class="sxs-lookup"><span data-stu-id="0a600-121">Figure 1-10 shows that there isn't a single, one-size-fits-all strategy for modernizing legacy applications.</span></span>

![Strategie migrace starších úloh](./media/strategies-for-migrating-legacy-workloads.png)

<span data-ttu-id="0a600-123">**Obrázek 1-10**.</span><span class="sxs-lookup"><span data-stu-id="0a600-123">**Figure 1-10**.</span></span> <span data-ttu-id="0a600-124">Strategie migrace starších úloh</span><span class="sxs-lookup"><span data-stu-id="0a600-124">Strategies for migrating legacy workloads</span></span>

<span data-ttu-id="0a600-125">Monolitické aplikace, které nejsou kritické, z velké části těží z rychlé migrace výtahu a posunu[(Cloud Infrastructure-Ready).](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)</span><span class="sxs-lookup"><span data-stu-id="0a600-125">Monolithic apps that are non-critical largely benefit from a quick lift-and-shift ([Cloud Infrastructure-Ready](../modernize-with-azure-containers/lift-and-shift-existing-apps-azure-iaas.md)) migration.</span></span> <span data-ttu-id="0a600-126">Tady je místní úloha rehosted na virtuální počítač na základě cloudu, beze změn.</span><span class="sxs-lookup"><span data-stu-id="0a600-126">Here, the on-premises workload is rehosted to a cloud-based VM, without changes.</span></span> <span data-ttu-id="0a600-127">Tento přístup používá [model IaaS (Infrastruktura jako služba).](https://azure.microsoft.com/overview/what-is-iaas/)</span><span class="sxs-lookup"><span data-stu-id="0a600-127">This approach uses the [IaaS (Infrastructure as a Service) model](https://azure.microsoft.com/overview/what-is-iaas/).</span></span> <span data-ttu-id="0a600-128">Azure obsahuje několik nástrojů, jako je [Migrace Azure](https://azure.microsoft.com/services/azure-migrate/), Azure [Site Recovery](https://azure.microsoft.com/services/site-recovery/)a Azure Database [Migration Service,](https://azure.microsoft.com/campaigns/database-migration/) aby takový přesun jednodušší.</span><span class="sxs-lookup"><span data-stu-id="0a600-128">Azure includes several tools such as [Azure Migrate](https://azure.microsoft.com/services/azure-migrate/), [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/), and [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/) to make such a move easier.</span></span> <span data-ttu-id="0a600-129">I když tato strategie může přinést určité úspory nákladů, tyto aplikace obvykle nebyly navrženy tak, aby odemkly a využily výhod cloud computingu.</span><span class="sxs-lookup"><span data-stu-id="0a600-129">While this strategy can yield some cost savings, such applications typically weren't architected to unlock and leverage the benefits of cloud computing.</span></span>

<span data-ttu-id="0a600-130">Monolitické aplikace, které jsou pro firmu kritické, mají často prospěch z rozšířené migrace výtahu a posunu *(optimalizovaná pro cloud).*</span><span class="sxs-lookup"><span data-stu-id="0a600-130">Monolithic apps that are critical to the business oftentimes benefit from an enhanced lift-and-shift (*Cloud Optimized*) migration.</span></span> <span data-ttu-id="0a600-131">Tento přístup zahrnuje optimalizace nasazení, které umožňují klíčové cloudové služby – beze změny základní architektury aplikace.</span><span class="sxs-lookup"><span data-stu-id="0a600-131">This approach includes deployment optimizations that enable key cloud services - without changing the core architecture of the application.</span></span> <span data-ttu-id="0a600-132">Můžete například [kontejnerizovat aplikaci](https://docs.microsoft.com/virtualization/windowscontainers/about/) a nasadit ji do orchestrátoru kontejneru, jako je [Azure Kubernetes Services](https://azure.microsoft.com/services/kubernetes-service/), popsané dále v této knize.</span><span class="sxs-lookup"><span data-stu-id="0a600-132">For example, you might [containerize](https://docs.microsoft.com/virtualization/windowscontainers/about/) the application and deploy it to a container orchestrator, like [Azure Kubernetes Services](https://azure.microsoft.com/services/kubernetes-service/), discussed later in this book.</span></span> <span data-ttu-id="0a600-133">Jakmile je aplikace v cloudu, může využívat další cloudové služby, jako jsou databáze, fronty zpráv, monitorování a distribuované ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="0a600-133">Once in the cloud, the application could consume other cloud services such as databases, message queues, monitoring, and distributed caching.</span></span>

<span data-ttu-id="0a600-134">Nakonec monolitické aplikace, které vykonávají strategické podnikové funkce, mohou nejlépe těžit z přístupu *nativního pro cloud,* který je předmětem této knihy.</span><span class="sxs-lookup"><span data-stu-id="0a600-134">Finally, monolithic apps that perform strategic enterprise functions might best benefit from a *Cloud-Native* approach, the subject of this book.</span></span> <span data-ttu-id="0a600-135">Tento přístup poskytuje agility a rychlost.</span><span class="sxs-lookup"><span data-stu-id="0a600-135">This approach provides agility and velocity.</span></span> <span data-ttu-id="0a600-136">Ale to přijde za cenu replatforming, rearchitecting, a přepisování kódu.</span><span class="sxs-lookup"><span data-stu-id="0a600-136">But, it comes at a cost of replatforming, rearchitecting, and rewriting code.</span></span>

<span data-ttu-id="0a600-137">Pokud vy a váš tým věří, že přístup nativní pro cloud je vhodný, slábne soudůvodit rozhodnutí s vaší organizací.</span><span class="sxs-lookup"><span data-stu-id="0a600-137">If you and your team believe a cloud-native approach is appropriate, it behooves you to rationalize the decision with your organization.</span></span> <span data-ttu-id="0a600-138">Co přesně je obchodní problém, který vyřeší přístup nativní pro cloud?</span><span class="sxs-lookup"><span data-stu-id="0a600-138">What exactly is the business problem that a cloud-native approach will solve?</span></span> <span data-ttu-id="0a600-139">Jak by to bylo v souladu s obchodními potřebami?</span><span class="sxs-lookup"><span data-stu-id="0a600-139">How would it align with business needs?</span></span>

- <span data-ttu-id="0a600-140">Rychlé uvolnění funkcí se zvýšenou důvěrou?</span><span class="sxs-lookup"><span data-stu-id="0a600-140">Rapid releases of features with increased confidence?</span></span>

- <span data-ttu-id="0a600-141">Jemně odstupňovaná škálovatelnost - efektivnější využití zdrojů?</span><span class="sxs-lookup"><span data-stu-id="0a600-141">Fine-grained scalability - more efficient usage of resources?</span></span>

- <span data-ttu-id="0a600-142">Vylepšená odolnost systému?</span><span class="sxs-lookup"><span data-stu-id="0a600-142">Improved system resiliency?</span></span>

- <span data-ttu-id="0a600-143">Zlepšený výkon systému?</span><span class="sxs-lookup"><span data-stu-id="0a600-143">Improved system performance?</span></span>

- <span data-ttu-id="0a600-144">Větší přehled o operacích?</span><span class="sxs-lookup"><span data-stu-id="0a600-144">More visibility into operations?</span></span>

- <span data-ttu-id="0a600-145">Blend vývojové platformy a úložiště dat, aby se dospělo k nejlepšímu nástroji pro práci?</span><span class="sxs-lookup"><span data-stu-id="0a600-145">Blend development platforms and data stores to arrive at the best tool for the job?</span></span>

- <span data-ttu-id="0a600-146">Investice do aplikací, které obnaží budoucnost?</span><span class="sxs-lookup"><span data-stu-id="0a600-146">Future-proof application investment?</span></span>

<span data-ttu-id="0a600-147">Správná strategie migrace závisí na prioritách organizace a systémech, na které cílíte.</span><span class="sxs-lookup"><span data-stu-id="0a600-147">The right migration strategy depends on organizational priorities and the systems you're targeting.</span></span> <span data-ttu-id="0a600-148">Pro mnohé může být nákladově efektivnější optimalizovat cloud monolitickou aplikaci nebo přidat hrubé odstupňované služby do aplikace N-Tier.</span><span class="sxs-lookup"><span data-stu-id="0a600-148">For many, it may be more cost effective to cloud-optimize a monolithic application or add coarse-grained services to an N-Tier app.</span></span> <span data-ttu-id="0a600-149">V těchto případech můžete stále plně využívat cloudové paas funkce, jako jsou ty, které nabízí Azure App Service.</span><span class="sxs-lookup"><span data-stu-id="0a600-149">In these cases, you can still make full use of cloud PaaS capabilities like the ones offered by Azure App Service.</span></span>

## <a name="summary"></a><span data-ttu-id="0a600-150">Souhrn</span><span class="sxs-lookup"><span data-stu-id="0a600-150">Summary</span></span>

<span data-ttu-id="0a600-151">V této kapitole jsme zavedli cloud-nativní výpočetní techniky.</span><span class="sxs-lookup"><span data-stu-id="0a600-151">In this chapter, we introduced cloud-native computing.</span></span> <span data-ttu-id="0a600-152">Poskytli jsme definici spolu s klíčovými funkcemi, které řídí aplikaci nativní pro cloud.</span><span class="sxs-lookup"><span data-stu-id="0a600-152">We provided a definition along with the key capabilities that drive a cloud-native application.</span></span> <span data-ttu-id="0a600-153">Podívali jsme se na typy aplikací, které by mohly ospravedlnit tuto investici a úsilí.</span><span class="sxs-lookup"><span data-stu-id="0a600-153">We looked at the types of applications that might justify this investment and effort.</span></span>

<span data-ttu-id="0a600-154">Se zavedením za sebou se nyní ponoříme do mnohem podrobnějšího pohledu na nativní cloud.</span><span class="sxs-lookup"><span data-stu-id="0a600-154">With the introduction behind, we now dive into a much more detailed look at cloud native.</span></span>

### <a name="references"></a><span data-ttu-id="0a600-155">Odkazy</span><span class="sxs-lookup"><span data-stu-id="0a600-155">References</span></span>

- [<span data-ttu-id="0a600-156">Nadace cloudnative computingu</span><span class="sxs-lookup"><span data-stu-id="0a600-156">Cloud Native Computing Foundation</span></span>](https://www.cncf.io/)

- [<span data-ttu-id="0a600-157">.NET Microservices: Architektura pro kontejnerizované aplikace .NET</span><span class="sxs-lookup"><span data-stu-id="0a600-157">.NET Microservices: Architecture for Containerized .NET applications</span></span>](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [<span data-ttu-id="0a600-158">Modernizace stávajících aplikací .NET pomocí cloudu Azure a kontejnerů s Windows</span><span class="sxs-lookup"><span data-stu-id="0a600-158">Modernize existing .NET applications with Azure cloud and Windows Containers</span></span>](https://dotnet.microsoft.com/download/thank-you/modernizing-existing-net-apps-ebook)

- [<span data-ttu-id="0a600-159">Cloud Nativní vzory od Cornelia Davis</span><span class="sxs-lookup"><span data-stu-id="0a600-159">Cloud Native Patterns by Cornelia Davis</span></span>](https://www.manning.com/books/cloud-native-patterns)

- [<span data-ttu-id="0a600-160">Kromě dvanáctifaktorové aplikace</span><span class="sxs-lookup"><span data-stu-id="0a600-160">Beyond the Twelve-Factor Application</span></span>](https://content.pivotal.io/blog/beyond-the-twelve-factor-app)

- [<span data-ttu-id="0a600-161">Co je infrastruktura jako kód</span><span class="sxs-lookup"><span data-stu-id="0a600-161">What is Infrastructure as Code</span></span>](https://docs.microsoft.com/azure/devops/learn/what-is-infrastructure-as-code)

- [<span data-ttu-id="0a600-162">Micro Deploy společnosti Uber Engineering: Nasazení denně s důvěrou</span><span class="sxs-lookup"><span data-stu-id="0a600-162">Uber Engineering's Micro Deploy: Deploying Daily with Confidence</span></span>](https://eng.uber.com/micro-deploy/)

- [<span data-ttu-id="0a600-163">Jak Netflix nasazuje kód</span><span class="sxs-lookup"><span data-stu-id="0a600-163">How Netflix Deploys Code</span></span>](https://www.infoq.com/news/2013/06/netflix/)

- [<span data-ttu-id="0a600-164">Řízení přetížení pro škálování WeChat Microservices</span><span class="sxs-lookup"><span data-stu-id="0a600-164">Overload Control for Scaling WeChat Microservices</span></span>](https://www.cs.columbia.edu/~ruigu/papers/socc18-final100.pdf)

>[!div class="step-by-step"]
><span data-ttu-id="0a600-165">[Předchozí](definition.md)
>[další](introduce-eshoponcontainers-reference-app.md)</span><span class="sxs-lookup"><span data-stu-id="0a600-165">[Previous](definition.md)
[Next](introduce-eshoponcontainers-reference-app.md)</span></span>
