---
title: Scénáře migrace do hybridního cloudu
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a Windows kontejnery | Migrace na scénáři s hybridními cloudy
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: b04c6edecf5b63f191cb2e0f808fb1d0f801d0a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936722"
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a><span data-ttu-id="33d9a-103">Scénáře migrace do hybridního cloudu</span><span class="sxs-lookup"><span data-stu-id="33d9a-103">Migrate to hybrid cloud scenarios</span></span>

<span data-ttu-id="33d9a-104">Některé organizace a podniky nemůžete migrovat některé ze svých aplikací do veřejných cloudů, jako je například Microsoft Azure nebo jiného veřejného cloudu kvůli předpisy nebo vlastní zásady.</span><span class="sxs-lookup"><span data-stu-id="33d9a-104">Some organizations and enterprises can't migrate some of their applications to public clouds like Microsoft Azure or any other public cloud due to regulations or their own policies.</span></span> <span data-ttu-id="33d9a-105">Je ale pravděpodobné, že každá organizace může mít užitek z některých aplikací ve veřejném cloudu a dalších aplikací v místním prostředí s.</span><span class="sxs-lookup"><span data-stu-id="33d9a-105">However, it's likely that any organization might benefit from having some of their applications in the public cloud and other applications on-premises.</span></span> <span data-ttu-id="33d9a-106">Ale smíšeném prostředí může vést k nadměrné složitosti v prostředí kvůli různé platformy a technologie používané ve veřejných cloudech a v místních prostředích.</span><span class="sxs-lookup"><span data-stu-id="33d9a-106">But a mixed environment can lead to excessive complexity in environments due to different platforms and technologies used in public clouds versus on-premises environments.</span></span>

<span data-ttu-id="33d9a-107">Společnost Microsoft poskytuje nejlepší hybridní cloudové řešení, jeden ve kterém můžete optimalizovat stávající prostředky místní a ve veřejném cloudu, zatímco zajistit konzistenci v Azure hybridního cloudu.</span><span class="sxs-lookup"><span data-stu-id="33d9a-107">Microsoft provides the best hybrid cloud solution, one in which you can optimize your existing assets on-premises and in the public cloud, while you ensure consistency in an Azure hybrid cloud.</span></span> <span data-ttu-id="33d9a-108">Můžete maximalizovat stávající dovednosti a získejte flexibilní a Unifikovaný přístup k vytváření aplikací, které můžou běžet v cloudu nebo místně, díky Azure Stack (v místním prostředí) a Azure (veřejný cloud).</span><span class="sxs-lookup"><span data-stu-id="33d9a-108">You can maximize existing skills, and get a flexible, unified approach to building apps that can run in the cloud or on-premises, thanks to Azure Stack (on-premises) and Azure (public cloud).</span></span>

<span data-ttu-id="33d9a-109">Při rozhodování o zabezpečení, můžete centralizovat správu a zabezpečení napříč hybridním cloudu.</span><span class="sxs-lookup"><span data-stu-id="33d9a-109">When it comes to security, you can centralize management and security across your hybrid cloud.</span></span> <span data-ttu-id="33d9a-110">Můžete mít kontrolu nad všemi prostředky z vašeho datového centra do cloudu a tím, že poskytuje jednotné přihlašování k místním a cloudovým aplikacím.</span><span class="sxs-lookup"><span data-stu-id="33d9a-110">You can get control over all assets, from your datacenter to the cloud, by providing single sign-on to on-premises and cloud apps.</span></span> <span data-ttu-id="33d9a-111">Můžete dosáhnout pomocí rozšíření služby Active Directory na hybridní cloud a s využitím správy identit.</span><span class="sxs-lookup"><span data-stu-id="33d9a-111">You accomplish this by extending Active Directory to a hybrid cloud, and by using identity management.</span></span>

