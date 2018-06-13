---
title: Obecné pokyny
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Obecné pokyny
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: ccaae99f4c46fe739041f9b9e907a702303e62f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592571"
---
# <a name="general-guidance"></a><span data-ttu-id="a190b-103">Obecné pokyny</span><span class="sxs-lookup"><span data-stu-id="a190b-103">General guidance</span></span>

<span data-ttu-id="a190b-104">Tato část obsahuje souhrn kdy zvolte .NET Core nebo rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a190b-104">This section provides a summary of when to choose .NET Core or .NET Framework.</span></span> <span data-ttu-id="a190b-105">Poskytujeme další podrobnosti o těchto možnostech v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="a190b-105">We provide more details about these choices in the sections that follow.</span></span>

<span data-ttu-id="a190b-106">.NET Core byste měli používat se systémem Linux nebo Windows kontejnery, pro aplikaci kontejnerizované server Docker při:</span><span class="sxs-lookup"><span data-stu-id="a190b-106">You should use .NET Core, with Linux or Windows Containers, for your containerized Docker server application when:</span></span>

-   <span data-ttu-id="a190b-107">Máte potřebám napříč platformami.</span><span class="sxs-lookup"><span data-stu-id="a190b-107">You have cross-platform needs.</span></span> <span data-ttu-id="a190b-108">Například chcete použít, Linux a Windows kontejnery.</span><span class="sxs-lookup"><span data-stu-id="a190b-108">For example, you want to use both Linux and Windows Containers.</span></span>

-   <span data-ttu-id="a190b-109">Architektuře aplikace je založena na mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="a190b-109">Your application architecture is based on microservices.</span></span>

-   <span data-ttu-id="a190b-110">Budete muset rychlého spuštění kontejnery a aby bylo možné snížit náklady na chcete malé nároky na kontejneru zajistit lepší hustotu nebo více kontejnerů na jednotku hardwaru.</span><span class="sxs-lookup"><span data-stu-id="a190b-110">You need to start containers fast and want a small footprint per container to achieve better density or more containers per hardware unit in order to lower your costs.</span></span>

<span data-ttu-id="a190b-111">Stručně řečeno když vytvoříte nové kontejnerizované aplikací .NET, měli byste zvážit .NET Core jako výchozí volba.</span><span class="sxs-lookup"><span data-stu-id="a190b-111">In short, when you create new containerized .NET applications, you should consider .NET Core as the default choice.</span></span> <span data-ttu-id="a190b-112">Má řadu výhod a nejlépe vyhovuje filosofie kontejnery a styl práci.</span><span class="sxs-lookup"><span data-stu-id="a190b-112">It has many benefits and fits best with the containers philosophy and style of working.</span></span>

<span data-ttu-id="a190b-113">Další výhodou používání .NET Core je, že můžete spustit vedle sebe verze rozhraní .NET pro aplikace v rámci stejného počítače.</span><span class="sxs-lookup"><span data-stu-id="a190b-113">An additional benefit of using .NET Core is that you can run side by side .NET versions for applications within the same machine.</span></span> <span data-ttu-id="a190b-114">Tuto výhodu je důležitější pro servery nebo virtuální počítače, které nepoužívají kontejnery, protože kontejnery izolovat verze rozhraní .NET, které aplikace potřebuje.</span><span class="sxs-lookup"><span data-stu-id="a190b-114">This benefit is more important for servers or VMs that do not use containers, because containers isolate the versions of .NET that the app needs.</span></span> <span data-ttu-id="a190b-115">(Za předpokladu, jsou kompatibilní s základního operačního systému.)</span><span class="sxs-lookup"><span data-stu-id="a190b-115">(As long as they are compatible with the underlying OS.)</span></span>

<span data-ttu-id="a190b-116">Rozhraní .NET Framework, byste měli použít s kontejnery Windows pro vaše kontejnerizované serverová aplikace Docker při:</span><span class="sxs-lookup"><span data-stu-id="a190b-116">You should use .NET Framework, with Windows Containers, for your containerized Docker server application when:</span></span>

-   <span data-ttu-id="a190b-117">Vaše aplikace právě používá rozhraní .NET Framework a má silné závislosti v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="a190b-117">Your application currently uses .NET Framework and has strong dependencies on Windows.</span></span>

-   <span data-ttu-id="a190b-118">Budete muset použít rozhraní API systému Windows, který nepodporuje .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a190b-118">You need to use Windows APIs that are not supported by .NET Core.</span></span>

-   <span data-ttu-id="a190b-119">Budete muset použít knihovny .NET třetích stran nebo balíčky NuGet, které nejsou k dispozici pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a190b-119">You need to use third-party .NET libraries or NuGet packages that are not available for .NET Core.</span></span>

<span data-ttu-id="a190b-120">Pomocí rozhraní .NET Framework na Docker lze vylepšit své zkušenosti nasazení minimalizovat problémy při nasazení.</span><span class="sxs-lookup"><span data-stu-id="a190b-120">Using .NET Framework on Docker can improve your deployment experiences by minimizing deployment issues.</span></span> <span data-ttu-id="a190b-121">To [ *"navýšení a posunutí" scénář* ](https://aka.ms/liftandshiftwithcontainersebook) je důležité pro containerizing starší aplikace, které byly původně vyvinuté s tradiční rozhraní .NET Framework jako webových formulářů ASP.NET, MVC webových aplikací nebo WCF ( Služby Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="a190b-121">This [*"lift and shift" scenario*](https://aka.ms/liftandshiftwithcontainersebook) is important for containerizing legacy applications that were originally developed with the traditional .NET Framework, like ASP.NET WebForms, MVC web apps or WCF (Windows Communication Foundation) services.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a190b-122">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="a190b-122">Additional resources</span></span>

-   <span data-ttu-id="a190b-123">**elektronická kniha: modernizovat existující aplikace rozhraní .NET Framework s Azure a Windows kontejnery**
    [*https://aka.ms/liftandshiftwithcontainersebook*](https://aka.ms/liftandshiftwithcontainersebook)</span><span class="sxs-lookup"><span data-stu-id="a190b-123">**e-book: Modernize existing .NET Framework applications with Azure and Windows Containers**
[*https://aka.ms/liftandshiftwithcontainersebook*](https://aka.ms/liftandshiftwithcontainersebook)</span></span>

-   <span data-ttu-id="a190b-124">**Ukázkové aplikace: modernizace starší verze webové aplikace ASP.NET pomocí Windows kontejnery**
    [*https://aka.ms/eshopmodernizing*](https://aka.ms/eshopmodernizing)</span><span class="sxs-lookup"><span data-stu-id="a190b-124">**Sample apps: Modernization of legacy ASP.NET web apps by using Windows Containers**
[*https://aka.ms/eshopmodernizing*](https://aka.ms/eshopmodernizing)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="a190b-125">[Předchozí] (index.md) [Další] (net – základní – kontejner scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="a190b-125">[Previous] (index.md) [Next] (net-core-container-scenarios.md)</span></span>
