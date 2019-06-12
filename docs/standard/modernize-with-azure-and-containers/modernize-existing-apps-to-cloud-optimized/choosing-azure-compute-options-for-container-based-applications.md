---
title: Volba výpočetních platforem Azure pro aplikace založené na kontejnerech
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a Windows kontejnery | Výběr platformy výpočetní prostředky Azure pro aplikace založené na kontejnerech
ms.date: 05/04/2018
ms.openlocfilehash: 64ae542e006bf7a5d7a0be08fe1cff9770552a77
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833857"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="5d11a-103">Volba výpočetních platforem Azure pro aplikace založené na kontejnerech</span><span class="sxs-lookup"><span data-stu-id="5d11a-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="5d11a-104">Protože jste si všimli po přečtení v předchozích částech, Azure je otevřete cloud, který nabízí více možností.</span><span class="sxs-lookup"><span data-stu-id="5d11a-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="5d11a-105">Můžete použít nejlépe vyhovovat vašim potřebám, ale se navíc zobrazí otázky o tom, jaký produkt/technologie byste měli použít pro své kontejnerizované aplikace.</span><span class="sxs-lookup"><span data-stu-id="5d11a-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="5d11a-106">Jako *výchozím* doporučení, tady je hlavním kritériem doporučení v tomto dokumentu:</span><span class="sxs-lookup"><span data-stu-id="5d11a-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

- <span data-ttu-id="5d11a-107">**Monolitické aplikace s jedním:** Zvolte Azure App Service</span><span class="sxs-lookup"><span data-stu-id="5d11a-107">**Single monolithic app:** Choose Azure App Service</span></span>
- <span data-ttu-id="5d11a-108">**N-vrstvé aplikace:** Pokud máte jednu nebo několik back endovým službám, zvolte orchestrátorů, jako je Azure Kubernetes Service (AKS) nebo služby App Service</span><span class="sxs-lookup"><span data-stu-id="5d11a-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS)or App Service if you have a single or few back-end services</span></span>
- <span data-ttu-id="5d11a-109">**Mikroslužby:** Zvolte AKS nebo Azure Web Apps for Containers</span><span class="sxs-lookup"><span data-stu-id="5d11a-109">**Microservices:** Choose AKS or Azure Web Apps for Containers</span></span>
- <span data-ttu-id="5d11a-110">**Funkce bez serveru a obslužné rutiny události:** Zvolte Azure Functions</span><span class="sxs-lookup"><span data-stu-id="5d11a-110">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
- <span data-ttu-id="5d11a-111">**Ve velkém měřítku Batch:** Zvolte Azure Batch</span><span class="sxs-lookup"><span data-stu-id="5d11a-111">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="5d11a-112">Toto doporučení by však provést s roztažením o hodnota salt, jako výběr produktu, bude záviset na konkrétní aplikaci požadavky a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5d11a-112">However, this recommendation should be taken with a pinch of salt, as the product’s selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="5d11a-113">Ne všechny aplikace jsou stejné, i když zpočátku může vypadat podobně jako typy.</span><span class="sxs-lookup"><span data-stu-id="5d11a-113">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="5d11a-114">Po dokončení hlubší analýzy potřeby aplikace mohou být odlišná vybranému produktu.</span><span class="sxs-lookup"><span data-stu-id="5d11a-114">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="5d11a-115">Ale jako výchozí bod, je dobré si základní pokyny z kde začít, vyhodnocování a testování na základě určitých priority.</span><span class="sxs-lookup"><span data-stu-id="5d11a-115">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="5d11a-116">Následující obrázek můžete zobrazit rozpis různých druhů aplikací a jejich ideální hostování scénáře Azure.</span><span class="sxs-lookup"><span data-stu-id="5d11a-116">In the next figure, you can see a breakdown of different kinds of apps and their ideal Azure hosting scenarios.</span></span>

![](./media/image8.5.png)

> [!div class="step-by-step"]
> <span data-ttu-id="5d11a-117">[Předchozí](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [další](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="5d11a-117">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
