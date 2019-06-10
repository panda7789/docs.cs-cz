---
title: Zvedněte a shift existujících aplikací .NET do Azure IaaS (infrastruktura připravených pro Cloud)
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a kontejnery Windows.
ms.date: 04/28/2018
ms.openlocfilehash: cda316ad01a58f26661395c804547de04e20d052
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758863"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a><span data-ttu-id="c12cd-103">Zvedněte a shift existujících aplikací .NET do Azure IaaS (infrastruktura připravených pro Cloud)</span><span class="sxs-lookup"><span data-stu-id="c12cd-103">Lift and shift existing .NET apps to Azure IaaS (Cloud Infrastructure-Ready)</span></span>

> <span data-ttu-id="c12cd-104">Pro zpracování obrazu: Jako první krok abyste snížili místních investic a celkové náklady na hardware a údržbu sítí, jednoduše opětovným hostováním existující aplikace v cloudu.</span><span class="sxs-lookup"><span data-stu-id="c12cd-104">Vision: As a first step, to reduce your on-premises investment and total cost of hardware and networking maintenance, simply rehost your existing applications in the cloud.</span></span>

<span data-ttu-id="c12cd-105">Před získáním do *jak* k migraci vašich stávajících aplikací do Azure infrastruktura jako služba (IaaS), je důležité analyzovat důvody *proč* je vhodné k migraci přímo na IaaS v Azure.</span><span class="sxs-lookup"><span data-stu-id="c12cd-105">Before getting into *how* to migrate your existing applications to the Azure infrastructure as a service (IaaS) platform, it's important to analyze the reasons *why* you'd want to migrate directly to IaaS in Azure.</span></span> <span data-ttu-id="c12cd-106">Scénář na této úrovni vyspělosti modernizaci v podstatě je začít používat virtuální počítače v cloudu zlepšuje nadále používat aktuální místní infrastrukturu.</span><span class="sxs-lookup"><span data-stu-id="c12cd-106">The scenario at this modernization maturity level essentially is to start using VMs in the cloud, instead of continuing to use your current, on-premises infrastructure.</span></span>

<span data-ttu-id="c12cd-107">Je jiný bod k analýze *proč* budete chtít migrovat do čistě cloudových IaaS namísto pouhého přidání další pokročilé spravované služby v Azure.</span><span class="sxs-lookup"><span data-stu-id="c12cd-107">Another point to analyze is *why* you might want to migrate to pure IaaS cloud instead of just adding more advanced managed services in Azure.</span></span> <span data-ttu-id="c12cd-108">Zjistit, co případech může vyžadovat IaaS na prvním místě.</span><span class="sxs-lookup"><span data-stu-id="c12cd-108">Determine what cases might require IaaS in the first place.</span></span>

<span data-ttu-id="c12cd-109">Obrázek 2 – 1 umístí v úrovni vyspělosti modernizaci aplikací připravených pro Cloud infrastruktury:</span><span class="sxs-lookup"><span data-stu-id="c12cd-109">Figure 2-1 positions Cloud Infrastructure-Ready applications in the modernization maturity levels:</span></span>

![Umístění aplikací připravených pro Cloud infrastruktury](./media/image2-1.png)

> <span data-ttu-id="c12cd-111">**Obrázek 2-1.**</span><span class="sxs-lookup"><span data-stu-id="c12cd-111">**Figure 2-1.**</span></span> <span data-ttu-id="c12cd-112">Umístění aplikací připravených pro Cloud infrastruktury</span><span class="sxs-lookup"><span data-stu-id="c12cd-112">Positioning Cloud Infrastructure-Ready applications</span></span>

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a><span data-ttu-id="c12cd-113">Proč migrovat existující webové aplikace .NET do Azure IaaS</span><span class="sxs-lookup"><span data-stu-id="c12cd-113">Why migrate existing .NET web applications to Azure IaaS</span></span>

<span data-ttu-id="c12cd-114">Hlavním důvodem k migraci do cloudu, dokonce i na počáteční úrovni IaaS, je dosáhnout snížení nákladů.</span><span class="sxs-lookup"><span data-stu-id="c12cd-114">The main reason to migrate to the cloud, even at an initial IaaS level, is to achieve cost reductions.</span></span> <span data-ttu-id="c12cd-115">Pomocí další služby spravovaná infrastruktura může snížit vaše organizace své investice do hardwaru údržby, server nebo zřizování virtuálních počítačů a nasazení a správu infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="c12cd-115">By using more managed infrastructure services, your organization can lower its investment in hardware maintenance, server or VM provisioning and deployment, and infrastructure management.</span></span>

