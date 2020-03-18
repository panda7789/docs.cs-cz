---
title: Scénáře migrace do hybridního cloudu
description: Modernizace stávajících aplikací .NET pomocí Azure Cloudu a kontejnerů Windows | Migrace do hybridních cloudových scénářů
ms.date: 04/30/2018
ms.openlocfilehash: dcbb799a45609f8bb811866c4041951abf1fda8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937365"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a><span data-ttu-id="70977-103">Scénáře migrace do hybridního cloudu</span><span class="sxs-lookup"><span data-stu-id="70977-103">Migrate to hybrid cloud scenarios</span></span>

<span data-ttu-id="70977-104">Některé organizace a podniky nemohou migrovat některé své aplikace do veřejných cloudů, jako je Microsoft Azure nebo jakýkoli jiný veřejný cloud kvůli předpisům nebo vlastním zásadám.</span><span class="sxs-lookup"><span data-stu-id="70977-104">Some organizations and enterprises can't migrate some of their applications to public clouds like Microsoft Azure or any other public cloud due to regulations or their own policies.</span></span> <span data-ttu-id="70977-105">Je však pravděpodobné, že každá organizace může mít prospěch z toho, že má některé své aplikace ve veřejném cloudu a v dalších místních aplikacích.</span><span class="sxs-lookup"><span data-stu-id="70977-105">However, it's likely that any organization might benefit from having some of their applications in the public cloud and other applications on-premises.</span></span> <span data-ttu-id="70977-106">Smíšené prostředí však může vést k nadměrné složitosti prostředí kvůli různým platformám a technologiím používaným ve veřejných cloudech oproti místním prostředím.</span><span class="sxs-lookup"><span data-stu-id="70977-106">But a mixed environment can lead to excessive complexity in environments due to different platforms and technologies used in public clouds versus on-premises environments.</span></span>

<span data-ttu-id="70977-107">Microsoft poskytuje nejlepší hybridní cloudové řešení, ve kterém můžete optimalizovat stávající prostředky místně a ve veřejném cloudu a zároveň zajistit konzistenci v hybridním cloudu Azure.</span><span class="sxs-lookup"><span data-stu-id="70977-107">Microsoft provides the best hybrid cloud solution, one in which you can optimize your existing assets on-premises and in the public cloud, while you ensure consistency in an Azure hybrid cloud.</span></span> <span data-ttu-id="70977-108">Díky Azure Stacku (místní) a Azure (veřejný cloud) můžete maximalizovat stávající dovednosti a získat flexibilní a jednotný přístup k vytváření aplikací, které můžou běžet v cloudu nebo místně.</span><span class="sxs-lookup"><span data-stu-id="70977-108">You can maximize existing skills, and get a flexible, unified approach to building apps that can run in the cloud or on-premises, thanks to Azure Stack (on-premises) and Azure (public cloud).</span></span>

<span data-ttu-id="70977-109">Pokud jde o zabezpečení, můžete centralizovat správu a zabezpečení v celém hybridním cloudu.</span><span class="sxs-lookup"><span data-stu-id="70977-109">When it comes to security, you can centralize management and security across your hybrid cloud.</span></span> <span data-ttu-id="70977-110">Můžete získat kontrolu nad všemi prostředky, z vašeho datového centra do cloudu, tím, že poskytuje jednotné přihlašování k místním a cloudovým aplikacím.</span><span class="sxs-lookup"><span data-stu-id="70977-110">You can get control over all assets, from your datacenter to the cloud, by providing single sign-on to on-premises and cloud apps.</span></span> <span data-ttu-id="70977-111">Toho lze dosáhnout rozšířením služby Active Directory na hybridní cloud a pomocí správy identit.</span><span class="sxs-lookup"><span data-stu-id="70977-111">You accomplish this by extending Active Directory to a hybrid cloud, and by using identity management.</span></span>

