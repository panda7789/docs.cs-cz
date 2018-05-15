---
title: Migrace na hybridní cloudové scénáře
description: Modernizovat existující aplikace .NET s kontejnery cloudu Azure a Windows | Migrace na hybridní cloudové scénáře
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 8885ee8fce4f8c11c14ee8936f3ee0ffd89ece04
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a><span data-ttu-id="50c5f-103">Migrace na hybridní cloudové scénáře</span><span class="sxs-lookup"><span data-stu-id="50c5f-103">Migrate to hybrid cloud scenarios</span></span>

<span data-ttu-id="50c5f-104">Některé organizacím a podnikům umožňují nemůžete migrovat některé z aplikací a veřejných cloudů, jako je například Microsoft Azure nebo jiných veřejného cloudu z důvodu předpisy nebo vlastní zásady.</span><span class="sxs-lookup"><span data-stu-id="50c5f-104">Some organizations and enterprises can't migrate some of their applications to public clouds like Microsoft Azure or any other public cloud due to regulations or their own policies.</span></span> <span data-ttu-id="50c5f-105">Je ale pravděpodobné, že některé z organizací, mohou využít s některé jejich aplikací ve veřejném cloudu a další aplikace místně.</span><span class="sxs-lookup"><span data-stu-id="50c5f-105">However, it's likely that any organization might benefit from having some of their applications in the public cloud and other applications on-premises.</span></span> <span data-ttu-id="50c5f-106">Ale smíšeném prostředí může způsobit nadměrné složitosti v prostředích různých platforem a technologií používaných v veřejné cloudy a místními prostředími.</span><span class="sxs-lookup"><span data-stu-id="50c5f-106">But a mixed environment can lead to excessive complexity in environments due to different platforms and technologies used in public clouds versus on-premises environments.</span></span>

<span data-ttu-id="50c5f-107">Společnost Microsoft poskytuje nejlepší hybridní cloudové řešení, jeden ve kterém můžete optimalizovat vaše stávající prostředky místní a ve veřejném cloudu, zatímco zajistit konzistenci Azure hybridní cloud.</span><span class="sxs-lookup"><span data-stu-id="50c5f-107">Microsoft provides the best hybrid cloud solution, one in which you can optimize your existing assets on-premises and in the public cloud, while you ensure consistency in an Azure hybrid cloud.</span></span> <span data-ttu-id="50c5f-108">Můžete maximalizovat existujících dovedností a získat flexibilní, jednotný přístup k sestavení aplikace, které můžou běžet v cloudu nebo místně, díky zásobník Azure (místní) a Azure (veřejný cloud).</span><span class="sxs-lookup"><span data-stu-id="50c5f-108">You can maximize existing skills, and get a flexible, unified approach to building apps that can run in the cloud or on-premises, thanks to Azure Stack (on-premises) and Azure (public cloud).</span></span>

<span data-ttu-id="50c5f-109">Pokud jde o zabezpečení, můžete centralizovat správu a zabezpečení mezi hybridní cloud.</span><span class="sxs-lookup"><span data-stu-id="50c5f-109">When it comes to security, you can centralize management and security across your hybrid cloud.</span></span> <span data-ttu-id="50c5f-110">Můžete získat kontrolu nad všechny prostředky z vašeho datového centra do cloudu, tím, že poskytuje jednotné přihlašování k místnímu a cloudových aplikací.</span><span class="sxs-lookup"><span data-stu-id="50c5f-110">You can get control over all assets, from your datacenter to the cloud, by providing single sign-on to on-premises and cloud apps.</span></span> <span data-ttu-id="50c5f-111">Můžete dosáhnout pomocí rozšíření služby Active Directory k hybridní cloud a pomocí správy identit.</span><span class="sxs-lookup"><span data-stu-id="50c5f-111">You accomplish this by extending Active Directory to a hybrid cloud, and by using identity management.</span></span>