<span data-ttu-id="c12cd-116">Když provedete rozhodnutí ohledně přesunu aplikace do cloudu, bude hlavním důvodem, proč můžete zvolit IaaS místo pokročilejší možnosti jako PaaS je jednoduše prostředí IaaS více do hloubky.</span><span class="sxs-lookup"><span data-stu-id="c12cd-116">After you make the decision to move your apps to the cloud, the main reason why you might choose IaaS instead of more advanced options like PaaS is simply that the IaaS environment will be more familiar.</span></span> <span data-ttu-id="c12cd-117">Přesun do prostředí, které se podobá vaše aktuální, v místním prostředí nabízí nižší učení křivky, což zajišťuje nejrychlejší cestu do cloudu.</span><span class="sxs-lookup"><span data-stu-id="c12cd-117">Moving to an environment that's similar to your current, on-premises environment offers a lower learning curve, which makes it the quickest path to the cloud.</span></span>

<span data-ttu-id="c12cd-118">Ale trvá nejrychlejší cestu do cloudu, neznamená, že získáte všechny výhody z vaší aplikace běžící v cloudu s.</span><span class="sxs-lookup"><span data-stu-id="c12cd-118">However, taking the quickest path to the cloud doesn't mean that you will gain the most benefit from having your applications running in the cloud.</span></span> <span data-ttu-id="c12cd-119">Každá organizace získají nejvíce velké výhody migrace do cloudu na úrovni vyspělosti už zavedená optimalizovaných pro Cloud a nativní pro Cloud.</span><span class="sxs-lookup"><span data-stu-id="c12cd-119">Any organization will gain the most significant benefits from a cloud migration at the already introduced Cloud-Optimized and Cloud-Native maturity levels.</span></span>

<span data-ttu-id="c12cd-120">Také se ukázalo, že aplikace budou snadněji modernizovat a úprava architektury v budoucnu, pokud už jsou spuštěné v cloudu i na IaaS.</span><span class="sxs-lookup"><span data-stu-id="c12cd-120">It also has become evident that applications are easier to modernize and rearchitect in the future when they are already running in the cloud, even on IaaS.</span></span> <span data-ttu-id="c12cd-121">Migrace dat aplikaci již bylo dosaženo.</span><span class="sxs-lookup"><span data-stu-id="c12cd-121">Application data migration has already been achieved.</span></span> <span data-ttu-id="c12cd-122">Také budou mít vaše organizace získané znalosti potřebné pro práci v cloudu a provedené na posun působí v "cloud jazykovou verzi."</span><span class="sxs-lookup"><span data-stu-id="c12cd-122">Also, your organization will have gained skills required for working in the cloud and made the shift to operating in a "cloud culture."</span></span>

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a><span data-ttu-id="c12cd-123">Kdy migrovat na IaaS místo pro PaaS</span><span class="sxs-lookup"><span data-stu-id="c12cd-123">When to migrate to IaaS instead of to PaaS</span></span>

<span data-ttu-id="c12cd-124">Následující části popisují aplikace optimalizované pro Cloud, většinou podle PaaS platforem a služeb.</span><span class="sxs-lookup"><span data-stu-id="c12cd-124">The next sections discuss Cloud-Optimized applications that are mostly based on PaaS platforms and services.</span></span> <span data-ttu-id="c12cd-125">Tyto aplikace umožňují většina výhody z migrace do cloudu.</span><span class="sxs-lookup"><span data-stu-id="c12cd-125">These apps give you the most benefits from migrating to the cloud.</span></span> 

<span data-ttu-id="c12cd-126">Pokud je vaším cílem je jednoduše přesun stávajících aplikací do cloudu, nejprve identifikování existujících aplikací, které nepotřebuje podstatné změny ke spuštění ve službě Azure App Service.</span><span class="sxs-lookup"><span data-stu-id="c12cd-126">If your goal is simply to move existing applications to the cloud, first, identify existing applications that would not require substantial modification to run in Azure App Service.</span></span> <span data-ttu-id="c12cd-127">Tyto aplikace by měla být první kandidáty pro Cloud optimalizovaný.</span><span class="sxs-lookup"><span data-stu-id="c12cd-127">These apps should be the first candidates for Cloud-Optimized.</span></span> 

