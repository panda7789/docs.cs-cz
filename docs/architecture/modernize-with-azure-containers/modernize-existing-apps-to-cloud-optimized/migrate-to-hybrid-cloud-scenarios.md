---
title: Scénáře migrace do hybridního cloudu
description: Modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows | Scénáře migrace do hybridního cloudu
ms.date: 04/30/2018
ms.openlocfilehash: 313608c41427b3833bbc873398595ceb37bd7c7d
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373949"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a><span data-ttu-id="88e40-103">Scénáře migrace do hybridního cloudu</span><span class="sxs-lookup"><span data-stu-id="88e40-103">Migrate to hybrid cloud scenarios</span></span>

<span data-ttu-id="88e40-104">Některé organizace a podniky nemůžou migrovat některé aplikace do veřejných cloudů, jako je Microsoft Azure nebo jiný veřejný cloud z důvodu předpisů nebo jejich vlastních zásad.</span><span class="sxs-lookup"><span data-stu-id="88e40-104">Some organizations and enterprises can't migrate some of their applications to public clouds like Microsoft Azure or any other public cloud due to regulations or their own policies.</span></span> <span data-ttu-id="88e40-105">Je ale pravděpodobné, že by jakákoli organizace mohla využívat některé z svých aplikací ve veřejném cloudu i v místních aplikacích.</span><span class="sxs-lookup"><span data-stu-id="88e40-105">However, it's likely that any organization might benefit from having some of their applications in the public cloud and other applications on-premises.</span></span> <span data-ttu-id="88e40-106">Smíšené prostředí ale může vést k nadměrné složitosti prostředí v důsledku různých platforem a technologií používaných ve veřejných cloudech i v místních prostředích.</span><span class="sxs-lookup"><span data-stu-id="88e40-106">But a mixed environment can lead to excessive complexity in environments due to different platforms and technologies used in public clouds versus on-premises environments.</span></span>

<span data-ttu-id="88e40-107">Microsoft poskytuje nejlepší řešení hybridního cloudu, které umožňuje optimalizovat stávající prostředky místně i ve veřejném cloudu a přitom zajistit konzistenci v hybridním cloudu Azure.</span><span class="sxs-lookup"><span data-stu-id="88e40-107">Microsoft provides the best hybrid cloud solution, one in which you can optimize your existing assets on-premises and in the public cloud, while you ensure consistency in an Azure hybrid cloud.</span></span> <span data-ttu-id="88e40-108">Můžete maximalizovat stávající dovednosti a získat flexibilní a jednotný přístup k vytváření aplikací, které můžou běžet v cloudu nebo místně, a díky tomu Azure Stack (místní) a Azure (veřejný cloud).</span><span class="sxs-lookup"><span data-stu-id="88e40-108">You can maximize existing skills, and get a flexible, unified approach to building apps that can run in the cloud or on-premises, thanks to Azure Stack (on-premises) and Azure (public cloud).</span></span>

<span data-ttu-id="88e40-109">Pokud jde o zabezpečení, můžete spravovat správu a zabezpečení napříč hybridním cloudem.</span><span class="sxs-lookup"><span data-stu-id="88e40-109">When it comes to security, you can centralize management and security across your hybrid cloud.</span></span> <span data-ttu-id="88e40-110">Díky jednotnému přihlašování k místním i cloudovým aplikacím můžete získat kontrolu nad všemi prostředky z vašeho datacentra do cloudu.</span><span class="sxs-lookup"><span data-stu-id="88e40-110">You can get control over all assets, from your datacenter to the cloud, by providing single sign-on to on-premises and cloud apps.</span></span> <span data-ttu-id="88e40-111">Toho dosáhnete rozšířením služby Active Directory do hybridního cloudu a pomocí správy identit.</span><span class="sxs-lookup"><span data-stu-id="88e40-111">You accomplish this by extending Active Directory to a hybrid cloud, and by using identity management.</span></span>