<span data-ttu-id="50c5f-112">Nakonec můžete distribuovat a bezproblémově analyzovat data, používat stejné jazyky dotazu pro cloudové a místní prostředky a použít analýzy a přímý učení v Azure a rozšíření dat, bez ohledu na její zdroj.</span><span class="sxs-lookup"><span data-stu-id="50c5f-112">Finally, you can distribute and analyze data seamlessly, use the same query languages for cloud and on-premises assets, and apply analytics and deep learning in Azure to enrich your data, regardless of its source.</span></span>

## <a name="azure-stack"></a><span data-ttu-id="50c5f-113">Azure zásobníku</span><span class="sxs-lookup"><span data-stu-id="50c5f-113">Azure Stack</span></span>

<span data-ttu-id="50c5f-114">Zásobník Azure je hybridní cloudové platformy, která umožňuje poskytovat služby Azure z vaší organizace datového centra.</span><span class="sxs-lookup"><span data-stu-id="50c5f-114">Azure Stack is a hybrid cloud platform that lets you deliver Azure services from your organization's datacenter.</span></span> <span data-ttu-id="50c5f-115">Azure zásobníku je navržen pro podporu nové možnosti pro moderní aplikace v klíčových scénářů, jako je okraj a prostředích bez připojení nebo konkrétní požadavky zabezpečení a dodržování předpisů na schůzku.</span><span class="sxs-lookup"><span data-stu-id="50c5f-115">Azure Stack is designed to support new options for your modern applications in key scenarios, like edge and unconnected environments, or meeting specific security and compliance requirements.</span></span>

<span data-ttu-id="50c5f-116">Obrázek 4 – 13 ukazuje přehled true hybridní Cloudová platforma, která společnost Microsoft nabízí.</span><span class="sxs-lookup"><span data-stu-id="50c5f-116">Figure 4-13 shows an overview of the true hybrid cloud platform that Microsoft offers.</span></span>

![Hybridní Cloudová platforma Microsoft s zásobník Azure a Azure](./media/image13.jpg)

> <span data-ttu-id="50c5f-118">**Obrázek 4 – 13.**</span><span class="sxs-lookup"><span data-stu-id="50c5f-118">**Figure 4-13.**</span></span> <span data-ttu-id="50c5f-119">Hybridní Cloudová platforma Microsoft s zásobník Azure a Azure</span><span class="sxs-lookup"><span data-stu-id="50c5f-119">Microsoft hybrid cloud platform with Azure Stack and Azure</span></span>

<span data-ttu-id="50c5f-120">Azure zásobník je k dispozici v dvě možnosti nasazení, aby odpovídaly vašim potřebám:</span><span class="sxs-lookup"><span data-stu-id="50c5f-120">Azure Stack is offered in two deployment options, to meet your needs:</span></span>

-   <span data-ttu-id="50c5f-121">Azure zásobníku integrované systémy</span><span class="sxs-lookup"><span data-stu-id="50c5f-121">Azure Stack integrated systems</span></span>

-   <span data-ttu-id="50c5f-122">Azure zásobníku Development Kit</span><span class="sxs-lookup"><span data-stu-id="50c5f-122">Azure Stack Development Kit</span></span>

### <a name="azure-stack-integrated-systems"></a><span data-ttu-id="50c5f-123">Azure zásobníku integrované systémy</span><span class="sxs-lookup"><span data-stu-id="50c5f-123">Azure Stack integrated systems</span></span>

<span data-ttu-id="50c5f-124">Azure zásobníku integrované systémy jsou nabízena prostřednictvím partnerství partnerů společnosti Microsoft a hardwaru.</span><span class="sxs-lookup"><span data-stu-id="50c5f-124">Azure Stack integrated systems are offered through a partnership of Microsoft and hardware partners.</span></span> <span data-ttu-id="50c5f-125">Spolupráci vytvoří řešení, které nabízí cloudu pracovníky inovací, který je vyvážit s jednoduchost ve správě.</span><span class="sxs-lookup"><span data-stu-id="50c5f-125">The partnership creates a solution that offers cloud-paced innovation that is balanced with simplicity in management.</span></span> <span data-ttu-id="50c5f-126">Protože zásobník Azure je poskytován jako integrovaný systém hardwaru a softwaru, zobrazí správného množství flexibilitu a řízení, při přijetí stále inovací z cloudu.</span><span class="sxs-lookup"><span data-stu-id="50c5f-126">Because Azure Stack is offered as an integrated system of hardware and software, you get the right amount of flexibility and control, while still adopting innovation from the cloud.</span></span> <span data-ttu-id="50c5f-127">Azure zásobníku integrované systémy rozsahu velikosti od 4 do 12 uzlů a společně podporuje hardwaru partnera a společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="50c5f-127">Azure Stack integrated systems range in size from 4 to 12 nodes, and are jointly supported by the hardware partner and Microsoft.</span></span> <span data-ttu-id="50c5f-128">Použití Azure zásobníku integrované systémy implementovat nové scénáře pro produkční zatížení.</span><span class="sxs-lookup"><span data-stu-id="50c5f-128">Use Azure Stack integrated systems to implement new scenarios for your production workloads.</span></span>