<span data-ttu-id="c12cd-128">Pak pro aplikace, která stále nelze přesunout do kontejnery Windows a PaaS, jako je App Service nebo orchestrátorů, jako jsou služby Azure Kubernetes Service migrovat do jednoduchého prostý virtuálních počítačích (IaaS).</span><span class="sxs-lookup"><span data-stu-id="c12cd-128">Then, for the apps that still cannot move to Windows Containers and PaaS such as App Service or orchestrators like Azure Kubernetes Service, migrate those to simple plain VMs (IaaS).</span></span> 

<span data-ttu-id="c12cd-129">Ale mějte na paměti, že správně konfiguraci, zabezpečení a správu virtuálních počítačů vyžaduje mnohem více času a znalosti v oboru IT ve srovnání s použitím služby PaaS v Azure.</span><span class="sxs-lookup"><span data-stu-id="c12cd-129">But, keep in mind that correctly configuring, securing, and maintaining VMs requires much more time and IT expertise compared to using PaaS services in Azure.</span></span> <span data-ttu-id="c12cd-130">Pokud uvažujete o Azure Virtual Machines, ujistěte se, že vzít v úvahu náročnost průběžné údržby vyžaduje opravu, aktualizovat a spravovat prostředí virtuálních počítačů.</span><span class="sxs-lookup"><span data-stu-id="c12cd-130">If you are considering Azure Virtual Machines, make sure that you take into account the ongoing maintenance effort required to patch, update, and manage your VM environment.</span></span> <span data-ttu-id="c12cd-131">Azure Virtual Machines je IaaS.</span><span class="sxs-lookup"><span data-stu-id="c12cd-131">Azure Virtual Machines is IaaS.</span></span>

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a><span data-ttu-id="c12cd-132">Pomocí Azure Migrate můžete analyzovat a migrovat existující aplikace do Azure</span><span class="sxs-lookup"><span data-stu-id="c12cd-132">Use Azure Migrate to analyze and migrate your existing applications to Azure</span></span>

<span data-ttu-id="c12cd-133">Migrace do cloudu nemusí být obtížná.</span><span class="sxs-lookup"><span data-stu-id="c12cd-133">Migrating to the cloud doesn't have to be difficult.</span></span> <span data-ttu-id="c12cd-134">Ale Začínáme - k Získejte podrobné informace o prostředí a těsné vzájemné závislosti mezi aplikací, úloh a dat je řada organizací velmi obtížné.</span><span class="sxs-lookup"><span data-stu-id="c12cd-134">But many organizations struggle to get started - to get deep visibility into the environment and the tight interdependencies between applications, workloads, and data.</span></span> <span data-ttu-id="c12cd-135">Bez viditelnost může být obtížné pro plán cesty vpřed.</span><span class="sxs-lookup"><span data-stu-id="c12cd-135">Without that visibility, it can be difficult to plan the path forward.</span></span> <span data-ttu-id="c12cd-136">Bez podrobných informací o jaké jsou požadavky pro úspěšné migrace nemůže mít správným konverzacím ve vaší organizaci.</span><span class="sxs-lookup"><span data-stu-id="c12cd-136">Without detailed information on what's required for a successful migration, you can't have the right conversations within your organization.</span></span> <span data-ttu-id="c12cd-137">Dostatek o potenciálních úsporách, nákladů neznáte nebo zda úlohy může právě lift and shift nebo by vyžadovaly výrazné přepracování migrace úspěšně.</span><span class="sxs-lookup"><span data-stu-id="c12cd-137">You don't know enough about the potential cost benefits, or whether workloads could just lift-and-shift or would require significant rework to migrate successfully.</span></span> <span data-ttu-id="c12cd-138">Žádné wonder, že mnoho organizací váhání.</span><span class="sxs-lookup"><span data-stu-id="c12cd-138">No wonder many organizations hesitate.</span></span>

