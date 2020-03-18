---
title: Obecné pokyny
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Obecné pokyny
ms.date: 09/11/2018
ms.openlocfilehash: 2fa66d7593b764a8df4d9acc20f93d3f8fb26174
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73089653"
---
# <a name="general-guidance"></a><span data-ttu-id="ce587-103">Obecné pokyny</span><span class="sxs-lookup"><span data-stu-id="ce587-103">General guidance</span></span>

<span data-ttu-id="ce587-104">Tato část obsahuje souhrn toho, kdy zvolit rozhraní .NET Core nebo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ce587-104">This section provides a summary of when to choose .NET Core or .NET Framework.</span></span> <span data-ttu-id="ce587-105">Další podrobnosti o těchto volbách poskytujeme v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="ce587-105">We provide more details about these choices in the sections that follow.</span></span>

<span data-ttu-id="ce587-106">Jádro .NET core s Linuxem nebo Kontejnery Windows byste měli použít pro kontejnerizovanou serverovou aplikaci Dockeru, když:</span><span class="sxs-lookup"><span data-stu-id="ce587-106">You should use .NET Core, with Linux or Windows Containers, for your containerized Docker server application when:</span></span>

- <span data-ttu-id="ce587-107">Máte potřeby napříč platformami.</span><span class="sxs-lookup"><span data-stu-id="ce587-107">You have cross-platform needs.</span></span> <span data-ttu-id="ce587-108">Například chcete použít linuxové i windows kontejnery.</span><span class="sxs-lookup"><span data-stu-id="ce587-108">For example, you want to use both Linux and Windows Containers.</span></span>

- <span data-ttu-id="ce587-109">Architektura aplikace je založena na mikroslužbách.</span><span class="sxs-lookup"><span data-stu-id="ce587-109">Your application architecture is based on microservices.</span></span>

- <span data-ttu-id="ce587-110">Musíte rychle spustit kontejnery a chcete malé rozměry na kontejner, abyste dosáhli lepší hustoty nebo více kontejnerů na hardwarovou jednotku, abyste snížili náklady.</span><span class="sxs-lookup"><span data-stu-id="ce587-110">You need to start containers fast and want a small footprint per container to achieve better density or more containers per hardware unit in order to lower your costs.</span></span>

<span data-ttu-id="ce587-111">Stručně řečeno, při vytváření nových kontejnerizovaných aplikací .NET byste měli považovat .NET Core jako výchozí volbu.</span><span class="sxs-lookup"><span data-stu-id="ce587-111">In short, when you create new containerized .NET applications, you should consider .NET Core as the default choice.</span></span> <span data-ttu-id="ce587-112">Má mnoho výhod a nejlépe se hodí k filozofii kontejnerů a stylu práce.</span><span class="sxs-lookup"><span data-stu-id="ce587-112">It has many benefits and fits best with the containers philosophy and style of working.</span></span>

<span data-ttu-id="ce587-113">Další výhodou použití rozhraní .NET Core je, že můžete spustit vedle sebe verze .NET pro aplikace v rámci stejného počítače.</span><span class="sxs-lookup"><span data-stu-id="ce587-113">An additional benefit of using .NET Core is that you can run side by side .NET versions for applications within the same machine.</span></span> <span data-ttu-id="ce587-114">Tato výhoda je důležitější pro servery nebo virtuální servery, které nepoužívají kontejnery, protože kontejnery izolovat verze rozhraní .NET, které aplikace potřebuje.</span><span class="sxs-lookup"><span data-stu-id="ce587-114">This benefit is more important for servers or VMs that do not use containers, because containers isolate the versions of .NET that the app needs.</span></span> <span data-ttu-id="ce587-115">(Pokud jsou kompatibilní s základním os.)</span><span class="sxs-lookup"><span data-stu-id="ce587-115">(As long as they are compatible with the underlying OS.)</span></span>

<span data-ttu-id="ce587-116">Rozhraní .NET Framework byste měli použít pro kontejnerizovanou serverovou aplikaci Dockeru, když:</span><span class="sxs-lookup"><span data-stu-id="ce587-116">You should use .NET Framework for your containerized Docker server application when:</span></span>

- <span data-ttu-id="ce587-117">Aplikace aktuálně používá rozhraní .NET Framework a má silné závislosti na systému Windows.</span><span class="sxs-lookup"><span data-stu-id="ce587-117">Your application currently uses .NET Framework and has strong dependencies on Windows.</span></span>

- <span data-ttu-id="ce587-118">Je třeba použít rozhraní API systému Windows, které nejsou podporovány .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ce587-118">You need to use Windows APIs that are not supported by .NET Core.</span></span>

- <span data-ttu-id="ce587-119">Musíte použít knihovny .NET jiných výrobců nebo balíčky NuGet, které nejsou k dispozici pro jádro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ce587-119">You need to use third-party .NET libraries or NuGet packages that are not available for .NET Core.</span></span>

<span data-ttu-id="ce587-120">Použití rozhraní .NET Framework v Dockeru může zlepšit vaše možnosti nasazení minimalizací problémů s nasazením.</span><span class="sxs-lookup"><span data-stu-id="ce587-120">Using .NET Framework on Docker can improve your deployment experiences by minimizing deployment issues.</span></span> <span data-ttu-id="ce587-121">Tento [scénář "lift and shift"](https://aka.ms/liftandshiftwithcontainersebook) je důležitý pro kontejnerizaci starších aplikací, které byly původně vyvinuty s tradiční rozhraní .NET Framework, jako jsou ASP.NET WebForms, MVC webové aplikace nebo WCF (Windows Communication Foundation) služby.</span><span class="sxs-lookup"><span data-stu-id="ce587-121">This ["lift and shift" scenario](https://aka.ms/liftandshiftwithcontainersebook) is important for containerizing legacy applications that were originally developed with the traditional .NET Framework, like ASP.NET WebForms, MVC web apps or WCF (Windows Communication Foundation) services.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="ce587-122">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="ce587-122">Additional resources</span></span>

- <span data-ttu-id="ce587-123">**E-kniha: Modernizace stávajících aplikací rozhraní .NET Framework pomocí kontejnerů Azure a Windows**</span><span class="sxs-lookup"><span data-stu-id="ce587-123">**E-book: Modernize existing .NET Framework applications with Azure and Windows Containers**</span></span>  
    https://aka.ms/liftandshiftwithcontainersebook

- <span data-ttu-id="ce587-124">**Ukázkové aplikace: Modernizace starších ASP.NET webových aplikací pomocí kontejnerů windows**</span><span class="sxs-lookup"><span data-stu-id="ce587-124">**Sample apps: Modernization of legacy ASP.NET web apps by using Windows Containers**</span></span>  
    https://aka.ms/eshopmodernizing

>[!div class="step-by-step"]
><span data-ttu-id="ce587-125">[Předchozí](index.md)
>[další](net-core-container-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="ce587-125">[Previous](index.md)
[Next](net-core-container-scenarios.md)</span></span>