<span data-ttu-id="88e40-112">Nakonec můžete bez problémů distribuovat a analyzovat data, použít stejné jazyky pro cloudové a místní prostředky a pomocí analýz a hloubkového učení v Azure rozšířit vaše data bez ohledu na její zdroj.</span><span class="sxs-lookup"><span data-stu-id="88e40-112">Finally, you can distribute and analyze data seamlessly, use the same query languages for cloud and on-premises assets, and apply analytics and deep learning in Azure to enrich your data, regardless of its source.</span></span>

## <a name="azure-stack"></a><span data-ttu-id="88e40-113">Azure Stack</span><span class="sxs-lookup"><span data-stu-id="88e40-113">Azure Stack</span></span>

<span data-ttu-id="88e40-114">Azure Stack je hybridní cloudová platforma, která vám umožní poskytovat služby Azure z datového centra vaší organizace.</span><span class="sxs-lookup"><span data-stu-id="88e40-114">Azure Stack is a hybrid cloud platform that lets you deliver Azure services from your organization's datacenter.</span></span> <span data-ttu-id="88e40-115">Azure Stack je navržená tak, aby podporovala nové možnosti pro moderní aplikace ve klíčových scénářích, jako jsou Edge a nepřipojená prostředí, nebo splňuje konkrétní požadavky na zabezpečení a dodržování předpisů.</span><span class="sxs-lookup"><span data-stu-id="88e40-115">Azure Stack is designed to support new options for your modern applications in key scenarios, like edge and unconnected environments, or meeting specific security and compliance requirements.</span></span>

<span data-ttu-id="88e40-116">Obrázek 4-13 ukazuje přehled skutečné hybridní cloudové platformy, kterou Microsoft nabízí.</span><span class="sxs-lookup"><span data-stu-id="88e40-116">Figure 4-13 shows an overview of the true hybrid cloud platform that Microsoft offers.</span></span>

![Hybridní cloudová platforma Microsoft s Azure Stack a Azure](./media/image13.jpg)

<span data-ttu-id="88e40-118">**Obrázek 4-13.**</span><span class="sxs-lookup"><span data-stu-id="88e40-118">**Figure 4-13.**</span></span> <span data-ttu-id="88e40-119">Hybridní cloudová platforma Microsoft s Azure Stack a Azure</span><span class="sxs-lookup"><span data-stu-id="88e40-119">Microsoft hybrid cloud platform with Azure Stack and Azure</span></span>

<span data-ttu-id="88e40-120">Azure Stack se nabízí ve dvou možnostech nasazení, které odpovídají vašim potřebám:</span><span class="sxs-lookup"><span data-stu-id="88e40-120">Azure Stack is offered in two deployment options, to meet your needs:</span></span>

- <span data-ttu-id="88e40-121">Integrované systémy pro službu Azure Stack</span><span class="sxs-lookup"><span data-stu-id="88e40-121">Azure Stack integrated systems</span></span>

- <span data-ttu-id="88e40-122">Vývojová sada pro Azure Stack</span><span class="sxs-lookup"><span data-stu-id="88e40-122">Azure Stack Development Kit</span></span>

### <a name="azure-stack-integrated-systems"></a><span data-ttu-id="88e40-123">Integrované systémy pro službu Azure Stack</span><span class="sxs-lookup"><span data-stu-id="88e40-123">Azure Stack integrated systems</span></span>