<span data-ttu-id="c12cd-139">[Azure Migrate](https://aka.ms/azuremigrate) je nová služba, která poskytuje pokyny, přehledy a mechanizmy, které potřebuje pomoc při migraci do Azure.</span><span class="sxs-lookup"><span data-stu-id="c12cd-139">[Azure Migrate](https://aka.ms/azuremigrate) is a new service that provides the guidance, insights, and mechanisms needed to assist you in migrating to Azure.</span></span> <span data-ttu-id="c12cd-140">Azure Migrate nabízí:</span><span class="sxs-lookup"><span data-stu-id="c12cd-140">Azure Migrate provides:</span></span>

- <span data-ttu-id="c12cd-141">Zjišťování a posouzení místních virtuálních počítačů</span><span class="sxs-lookup"><span data-stu-id="c12cd-141">Discovery and assessment for on-premises virtual machines</span></span>

- <span data-ttu-id="c12cd-142">Mapování závislostí integrované bez obav zjišťování vícevrstvých aplikací</span><span class="sxs-lookup"><span data-stu-id="c12cd-142">Inbuilt dependency mapping for high-confidence discovery of multi-tier applications</span></span>

- <span data-ttu-id="c12cd-143">Inteligentní nastavení správné velikosti virtuálních počítačů Azure</span><span class="sxs-lookup"><span data-stu-id="c12cd-143">Intelligent right sizing to Azure virtual machines</span></span>

- <span data-ttu-id="c12cd-144">Kompatibility, vytváření sestav s pokyny pro napravení možných problémů</span><span class="sxs-lookup"><span data-stu-id="c12cd-144">Compatibility reporting with guidelines for remediating potential issues</span></span>

- <span data-ttu-id="c12cd-145">Integrace se službou správy databáze Azure pro databázi zjišťování a migrace</span><span class="sxs-lookup"><span data-stu-id="c12cd-145">Integration with Azure Database Management Service for database discovery and migration</span></span>

<span data-ttu-id="c12cd-146">Azure Migrate zajišťuje vaše úlohy migrace s minimálním dopadem na podnikání a spustit podle očekávání v Azure.</span><span class="sxs-lookup"><span data-stu-id="c12cd-146">Azure Migrate gives you confidence that your workloads can migrate with minimal impact to the business and run as expected in Azure.</span></span> <span data-ttu-id="c12cd-147">Správných nástrojů a pokynů můžete dosáhnout maximální návratnosti investic současným tento kritické výkon a splnění požadavků spolehlivost.</span><span class="sxs-lookup"><span data-stu-id="c12cd-147">With the right tools and guidance, you can achieve maximum return on investment while assuring that critical performance and reliability needs are met.</span></span>

<span data-ttu-id="c12cd-148">Obrázek 2-2 ukazuje mapování integrované závislostí pro všechna připojení serveru a aplikace provádí Azure Migrate.</span><span class="sxs-lookup"><span data-stu-id="c12cd-148">Figure 2-2 shows you the built-in dependency mapping for all server and application connections performed by Azure Migrate.</span></span>

![Umístění aplikací připravených pro Cloud infrastruktury](./media/image2-2.png)

> <span data-ttu-id="c12cd-150">**Obrázek 2-2.**</span><span class="sxs-lookup"><span data-stu-id="c12cd-150">**Figure 2-2.**</span></span> <span data-ttu-id="c12cd-151">Umístění aplikací připravených pro Cloud infrastruktury</span><span class="sxs-lookup"><span data-stu-id="c12cd-151">Positioning Cloud Infrastructure-Ready applications</span></span>

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a><span data-ttu-id="c12cd-152">Pomocí Azure Site Recovery můžete migrovat vaše stávající virtuální počítače na virtuální počítače Azure</span><span class="sxs-lookup"><span data-stu-id="c12cd-152">Use Azure Site Recovery to migrate your existing VMs to Azure VMs</span></span>

<span data-ttu-id="c12cd-153">Jako součást end-to-end [Azure Migrate](https://aka.ms/azuremigrate), [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) je nástroj, který vám umožní snadno migrovat vaše webové aplikace do virtuálních počítačů v Azure.</span><span class="sxs-lookup"><span data-stu-id="c12cd-153">As part of the end-to-end [Azure Migrate](https://aka.ms/azuremigrate), [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) is a tool that you can use to easily migrate your web apps to VMs in Azure.</span></span> <span data-ttu-id="c12cd-154">Můžete pomocí Site Recovery pro replikaci místních virtuálních počítačů a fyzických serverů do Azure, nebo chcete replikovat do sekundárního místního umístění.</span><span class="sxs-lookup"><span data-stu-id="c12cd-154">You can use Site Recovery to replicate on-premises VMs and physical servers to Azure, or to replicate them to a secondary on-premises location.</span></span> <span data-ttu-id="c12cd-155">Můžete dokonce replikovat úlohu, která běží na podporovaném virtuálním počítači Azure, na místní *Hyper-V* virtuálního počítače, na *VMware* virtuálního počítače, nebo na fyzickém serveru Windows nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="c12cd-155">You can even replicate a workload that's running on a supported Azure VM, on an on-premises *Hyper-V* VM, on a *VMware* VM, or on a Windows or Linux physical server.</span></span> <span data-ttu-id="c12cd-156">Replikace do Azure se eliminují náklady a složitost spojené s udržováním sekundárního datového centra.</span><span class="sxs-lookup"><span data-stu-id="c12cd-156">Replication to Azure eliminates the cost and complexity of maintaining a secondary datacenter.</span></span>

<span data-ttu-id="c12cd-157">Site Recovery je rovněž speciálně pro hybridní prostředí, které jsou částečně místně a částečně v Azure.</span><span class="sxs-lookup"><span data-stu-id="c12cd-157">Site Recovery is also made specifically for hybrid environments that are partly on-premises and partly on Azure.</span></span> <span data-ttu-id="c12cd-158">Site Recovery pomáhá zajistit kontinuitu udržováním vašimi aplikacemi, které běží na virtuálních počítačích a místní fyzické servery, které jsou k dispozici Pokud web přestane fungovat.</span><span class="sxs-lookup"><span data-stu-id="c12cd-158">Site Recovery helps ensure business continuity by keeping your apps that are running on VMs and on-premises physical servers available if a site goes down.</span></span> <span data-ttu-id="c12cd-159">Replikuje úlohy spuštěné na virtuálních počítačích a fyzických serverů tak, aby zůstaly dostupné i v nějakém sekundárním umístění Pokud primární lokalita není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="c12cd-159">It replicates workloads that are running on VMs and physical servers so that they remain available in a secondary location if the primary site isn't available.</span></span> <span data-ttu-id="c12cd-160">Do ní úlohy obnoví primární lokality, když je a znovu spustit.</span><span class="sxs-lookup"><span data-stu-id="c12cd-160">It recovers workloads to the primary site when it's up and running again.</span></span>

<span data-ttu-id="c12cd-161">Obrázek 2 – 3 ukazuje spuštění několika migrací virtuálních počítačů pomocí Azure Site Recovery.</span><span class="sxs-lookup"><span data-stu-id="c12cd-161">Figure 2-3 shows the execution of multiple VM migrations by using Azure Site Recovery.</span></span>

![Umístění aplikací připravených pro Cloud infrastruktury](./media/image2-3.png)

> <span data-ttu-id="c12cd-163">**Obrázek 2 – 3.**</span><span class="sxs-lookup"><span data-stu-id="c12cd-163">**Figure 2-3.**</span></span> <span data-ttu-id="c12cd-164">Umístění aplikací připravených pro Cloud infrastruktury</span><span class="sxs-lookup"><span data-stu-id="c12cd-164">Positioning Cloud Infrastructure-Ready applications</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c12cd-165">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="c12cd-165">Additional resources</span></span>

- <span data-ttu-id="c12cd-166">**Azure Migrate datový list**</span><span class="sxs-lookup"><span data-stu-id="c12cd-166">**Azure Migrate Datasheet**</span></span>

    <https://aka.ms/azuremigration\_datasheet>

- <span data-ttu-id="c12cd-167">**Azure Migrate**</span><span class="sxs-lookup"><span data-stu-id="c12cd-167">**Azure Migrate**</span></span>

    <https://aka.ms/azuremigrate>

- <span data-ttu-id="c12cd-168">**Migrační Centrum Azure**</span><span class="sxs-lookup"><span data-stu-id="c12cd-168">**Azure migration center**</span></span>

    <https://azure.microsoft.com/migration/>

- <span data-ttu-id="c12cd-169">**Migrace do Azure pomocí Site Recovery**</span><span class="sxs-lookup"><span data-stu-id="c12cd-169">**Migrate to Azure with Site Recovery**</span></span>

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure>

- <span data-ttu-id="c12cd-170">**Přehled služby Azure Site Recovery**</span><span class="sxs-lookup"><span data-stu-id="c12cd-170">**Azure Site Recovery service overview**</span></span>

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-overview>

- <span data-ttu-id="c12cd-171">**Migrace virtuálních počítačů v AWS do virtuálních počítačů Azure**</span><span class="sxs-lookup"><span data-stu-id="c12cd-171">**Migrating VMs in AWS to Azure VMs**</span></span>

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure>

>[!div class="step-by-step"]
><span data-ttu-id="c12cd-172">[Předchozí](index.md)
>[další](migrate-your-relational-databases-to-azure.md)</span><span class="sxs-lookup"><span data-stu-id="c12cd-172">[Previous](index.md)
[Next](migrate-your-relational-databases-to-azure.md)</span></span>
