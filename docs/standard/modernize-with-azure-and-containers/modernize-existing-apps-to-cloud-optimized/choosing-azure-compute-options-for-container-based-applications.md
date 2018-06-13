---
title: Výběr platformy výpočtů Azure pro aplikace založené na kontejneru
description: Modernizovat existující aplikace .NET s kontejnery cloudu Azure a Windows | Výběr platformy výpočtů Azure pro aplikace založené na kontejneru
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/04/2018
ms.openlocfilehash: ebf022a52aaaf95ae335976f5e097921b0ac8006
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958242"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="6ebba-103">Výběr platformy výpočtů Azure pro aplikace založené na kontejneru</span><span class="sxs-lookup"><span data-stu-id="6ebba-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="6ebba-104">Jste si všimli po přečtení předchozí části, je Azure otevřete cloudu, která nabízí více možností.</span><span class="sxs-lookup"><span data-stu-id="6ebba-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="6ebba-105">Můžete použít bude nejlépe vyhovovat vašim potřebám, ale se navíc zobrazí otázky o jaké produkt nebo technologii byste měli použít pro kontejnerové aplikace.</span><span class="sxs-lookup"><span data-stu-id="6ebba-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="6ebba-106">Jako *výchozím* doporučení, toto je hlavní kritéria doporučení v tomto návodu:</span><span class="sxs-lookup"><span data-stu-id="6ebba-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

  - <span data-ttu-id="6ebba-107">**Jedna monolitický aplikace:** zvolte Azure App Service</span><span class="sxs-lookup"><span data-stu-id="6ebba-107">**Single monolithic app:** Choose Azure App Service</span></span>
  - <span data-ttu-id="6ebba-108">**Vícevrstvé aplikace:** orchestrators například Azure Kubernetes služby (AKS), Service Fabric n nebo služby App Service zvolte, pokud máte jeden nebo několik back endové služby</span><span class="sxs-lookup"><span data-stu-id="6ebba-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS), Service Fabric (SF) or App Service if you have a single or few back-end services</span></span>
  - <span data-ttu-id="6ebba-109">**Linux mikroslužeb:** zvolte AKS/Kubernetes</span><span class="sxs-lookup"><span data-stu-id="6ebba-109">**Linux microservices:** Choose AKS/Kubernetes</span></span>
  - <span data-ttu-id="6ebba-110">**Windows mikroslužeb:** zvolte Service Fabric</span><span class="sxs-lookup"><span data-stu-id="6ebba-110">**Windows microservices:** Choose Service Fabric</span></span>
  - <span data-ttu-id="6ebba-111">**Bez serveru funkce & obslužné rutiny událostí:** zvolte Azure Functions</span><span class="sxs-lookup"><span data-stu-id="6ebba-111">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
  - <span data-ttu-id="6ebba-112">**Ve velkém měřítku Batch:** zvolte Azure Batch</span><span class="sxs-lookup"><span data-stu-id="6ebba-112">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="6ebba-113">Toto doporučení však by měla být provedena s roztahováním salt, protože produktu výběr bude záviset na konkrétní aplikaci požadavky a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6ebba-113">However, this recommendation should be taken with a pinch of salt, as the product’s selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="6ebba-114">Ne všechny aplikace jsou stejné i v případě začátku může vypadat podobně jako typy.</span><span class="sxs-lookup"><span data-stu-id="6ebba-114">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="6ebba-115">Po dokončení hlubší analýzy potřebám aplikace může být produktu vybrané jiné.</span><span class="sxs-lookup"><span data-stu-id="6ebba-115">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="6ebba-116">Ale, jako výchozí bod, je vhodné mít počáteční pokyny, ze které můžete spustit vyhodnocování a testování podle určité priority.</span><span class="sxs-lookup"><span data-stu-id="6ebba-116">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="6ebba-117">V následující obrázek můžete analyzovat více globální při podrobné rozhodovací tabulky.</span><span class="sxs-lookup"><span data-stu-id="6ebba-117">In the next figure, you can analyze a more global while detailed decision table.</span></span>

![](./media/image8.5.png)

<span data-ttu-id="6ebba-118">Všimněte si jak základní operační systém (Windows vs. Linux) může být také rozhodnutí faktor jsou některé orchestrators vyspělá kontejnerům Linux a dalších kontejnerům systému Windows.</span><span class="sxs-lookup"><span data-stu-id="6ebba-118">Notice how the underlying OS (Windows vs. Linux) can also be a decision factor as some orchestrators are more mature on Linux containers and other on Windows containers.</span></span> <span data-ttu-id="6ebba-119">Pro instanci kontejnery Linux jsou velmi vyspělá v Kubernetes (AKS v Azure) ale méně vyspělá v Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="6ebba-119">For instance, Linux containers are very mature in Kubernetes (AKS in Azure) but less mature on Service Fabric.</span></span> <span data-ttu-id="6ebba-120">Na druhé straně kontejnery Windows jsou víc vyspělých v Service Fabric (vydané v květnu 2017) a méně vyspělá v AKS.</span><span class="sxs-lookup"><span data-stu-id="6ebba-120">On the other hand, Windows Containers are more mature in Service Fabric (released in May 2017) and less mature in AKS.</span></span>

<span data-ttu-id="6ebba-121">Ale tyto rozdíly v dospělosti operačního systému bude v budoucnu objevovat a více platforem budou mít porovnatelný z hlediska vyspělosti operačního systému a rozhodnutí budou obsahovat další informace o předvolby podle konkrétních příznaků, může být nutné aplikaci nebo v závislosti na každou platformu ekosystém z důvodů.</span><span class="sxs-lookup"><span data-stu-id="6ebba-121">However, those differences in OS maturity will fade in the future and multiple platforms will have comparable OS maturity and the decision will lay more on preferences based on specific features your application might need or based on each platform's ecosystem reasons.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="6ebba-122">[Předchozí](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[další](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="6ebba-122">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
