---
title: Volba výpočetních platforem Azure pro aplikace založené na kontejnerech
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a Windows kontejnery | Výběr platformy výpočetní prostředky Azure pro aplikace založené na kontejnerech
ms.date: 05/04/2018
ms.openlocfilehash: 28e103c67f47d63582384c9ab468a5f631b5ce9e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65638982"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="af715-103">Volba výpočetních platforem Azure pro aplikace založené na kontejnerech</span><span class="sxs-lookup"><span data-stu-id="af715-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="af715-104">Protože jste si všimli po přečtení v předchozích částech, Azure je otevřete cloud, který nabízí více možností.</span><span class="sxs-lookup"><span data-stu-id="af715-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="af715-105">Můžete použít nejlépe vyhovovat vašim potřebám, ale se navíc zobrazí otázky o tom, jaký produkt/technologie byste měli použít pro své kontejnerizované aplikace.</span><span class="sxs-lookup"><span data-stu-id="af715-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="af715-106">Jako *výchozím* doporučení, tady je hlavním kritériem doporučení v tomto dokumentu:</span><span class="sxs-lookup"><span data-stu-id="af715-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

- <span data-ttu-id="af715-107">**Monolitické aplikace s jedním:** Zvolte Azure App Service</span><span class="sxs-lookup"><span data-stu-id="af715-107">**Single monolithic app:** Choose Azure App Service</span></span>
- <span data-ttu-id="af715-108">**N-vrstvé aplikace:** Pokud máte jednu nebo několik back endovým službám, zvolte orchestrátorů, jako je například Azure Kubernetes Service (AKS), Service Fabric (SF) nebo služby App Service</span><span class="sxs-lookup"><span data-stu-id="af715-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS), Service Fabric (SF) or App Service if you have a single or few back-end services</span></span>
- <span data-ttu-id="af715-109">**Mikroslužby Linux:** Zvolte AKS/Kubernetes</span><span class="sxs-lookup"><span data-stu-id="af715-109">**Linux microservices:** Choose AKS/Kubernetes</span></span>
- <span data-ttu-id="af715-110">**Mikroslužby Windows:** Zvolte Service Fabric</span><span class="sxs-lookup"><span data-stu-id="af715-110">**Windows microservices:** Choose Service Fabric</span></span>
- <span data-ttu-id="af715-111">**Funkce bez serveru a obslužné rutiny události:** Zvolte Azure Functions</span><span class="sxs-lookup"><span data-stu-id="af715-111">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
- <span data-ttu-id="af715-112">**Ve velkém měřítku Batch:** Zvolte Azure Batch</span><span class="sxs-lookup"><span data-stu-id="af715-112">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="af715-113">Toto doporučení by však provést s roztažením o hodnota salt, jako výběr produktu, bude záviset na konkrétní aplikaci požadavky a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="af715-113">However, this recommendation should be taken with a pinch of salt, as the product’s selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="af715-114">Ne všechny aplikace jsou stejné, i když zpočátku může vypadat podobně jako typy.</span><span class="sxs-lookup"><span data-stu-id="af715-114">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="af715-115">Po dokončení hlubší analýzy potřeby aplikace mohou být odlišná vybranému produktu.</span><span class="sxs-lookup"><span data-stu-id="af715-115">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="af715-116">Ale jako výchozí bod, je dobré si základní pokyny z kde začít, vyhodnocování a testování na základě určitých priority.</span><span class="sxs-lookup"><span data-stu-id="af715-116">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="af715-117">Následující obrázek můžete analyzovat více globální při podrobné rozhodovací tabulky.</span><span class="sxs-lookup"><span data-stu-id="af715-117">In the next figure, you can analyze a more global while detailed decision table.</span></span>

![](./media/image8.5.png)

<span data-ttu-id="af715-118">Všimněte si, že jak základní operační systém (Windows vs. Linux) může být také faktor rozhodnutí jsou některé zvolené orchestrátory až po zralé kontejnerům Linuxu a dalších v kontejnerech Windows.</span><span class="sxs-lookup"><span data-stu-id="af715-118">Notice how the underlying OS (Windows vs. Linux) can also be a decision factor as some orchestrators are more mature on Linux containers and other on Windows containers.</span></span> <span data-ttu-id="af715-119">Například kontejnery Linuxu jsou velmi až po zralé v Kubernetes (AKS v Azure) ale méně až po zralé na platformě Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="af715-119">For instance, Linux containers are very mature in Kubernetes (AKS in Azure) but less mature on Service Fabric.</span></span> <span data-ttu-id="af715-120">Na druhé straně jsou kontejnery Windows vyspělejší v Service Fabric (vydané spolu. května 2017) a méně až po zralé ve službě AKS.</span><span class="sxs-lookup"><span data-stu-id="af715-120">On the other hand, Windows Containers are more mature in Service Fabric (released in May 2017) and less mature in AKS.</span></span>

<span data-ttu-id="af715-121">Však bude v budoucnu fade těchto rozdílů v OS vyspělosti a více platforem budou mít srovnatelné vyspělosti operačního systému a rozhodnutí budou obsahovat další informace o předvolby podle konkrétních příznaků, které vaše aplikace může být nutné nebo založené na každou platformu ekosystém z důvodů.</span><span class="sxs-lookup"><span data-stu-id="af715-121">However, those differences in OS maturity will fade in the future and multiple platforms will have comparable OS maturity and the decision will lay more on preferences based on specific features your application might need or based on each platform's ecosystem reasons.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="af715-122">[Předchozí](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [další](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="af715-122">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