<span data-ttu-id="70977-112">Nakonec můžete bez problémů distribuovat a analyzovat data, používat stejné jazyky dotazů pro cloudové a místní prostředky a používat analýzy a hloubkové učení v Azure k obohacení dat bez ohledu na jejich zdroj.</span><span class="sxs-lookup"><span data-stu-id="70977-112">Finally, you can distribute and analyze data seamlessly, use the same query languages for cloud and on-premises assets, and apply analytics and deep learning in Azure to enrich your data, regardless of its source.</span></span>

## <a name="azure-stack"></a><span data-ttu-id="70977-113">Azure Stack</span><span class="sxs-lookup"><span data-stu-id="70977-113">Azure Stack</span></span>

<span data-ttu-id="70977-114">Azure Stack je hybridní cloudová platforma, která vám umožní poskytovat služby Azure z datového centra vaší organizace.</span><span class="sxs-lookup"><span data-stu-id="70977-114">Azure Stack is a hybrid cloud platform that lets you deliver Azure services from your organization's datacenter.</span></span> <span data-ttu-id="70977-115">Azure Stack je navržený tak, aby podporoval nové možnosti pro vaše moderní aplikace v klíčových scénářích, jako jsou hraniční a nepropojená prostředí, nebo splnění specifických požadavků na zabezpečení a dodržování předpisů.</span><span class="sxs-lookup"><span data-stu-id="70977-115">Azure Stack is designed to support new options for your modern applications in key scenarios, like edge and unconnected environments, or meeting specific security and compliance requirements.</span></span>

<span data-ttu-id="70977-116">Obrázek 4-13 ukazuje přehled skutečné hybridní cloudové platformy, kterou Microsoft nabízí.</span><span class="sxs-lookup"><span data-stu-id="70977-116">Figure 4-13 shows an overview of the true hybrid cloud platform that Microsoft offers.</span></span>

![Diagram hybridní cloudové platformy Microsoftu s Azure Stack a Azure.](./media/migrate-to-hybrid-cloud-scenarios/microsoft-hybrid-cloud-platform.png)

<span data-ttu-id="70977-118">**Obrázek 4-13.**</span><span class="sxs-lookup"><span data-stu-id="70977-118">**Figure 4-13.**</span></span> <span data-ttu-id="70977-119">Hybridní cloudová platforma Microsoftu s Azure Stackem a Azure</span><span class="sxs-lookup"><span data-stu-id="70977-119">Microsoft hybrid cloud platform with Azure Stack and Azure</span></span>

<span data-ttu-id="70977-120">Azure Stack se nabízí ve dvou možnostech nasazení, které splní vaše potřeby:</span><span class="sxs-lookup"><span data-stu-id="70977-120">Azure Stack is offered in two deployment options, to meet your needs:</span></span>

- <span data-ttu-id="70977-121">Integrované systémy Azure Stack</span><span class="sxs-lookup"><span data-stu-id="70977-121">Azure Stack integrated systems</span></span>

- <span data-ttu-id="70977-122">Azure Stack Development Kit</span><span class="sxs-lookup"><span data-stu-id="70977-122">Azure Stack Development Kit</span></span>

### <a name="azure-stack-integrated-systems"></a><span data-ttu-id="70977-123">Integrované systémy Azure Stack</span><span class="sxs-lookup"><span data-stu-id="70977-123">Azure Stack integrated systems</span></span>