### <a name="azure-stack-development-kit"></a><span data-ttu-id="50c5f-129">Azure zásobníku Development Kit</span><span class="sxs-lookup"><span data-stu-id="50c5f-129">Azure Stack Development Kit</span></span>

<span data-ttu-id="50c5f-130">Microsoft Azure zásobníku Development Kit je jedním uzlem nasazení zásobníku Azure, který můžete použít k vyhodnocení a další informace o Azure zásobníku.</span><span class="sxs-lookup"><span data-stu-id="50c5f-130">Microsoft Azure Stack Development Kit is a single-node deployment of Azure Stack, which you can use to evaluate and learn about Azure Stack.</span></span> <span data-ttu-id="50c5f-131">Můžete také použít Azure zásobníku Development Kit jako vývojářského prostředí, kde můžete vyvíjet pomocí rozhraní API a nástrojů, které jsou konzistentní s Azure.</span><span class="sxs-lookup"><span data-stu-id="50c5f-131">You can also use Azure Stack Development Kit as a developer environment, where you can develop using APIs and tooling that are consistent with Azure.</span></span> <span data-ttu-id="50c5f-132">Azure Development Kit zásobníku není určena pro použití jako provozním prostředí.</span><span class="sxs-lookup"><span data-stu-id="50c5f-132">Azure Stack Development Kit is not intended to be used as a production environment.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="50c5f-133">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="50c5f-133">Additional resources</span></span>

-   <span data-ttu-id="50c5f-134">**Azure hybridního cloudu**</span><span class="sxs-lookup"><span data-stu-id="50c5f-134">**Azure hybrid cloud**</span></span>

    [https://www.microsoft.com/cloud-platform/hybrid-cloud](https://www.microsoft.com/cloud-platform/hybrid-cloud)

-   <span data-ttu-id="50c5f-135">**Azure zásobníku**</span><span class="sxs-lookup"><span data-stu-id="50c5f-135">**Azure Stack**</span></span>

    [https://azure.microsoft.com/overview/azure-stack/](https://azure.microsoft.com/overview/azure-stack/)

-   <span data-ttu-id="50c5f-136">**Účty služby Active Directory pro Windows kontejnery**</span><span class="sxs-lookup"><span data-stu-id="50c5f-136">**Active Directory Service Accounts for Windows Containers**</span></span>

    [https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts)

-   <span data-ttu-id="50c5f-137">**Vytvořit kontejner s podporou služby Active Directory**</span><span class="sxs-lookup"><span data-stu-id="50c5f-137">**Create a container with Active Directory support**</span></span>

    [https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/](https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/)

-   <span data-ttu-id="50c5f-138">**Licencování Azure hybridní výhody**</span><span class="sxs-lookup"><span data-stu-id="50c5f-138">**Azure Hybrid Benefit licensing**</span></span>

    [https://azure.microsoft.com/pricing/hybrid-use-benefit/](https://azure.microsoft.com/pricing/hybrid-use-benefit/)

>[!div class="step-by-step"]
<span data-ttu-id="50c5f-139">[Předchozí](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[další](../walkthroughs-technical-get-started-overview.md)</span><span class="sxs-lookup"><span data-stu-id="50c5f-139">[Previous](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[Next](../walkthroughs-technical-get-started-overview.md)</span></span>