<span data-ttu-id="33d9a-112">Nakonec můžete distribuovat a analyzovat data bez problémů, použít stejné dotazovací jazyky pro cloudové a místní prostředky a analýz a obsáhlého learningu v Azure obohatíte vaše data bez ohledu na jeho zdroj.</span><span class="sxs-lookup"><span data-stu-id="33d9a-112">Finally, you can distribute and analyze data seamlessly, use the same query languages for cloud and on-premises assets, and apply analytics and deep learning in Azure to enrich your data, regardless of its source.</span></span>

## <a name="azure-stack"></a><span data-ttu-id="33d9a-113">Azure Stack</span><span class="sxs-lookup"><span data-stu-id="33d9a-113">Azure Stack</span></span>

<span data-ttu-id="33d9a-114">Azure Stack je hybridní Cloudová platforma, která umožňuje poskytovat služby Azure z datového centra vaší organizace.</span><span class="sxs-lookup"><span data-stu-id="33d9a-114">Azure Stack is a hybrid cloud platform that lets you deliver Azure services from your organization's datacenter.</span></span> <span data-ttu-id="33d9a-115">Azure Stack je navržena pro podporu nové možnosti pro moderní aplikace v klíčových scénářů, jako je edge a nepřipojené prostředí nebo specifické požadavky zabezpečení a dodržování předpisů na schůzku.</span><span class="sxs-lookup"><span data-stu-id="33d9a-115">Azure Stack is designed to support new options for your modern applications in key scenarios, like edge and unconnected environments, or meeting specific security and compliance requirements.</span></span>

<span data-ttu-id="33d9a-116">Obrázek 4 – 13 ukazuje přehled skutečně hybridní Cloudová platforma, která nabízí Microsoft.</span><span class="sxs-lookup"><span data-stu-id="33d9a-116">Figure 4-13 shows an overview of the true hybrid cloud platform that Microsoft offers.</span></span>

![Hybridní Cloudová platforma Microsoftu pomocí služby Azure Stack a Azure](./media/image13.jpg)

> <span data-ttu-id="33d9a-118">**Obrázek 4 – 13.**</span><span class="sxs-lookup"><span data-stu-id="33d9a-118">**Figure 4-13.**</span></span> <span data-ttu-id="33d9a-119">Hybridní Cloudová platforma Microsoftu pomocí služby Azure Stack a Azure</span><span class="sxs-lookup"><span data-stu-id="33d9a-119">Microsoft hybrid cloud platform with Azure Stack and Azure</span></span>

<span data-ttu-id="33d9a-120">Azure Stack se nabízí ve dvou možnosti nasazení podle svých potřeb:</span><span class="sxs-lookup"><span data-stu-id="33d9a-120">Azure Stack is offered in two deployment options, to meet your needs:</span></span>

- <span data-ttu-id="33d9a-121">Integrované systémy pro službu Azure Stack</span><span class="sxs-lookup"><span data-stu-id="33d9a-121">Azure Stack integrated systems</span></span>

- <span data-ttu-id="33d9a-122">Vývojová sada pro Azure Stack</span><span class="sxs-lookup"><span data-stu-id="33d9a-122">Azure Stack Development Kit</span></span>

### <a name="azure-stack-integrated-systems"></a><span data-ttu-id="33d9a-123">Integrované systémy pro službu Azure Stack</span><span class="sxs-lookup"><span data-stu-id="33d9a-123">Azure Stack integrated systems</span></span>