<span data-ttu-id="70977-124">Integrované systémy Azure Stack jsou nabízeny prostřednictvím partnerství Microsoftu a hardwarových partnerů.</span><span class="sxs-lookup"><span data-stu-id="70977-124">Azure Stack integrated systems are offered through a partnership of Microsoft and hardware partners.</span></span> <span data-ttu-id="70977-125">Partnerství vytváří řešení, které nabízí inovace v cloudovém tempu, které je vyváženo jednoduchostí správy.</span><span class="sxs-lookup"><span data-stu-id="70977-125">The partnership creates a solution that offers cloud-paced innovation that is balanced with simplicity in management.</span></span> <span data-ttu-id="70977-126">Vzhledem k tomu, že Azure Stack je nabízen jako integrovaný systém hardwaru a softwaru, získáte správné množství flexibility a kontroly a zároveň přijímáte inovace z cloudu.</span><span class="sxs-lookup"><span data-stu-id="70977-126">Because Azure Stack is offered as an integrated system of hardware and software, you get the right amount of flexibility and control, while still adopting innovation from the cloud.</span></span> <span data-ttu-id="70977-127">Integrované systémy Azure Stack se pohybují ve velikosti od 4 do 12 uzlů a jsou společně podporovány hardwarovým partnerem a Microsoftem.</span><span class="sxs-lookup"><span data-stu-id="70977-127">Azure Stack integrated systems range in size from 4 to 12 nodes, and are jointly supported by the hardware partner and Microsoft.</span></span> <span data-ttu-id="70977-128">Pomocí integrovaných systémů Azure Stack implementujte nové scénáře pro vaše produkční úlohy.</span><span class="sxs-lookup"><span data-stu-id="70977-128">Use Azure Stack integrated systems to implement new scenarios for your production workloads.</span></span>

### <a name="azure-stack-development-kit"></a><span data-ttu-id="70977-129">Azure Stack Development Kit</span><span class="sxs-lookup"><span data-stu-id="70977-129">Azure Stack Development Kit</span></span>

<span data-ttu-id="70977-130">Microsoft Azure Stack Development Kit je jednouzde nasazení Azure Stack, které můžete použít k vyhodnocení a získat informace o Azure Stack.</span><span class="sxs-lookup"><span data-stu-id="70977-130">Microsoft Azure Stack Development Kit is a single-node deployment of Azure Stack, which you can use to evaluate and learn about Azure Stack.</span></span> <span data-ttu-id="70977-131">Azure Stack Development Kit můžete také použít jako vývojářské prostředí, kde můžete vyvíjet pomocí api a nástrojů, které jsou konzistentní s Azure.</span><span class="sxs-lookup"><span data-stu-id="70977-131">You can also use Azure Stack Development Kit as a developer environment, where you can develop using APIs and tooling that are consistent with Azure.</span></span> <span data-ttu-id="70977-132">Azure Stack Development Kit není určen pro použití jako produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="70977-132">Azure Stack Development Kit is not intended to be used as a production environment.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="70977-133">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="70977-133">Additional resources</span></span>

- <span data-ttu-id="70977-134">**Hybridní cloud Azure**</span><span class="sxs-lookup"><span data-stu-id="70977-134">**Azure hybrid cloud**</span></span>

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- <span data-ttu-id="70977-135">**Azure Stack**</span><span class="sxs-lookup"><span data-stu-id="70977-135">**Azure Stack**</span></span>

    <https://azure.microsoft.com/overview/azure-stack/>

- <span data-ttu-id="70977-136">**Účty služby Active Directory pro kontejnery systému Windows**</span><span class="sxs-lookup"><span data-stu-id="70977-136">**Active Directory Service Accounts for Windows Containers**</span></span>

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- <span data-ttu-id="70977-137">**Vytvoření kontejneru s podporou služby Active Directory**</span><span class="sxs-lookup"><span data-stu-id="70977-137">**Create a container with Active Directory support**</span></span>

    <https://docs.microsoft.com/archive/blogs/containerstuff/create-a-container-with-active-directory-support>

- <span data-ttu-id="70977-138">**Licencování hybridních výhod Azure**</span><span class="sxs-lookup"><span data-stu-id="70977-138">**Azure Hybrid Benefit licensing**</span></span>

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
><span data-ttu-id="70977-139">[Předchozí](life-cycle-ci-cd-pipelines-devops-tools.md)
>[další](../walkthroughs-technical-get-started-overview.md)</span><span class="sxs-lookup"><span data-stu-id="70977-139">[Previous](life-cycle-ci-cd-pipelines-devops-tools.md)
[Next](../walkthroughs-technical-get-started-overview.md)</span></span>
