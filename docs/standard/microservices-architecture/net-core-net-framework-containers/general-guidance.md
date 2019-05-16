---
title: Obecné pokyny
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Obecné pokyny
ms.date: 09/11/2018
ms.openlocfilehash: 0981cb16d5aa2036391caba0cf6ad3ac5c44ed6f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644138"
---
# <a name="general-guidance"></a><span data-ttu-id="91bc7-103">Obecné pokyny</span><span class="sxs-lookup"><span data-stu-id="91bc7-103">General guidance</span></span>

<span data-ttu-id="91bc7-104">Tato část obsahuje přehled kdy zvolit .NET Core nebo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="91bc7-104">This section provides a summary of when to choose .NET Core or .NET Framework.</span></span> <span data-ttu-id="91bc7-105">Společnost Microsoft poskytuje další podrobnosti o těchto možnostech v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="91bc7-105">We provide more details about these choices in the sections that follow.</span></span>

<span data-ttu-id="91bc7-106">Pro kontejnerizované aplikace Dockeru serveru byste měli použít .NET Core s Linuxem nebo Windows kontejnery, když:</span><span class="sxs-lookup"><span data-stu-id="91bc7-106">You should use .NET Core, with Linux or Windows Containers, for your containerized Docker server application when:</span></span>

- <span data-ttu-id="91bc7-107">Máte požadavky napříč platformami.</span><span class="sxs-lookup"><span data-stu-id="91bc7-107">You have cross-platform needs.</span></span> <span data-ttu-id="91bc7-108">Můžete třeba používat kontejnery Windows i Linux.</span><span class="sxs-lookup"><span data-stu-id="91bc7-108">For example, you want to use both Linux and Windows Containers.</span></span>

- <span data-ttu-id="91bc7-109">Vaše aplikace architektura je založená na mikroslužbách.</span><span class="sxs-lookup"><span data-stu-id="91bc7-109">Your application architecture is based on microservices.</span></span>

- <span data-ttu-id="91bc7-110">Potřebujete rychle se pusťte do kontejnerů a aby bylo možné snížit náklady na mají malé náklady na kontejner k dosažení vyšší hustotu nebo více kontejnerů na jednotku hardwaru.</span><span class="sxs-lookup"><span data-stu-id="91bc7-110">You need to start containers fast and want a small footprint per container to achieve better density or more containers per hardware unit in order to lower your costs.</span></span>

<span data-ttu-id="91bc7-111">Stručně řečeno když vytvoříte nový kontejnerizované aplikace .NET, měli byste zvážit .NET Core jako výchozí volbu.</span><span class="sxs-lookup"><span data-stu-id="91bc7-111">In short, when you create new containerized .NET applications, you should consider .NET Core as the default choice.</span></span> <span data-ttu-id="91bc7-112">Má mnoho výhod a nejlépe s filozofií kontejnery a stylu práce.</span><span class="sxs-lookup"><span data-stu-id="91bc7-112">It has many benefits and fits best with the containers philosophy and style of working.</span></span>

<span data-ttu-id="91bc7-113">Další výhodou používání .NET Core je, abyste mohli spouštět souběžně verze rozhraní .NET pro aplikace ve stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="91bc7-113">An additional benefit of using .NET Core is that you can run side by side .NET versions for applications within the same machine.</span></span> <span data-ttu-id="91bc7-114">Tuto výhodu je důležitější pro servery nebo virtuální počítače, které se nepoužívá kontejnery, protože kontejnery izolovat verze rozhraní .NET, které aplikace potřebuje.</span><span class="sxs-lookup"><span data-stu-id="91bc7-114">This benefit is more important for servers or VMs that do not use containers, because containers isolate the versions of .NET that the app needs.</span></span> <span data-ttu-id="91bc7-115">(Za předpokladu, že jsou kompatibilní s podkladovému operačnímu systému.)</span><span class="sxs-lookup"><span data-stu-id="91bc7-115">(As long as they are compatible with the underlying OS.)</span></span>

<span data-ttu-id="91bc7-116">Rozhraní .NET Framework byste měli použít své kontejnerizované aplikace Dockeru serveru při:</span><span class="sxs-lookup"><span data-stu-id="91bc7-116">You should use .NET Framework for your containerized Docker server application when:</span></span>

- <span data-ttu-id="91bc7-117">Vaše aplikace právě používá rozhraní .NET Framework a obsahuje silné závislosti na Windows.</span><span class="sxs-lookup"><span data-stu-id="91bc7-117">Your application currently uses .NET Framework and has strong dependencies on Windows.</span></span>

- <span data-ttu-id="91bc7-118">Budete muset použít rozhraní Windows API, která nepodporuje .NET Core.</span><span class="sxs-lookup"><span data-stu-id="91bc7-118">You need to use Windows APIs that are not supported by .NET Core.</span></span>

- <span data-ttu-id="91bc7-119">Budete muset použít .NET knihovny třetích stran nebo balíčky NuGet, které nejsou dostupné pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="91bc7-119">You need to use third-party .NET libraries or NuGet packages that are not available for .NET Core.</span></span>

<span data-ttu-id="91bc7-120">Pomocí rozhraní .NET Framework v Dockeru lze vylepšit prostředí pro vaše nasazení minimalizovat potíže s nasazením.</span><span class="sxs-lookup"><span data-stu-id="91bc7-120">Using .NET Framework on Docker can improve your deployment experiences by minimizing deployment issues.</span></span> <span data-ttu-id="91bc7-121">To ["metodou lift and shift" scénář](https://aka.ms/liftandshiftwithcontainersebook) je důležité pro uzavření do kontejneru starších aplikací, které byly původně vyvinuta tradiční rozhraní .NET Framework, jako je webových formulářů ASP.NET, MVC, web apps nebo WCF (Windows Communication Foundation ) služby.</span><span class="sxs-lookup"><span data-stu-id="91bc7-121">This ["lift and shift" scenario](https://aka.ms/liftandshiftwithcontainersebook) is important for containerizing legacy applications that were originally developed with the traditional .NET Framework, like ASP.NET WebForms, MVC web apps or WCF (Windows Communication Foundation) services.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="91bc7-122">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="91bc7-122">Additional resources</span></span>

- <span data-ttu-id="91bc7-123">**elektronická kniha: Modernizace stávajících aplikací rozhraní .NET Framework s využitím Azure a kontejnery Windows**</span><span class="sxs-lookup"><span data-stu-id="91bc7-123">**eBook: Modernize existing .NET Framework applications with Azure and Windows Containers**</span></span>  
    https://aka.ms/liftandshiftwithcontainersebook

- <span data-ttu-id="91bc7-124">**Ukázkové aplikace: Modernizace starší verze webových aplikací ASP.NET s využitím kontejnerů Windows**</span><span class="sxs-lookup"><span data-stu-id="91bc7-124">**Sample apps: Modernization of legacy ASP.NET web apps by using Windows Containers**</span></span>  
    https://aka.ms/eshopmodernizing

>[!div class="step-by-step"]
><span data-ttu-id="91bc7-125">[Předchozí](index.md)
>[další](net-core-container-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="91bc7-125">[Previous](index.md)
[Next](net-core-container-scenarios.md)</span></span>