<span data-ttu-id="88e40-124">Azure Stack integrované systémy jsou nabízeny prostřednictvím partnerství s Microsoftem a hardwarovými partnery.</span><span class="sxs-lookup"><span data-stu-id="88e40-124">Azure Stack integrated systems are offered through a partnership of Microsoft and hardware partners.</span></span> <span data-ttu-id="88e40-125">Partnerství vytvoří řešení, které nabízí inovace s využitím cloudu, které jsou v rámci správy vyvážené s jednoduchostí.</span><span class="sxs-lookup"><span data-stu-id="88e40-125">The partnership creates a solution that offers cloud-paced innovation that is balanced with simplicity in management.</span></span> <span data-ttu-id="88e40-126">Vzhledem k tomu, že Azure Stack se nabízí jako integrovaný systém hardwaru a softwaru, získáte správnou míru flexibility a kontroly a zároveň stále přijímáte inovace z cloudu.</span><span class="sxs-lookup"><span data-stu-id="88e40-126">Because Azure Stack is offered as an integrated system of hardware and software, you get the right amount of flexibility and control, while still adopting innovation from the cloud.</span></span> <span data-ttu-id="88e40-127">Azure Stack integrovaných systémů v rozsahu od 4 do 12 uzlů a jsou společně podporované hardwarovým partnerem a společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="88e40-127">Azure Stack integrated systems range in size from 4 to 12 nodes, and are jointly supported by the hardware partner and Microsoft.</span></span> <span data-ttu-id="88e40-128">Pomocí Azure Stack integrovaných systémů můžete implementovat nové scénáře pro produkční úlohy.</span><span class="sxs-lookup"><span data-stu-id="88e40-128">Use Azure Stack integrated systems to implement new scenarios for your production workloads.</span></span>

### <a name="azure-stack-development-kit"></a><span data-ttu-id="88e40-129">Vývojová sada pro Azure Stack</span><span class="sxs-lookup"><span data-stu-id="88e40-129">Azure Stack Development Kit</span></span>

<span data-ttu-id="88e40-130">Microsoft Azure Stack Development Kit je nasazení Azure Stack s jedním uzlem, které můžete použít k vyhodnocení a získání informací o Azure Stack.</span><span class="sxs-lookup"><span data-stu-id="88e40-130">Microsoft Azure Stack Development Kit is a single-node deployment of Azure Stack, which you can use to evaluate and learn about Azure Stack.</span></span> <span data-ttu-id="88e40-131">Azure Stack Development Kit můžete použít také jako vývojářské prostředí, kde můžete vyvíjet pomocí rozhraní API a nástrojů, které jsou konzistentní s Azure.</span><span class="sxs-lookup"><span data-stu-id="88e40-131">You can also use Azure Stack Development Kit as a developer environment, where you can develop using APIs and tooling that are consistent with Azure.</span></span> <span data-ttu-id="88e40-132">Azure Stack Development Kit není určeno pro použití v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="88e40-132">Azure Stack Development Kit is not intended to be used as a production environment.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="88e40-133">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="88e40-133">Additional resources</span></span>

- <span data-ttu-id="88e40-134">**Hybridní cloud Azure**</span><span class="sxs-lookup"><span data-stu-id="88e40-134">**Azure hybrid cloud**</span></span>

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- <span data-ttu-id="88e40-135">**Azure Stack**</span><span class="sxs-lookup"><span data-stu-id="88e40-135">**Azure Stack**</span></span>

    <https://azure.microsoft.com/overview/azure-stack/>

- <span data-ttu-id="88e40-136">**Účty služby Active Directory pro kontejnery Windows**</span><span class="sxs-lookup"><span data-stu-id="88e40-136">**Active Directory Service Accounts for Windows Containers**</span></span>

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- <span data-ttu-id="88e40-137">**Vytvoření kontejneru s podporou služby Active Directory**</span><span class="sxs-lookup"><span data-stu-id="88e40-137">**Create a container with Active Directory support**</span></span>

    <https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/>

- <span data-ttu-id="88e40-138">**Zvýhodněné hybridní využití Azure licencování**</span><span class="sxs-lookup"><span data-stu-id="88e40-138">**Azure Hybrid Benefit licensing**</span></span>

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
><span data-ttu-id="88e40-139">[Předchozí](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)Další
>[](../walkthroughs-technical-get-started-overview.md)</span><span class="sxs-lookup"><span data-stu-id="88e40-139">[Previous](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[Next](../walkthroughs-technical-get-started-overview.md)</span></span>
