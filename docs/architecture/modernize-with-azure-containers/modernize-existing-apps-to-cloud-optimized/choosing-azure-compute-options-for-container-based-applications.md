---
title: Volba výpočetních platforem Azure pro aplikace založené na kontejnerech
description: Modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows | Výběr platforem Azure COMPUTE pro aplikace založené na kontejnerech
ms.date: 05/04/2018
ms.openlocfilehash: 079c9c5ca02b6dc75214d63cb59afdead03d3190
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737019"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="9b7f6-103">Volba výpočetních platforem Azure pro aplikace založené na kontejnerech</span><span class="sxs-lookup"><span data-stu-id="9b7f6-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="9b7f6-104">Jakmile jste si všimli, že jste si přečetli předchozí části, je Azure otevřeným cloudem, který nabízí víc možností.</span><span class="sxs-lookup"><span data-stu-id="9b7f6-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="9b7f6-105">Pro vaše potřeby můžete použít nejvhodnější, ale také si vyřadíme otázky týkající se produktu nebo technologie, které byste měli použít pro své aplikace v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="9b7f6-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="9b7f6-106">V rámci *výchozího* doporučení jsou tady uvedená hlavní kritéria, která jsou doporučena v těchto pokynech:</span><span class="sxs-lookup"><span data-stu-id="9b7f6-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

- <span data-ttu-id="9b7f6-107">**Jedna aplikace monolitické:** Zvolit Azure App Service</span><span class="sxs-lookup"><span data-stu-id="9b7f6-107">**Single monolithic app:** Choose Azure App Service</span></span>
- <span data-ttu-id="9b7f6-108">**N-vrstvá aplikace:** Vyberte orchestrace, jako je Azure Kubernetes Service (AKS), nebo App Service, pokud máte jednu nebo několik back-endové služeb.</span><span class="sxs-lookup"><span data-stu-id="9b7f6-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS) or App Service if you have a single or a few back-end services</span></span>
- <span data-ttu-id="9b7f6-109">**Mikroslužby:** Výběr AKS nebo Azure Web Apps pro kontejnery</span><span class="sxs-lookup"><span data-stu-id="9b7f6-109">**Microservices:** Choose AKS or Azure Web Apps for Containers</span></span>
- <span data-ttu-id="9b7f6-110">**Funkce bez serveru & obslužné rutiny událostí:** Zvolit Azure Functions</span><span class="sxs-lookup"><span data-stu-id="9b7f6-110">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
- <span data-ttu-id="9b7f6-111">**Velká škála dávek:** Zvolit Azure Batch</span><span class="sxs-lookup"><span data-stu-id="9b7f6-111">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="9b7f6-112">Toto doporučení je ale potřeba vzít s gesto roztažení prstůou sůl, protože výběr produktu bude záviset na potřebách a vlastnostech konkrétní aplikace.</span><span class="sxs-lookup"><span data-stu-id="9b7f6-112">However, this recommendation should be taken with a pinch of salt, as the product's selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="9b7f6-113">Ne všechny aplikace jsou stejné, i když zpočátku můžou vypadat podobné typy.</span><span class="sxs-lookup"><span data-stu-id="9b7f6-113">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="9b7f6-114">Po hlubší analýze potřeb aplikace může být vybraný produkt jiný.</span><span class="sxs-lookup"><span data-stu-id="9b7f6-114">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="9b7f6-115">Ale jako výchozí bod je dobré mít počáteční pokyny, ze kterých můžete začít vyhodnocovat a testovat na základě určité priority.</span><span class="sxs-lookup"><span data-stu-id="9b7f6-115">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="9b7f6-116">Na obrázku 1 vidíte rozpis různých druhů aplikací a jejich ideální scénáře hostování Azure.</span><span class="sxs-lookup"><span data-stu-id="9b7f6-116">In Figure 1, you can see a breakdown of different kinds of apps and their ideal Azure hosting scenarios.</span></span>

![Tabulka těch scénářů hostování Azure, které jsou nejvhodnější pro různé aplikace.](./media/choosing-azure-compute-options-for-container-based-applications/azure-hosting-scenarios-for-apps.png)

> [!div class="step-by-step"]
> <span data-ttu-id="9b7f6-118">[Předchozí](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [Další](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="9b7f6-118">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
