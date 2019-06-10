---
title: Volba výpočetních platforem Azure pro aplikace založené na kontejnerech
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a Windows kontejnery | Výběr platformy výpočetní prostředky Azure pro aplikace založené na kontejnerech
ms.date: 05/04/2018
ms.openlocfilehash: d91cd279402dc24beb5f766c06cb85ac8d74f482
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758829"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="95797-103">Volba výpočetních platforem Azure pro aplikace založené na kontejnerech</span><span class="sxs-lookup"><span data-stu-id="95797-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="95797-104">Protože jste si všimli po přečtení v předchozích částech, Azure je otevřete cloud, který nabízí více možností.</span><span class="sxs-lookup"><span data-stu-id="95797-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="95797-105">Můžete použít nejlépe vyhovovat vašim potřebám, ale se navíc zobrazí otázky o tom, jaký produkt/technologie byste měli použít pro své kontejnerizované aplikace.</span><span class="sxs-lookup"><span data-stu-id="95797-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="95797-106">Jako *výchozím* doporučení, tady je hlavním kritériem doporučení v tomto dokumentu:</span><span class="sxs-lookup"><span data-stu-id="95797-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

- <span data-ttu-id="95797-107">**Monolitické aplikace s jedním:** Zvolte Azure App Service</span><span class="sxs-lookup"><span data-stu-id="95797-107">**Single monolithic app:** Choose Azure App Service</span></span>
- <span data-ttu-id="95797-108">**N-vrstvé aplikace:** Pokud máte jednu nebo několik back endovým službám, zvolte orchestrátorů, jako je Azure Kubernetes Service (AKS) nebo služby App Service</span><span class="sxs-lookup"><span data-stu-id="95797-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS)or App Service if you have a single or few back-end services</span></span>
- <span data-ttu-id="95797-109">**Mikroslužby Linux:** Zvolte AKS/Kubernetes</span><span class="sxs-lookup"><span data-stu-id="95797-109">**Linux microservices:** Choose AKS/Kubernetes</span></span>
- <span data-ttu-id="95797-110">**Mikroslužby Windows:** Zvolte Azure Web Apps for Containers</span><span class="sxs-lookup"><span data-stu-id="95797-110">**Windows microservices:** Choose Azure Web Apps for Containers</span></span>
- <span data-ttu-id="95797-111">**Funkce bez serveru a obslužné rutiny události:** Zvolte Azure Functions</span><span class="sxs-lookup"><span data-stu-id="95797-111">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
- <span data-ttu-id="95797-112">**Ve velkém měřítku Batch:** Zvolte Azure Batch</span><span class="sxs-lookup"><span data-stu-id="95797-112">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="95797-113">Toto doporučení by však provést s roztažením o hodnota salt, jako výběr produktu, bude záviset na konkrétní aplikaci požadavky a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="95797-113">However, this recommendation should be taken with a pinch of salt, as the product’s selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="95797-114">Ne všechny aplikace jsou stejné, i když zpočátku může vypadat podobně jako typy.</span><span class="sxs-lookup"><span data-stu-id="95797-114">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="95797-115">Po dokončení hlubší analýzy potřeby aplikace mohou být odlišná vybranému produktu.</span><span class="sxs-lookup"><span data-stu-id="95797-115">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="95797-116">Ale jako výchozí bod, je dobré si základní pokyny z kde začít, vyhodnocování a testování na základě určitých priority.</span><span class="sxs-lookup"><span data-stu-id="95797-116">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="95797-117">Následující obrázek můžete zobrazit rozpis různých druhů aplikací a jejich ideální hostování scénáře Azure.</span><span class="sxs-lookup"><span data-stu-id="95797-117">In the next figure, you can see a breakdown of different kinds of apps and their ideal Azure hosting scenarios.</span></span>

![](./media/image8.5.png)

> [!div class="step-by-step"]
> <span data-ttu-id="95797-118">[Předchozí](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [další](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="95797-118">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