<span data-ttu-id="33d9a-124">Azure Stack integrované systémy jsou nabízeny Díky partnerství Microsoftu a hardwarových partnerů.</span><span class="sxs-lookup"><span data-stu-id="33d9a-124">Azure Stack integrated systems are offered through a partnership of Microsoft and hardware partners.</span></span> <span data-ttu-id="33d9a-125">Partnerství vytvoří řešení, které nabízí cloud tempem inovací vyrovnávaném pomocí jednoduchost ve správě.</span><span class="sxs-lookup"><span data-stu-id="33d9a-125">The partnership creates a solution that offers cloud-paced innovation that is balanced with simplicity in management.</span></span> <span data-ttu-id="33d9a-126">Protože Azure Stack se nabízí jako integrovaný systém softwaru a hardwaru, získáte úroveň flexibility a kontroly, při přijetí stále inovace v cloudu.</span><span class="sxs-lookup"><span data-stu-id="33d9a-126">Because Azure Stack is offered as an integrated system of hardware and software, you get the right amount of flexibility and control, while still adopting innovation from the cloud.</span></span> <span data-ttu-id="33d9a-127">Systémy ve službě Azure Stack integrované velikosti od 4 do 12 uzlů v rozsahu a společně podporuje hardwarových partnerů a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="33d9a-127">Azure Stack integrated systems range in size from 4 to 12 nodes, and are jointly supported by the hardware partner and Microsoft.</span></span> <span data-ttu-id="33d9a-128">Implementace nové scénáře pro vaše produkční úlohy pomocí integrované systémy Azure Stack.</span><span class="sxs-lookup"><span data-stu-id="33d9a-128">Use Azure Stack integrated systems to implement new scenarios for your production workloads.</span></span>

### <a name="azure-stack-development-kit"></a><span data-ttu-id="33d9a-129">Vývojová sada pro Azure Stack</span><span class="sxs-lookup"><span data-stu-id="33d9a-129">Azure Stack Development Kit</span></span>

<span data-ttu-id="33d9a-130">Microsoft Azure Stack Development Kit je jedním uzlem nasazení služby Azure Stack, který můžete použít k vyhodnocení a další informace o službě Azure Stack.</span><span class="sxs-lookup"><span data-stu-id="33d9a-130">Microsoft Azure Stack Development Kit is a single-node deployment of Azure Stack, which you can use to evaluate and learn about Azure Stack.</span></span> <span data-ttu-id="33d9a-131">Jako prostředí pro vývojáře, kde můžete při vývoji využít rozhraní API a nabízí nástroje, které jsou konzistentní s Azure můžete také použít Azure Stack Development Kit.</span><span class="sxs-lookup"><span data-stu-id="33d9a-131">You can also use Azure Stack Development Kit as a developer environment, where you can develop using APIs and tooling that are consistent with Azure.</span></span> <span data-ttu-id="33d9a-132">Azure Stack Development Kit není určena pro použití jako v provozním prostředí.</span><span class="sxs-lookup"><span data-stu-id="33d9a-132">Azure Stack Development Kit is not intended to be used as a production environment.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="33d9a-133">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="33d9a-133">Additional resources</span></span>

- <span data-ttu-id="33d9a-134">**Azure hybrid cloud**</span><span class="sxs-lookup"><span data-stu-id="33d9a-134">**Azure hybrid cloud**</span></span>

    <https://azure.microsoft.com/overview/hybrid-cloud/>

- <span data-ttu-id="33d9a-135">**Azure Stack**</span><span class="sxs-lookup"><span data-stu-id="33d9a-135">**Azure Stack**</span></span>

    <https://azure.microsoft.com/overview/azure-stack/>

- <span data-ttu-id="33d9a-136">**Účty služby Active Directory pro kontejnery Windows**</span><span class="sxs-lookup"><span data-stu-id="33d9a-136">**Active Directory Service Accounts for Windows Containers**</span></span>

    <https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts>

- <span data-ttu-id="33d9a-137">**Vytvořit kontejner s podporou služby Active Directory**</span><span class="sxs-lookup"><span data-stu-id="33d9a-137">**Create a container with Active Directory support**</span></span>

    <https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/>

- <span data-ttu-id="33d9a-138">**Licencování programu Azure Hybrid Benefit**</span><span class="sxs-lookup"><span data-stu-id="33d9a-138">**Azure Hybrid Benefit licensing**</span></span>

    <https://azure.microsoft.com/pricing/hybrid-benefit/>

>[!div class="step-by-step"]
><span data-ttu-id="33d9a-139">[Předchozí](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
>[další](../walkthroughs-technical-get-started-overview.md)</span><span class="sxs-lookup"><span data-stu-id="33d9a-139">[Previous](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[Next](../walkthroughs-technical-get-started-overview.md)</span></span>
