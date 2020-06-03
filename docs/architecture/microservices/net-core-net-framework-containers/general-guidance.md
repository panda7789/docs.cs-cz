---
title: Obecné pokyny
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Obecné pokyny
ms.date: 09/11/2018
ms.openlocfilehash: 6e63d7804abc1703f17378584d58d66a933022c7
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/03/2020
ms.locfileid: "84306874"
---
# <a name="general-guidance"></a><span data-ttu-id="aa86d-103">Obecné pokyny</span><span class="sxs-lookup"><span data-stu-id="aa86d-103">General guidance</span></span>

<span data-ttu-id="aa86d-104">V této části najdete přehled, kdy zvolit rozhraní .NET Core nebo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aa86d-104">This section provides a summary of when to choose .NET Core or .NET Framework.</span></span> <span data-ttu-id="aa86d-105">Další podrobnosti o těchto volbách poskytujeme v níže uvedených částech.</span><span class="sxs-lookup"><span data-stu-id="aa86d-105">We provide more details about these choices in the sections that follow.</span></span>

<span data-ttu-id="aa86d-106">Použijte .NET Core s kontejnery Linux nebo Windows pro vaši kontejnerovou aplikaci Docker, která je v těchto případech:</span><span class="sxs-lookup"><span data-stu-id="aa86d-106">Use .NET Core, with Linux or Windows Containers, for your containerized Docker server application when:</span></span>

- <span data-ttu-id="aa86d-107">Máte různé požadavky na více platforem.</span><span class="sxs-lookup"><span data-stu-id="aa86d-107">You have cross-platform needs.</span></span> <span data-ttu-id="aa86d-108">Například chcete použít kontejnery Linux i Windows.</span><span class="sxs-lookup"><span data-stu-id="aa86d-108">For example, you want to use both Linux and Windows Containers.</span></span>

- <span data-ttu-id="aa86d-109">Architektura vaší aplikace je založena na mikroslužbách.</span><span class="sxs-lookup"><span data-stu-id="aa86d-109">Your application architecture is based on microservices.</span></span>

- <span data-ttu-id="aa86d-110">Je potřeba začít kontejnery rychle a chtít malé nároky na kontejner, abyste dosáhli lepší hustoty nebo většího počtu kontejnerů na jednotku hardwaru za účelem snížení nákladů.</span><span class="sxs-lookup"><span data-stu-id="aa86d-110">You need to start containers fast and want a small footprint per container to achieve better density or more containers per hardware unit in order to lower your costs.</span></span>

<span data-ttu-id="aa86d-111">V krátké době, kdy vytváříte nové kontejnery aplikací .NET, byste měli zvážit jako výchozí volbu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aa86d-111">In short, when you create new containerized .NET applications, you should consider .NET Core as the default choice.</span></span> <span data-ttu-id="aa86d-112">Má spoustu výhod a nejlépe vyhovuje kontejnerům filozofie a stylu práce.</span><span class="sxs-lookup"><span data-stu-id="aa86d-112">It has many benefits and fits best with the containers philosophy and style of working.</span></span>

<span data-ttu-id="aa86d-113">Další výhodou používání .NET Core je, že pro aplikace ve stejném počítači můžete spouštět souběžné verze .NET.</span><span class="sxs-lookup"><span data-stu-id="aa86d-113">An additional benefit of using .NET Core is that you can run side by side .NET versions for applications within the same machine.</span></span> <span data-ttu-id="aa86d-114">Tato výhoda je důležitější pro servery nebo virtuální počítače, které nepoužívají kontejnery, protože kontejnery izolují verze rozhraní .NET, které aplikace potřebuje.</span><span class="sxs-lookup"><span data-stu-id="aa86d-114">This benefit is more important for servers or VMs that do not use containers, because containers isolate the versions of .NET that the app needs.</span></span> <span data-ttu-id="aa86d-115">(Pokud jsou kompatibilní s podkladovým operačním systémem.)</span><span class="sxs-lookup"><span data-stu-id="aa86d-115">(As long as they are compatible with the underlying OS.)</span></span>

<span data-ttu-id="aa86d-116">Použijte .NET Framework pro svou kontejnerovou aplikaci Docker Server, když:</span><span class="sxs-lookup"><span data-stu-id="aa86d-116">Use .NET Framework for your containerized Docker server application when:</span></span>

- <span data-ttu-id="aa86d-117">Vaše aplikace aktuálně používá .NET Framework a má silné závislosti v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="aa86d-117">Your application currently uses .NET Framework and has strong dependencies on Windows.</span></span>

- <span data-ttu-id="aa86d-118">Je nutné použít rozhraní API systému Windows, která nejsou podporována rozhraním .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aa86d-118">You need to use Windows APIs that are not supported by .NET Core.</span></span>

- <span data-ttu-id="aa86d-119">Je nutné použít knihovny .NET nebo balíčky NuGet třetích stran, které nejsou k dispozici pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aa86d-119">You need to use third-party .NET libraries or NuGet packages that are not available for .NET Core.</span></span>

<span data-ttu-id="aa86d-120">Použití .NET Framework v Docker může zlepšit vaše prostředí nasazení díky minimalizaci problémů s nasazením.</span><span class="sxs-lookup"><span data-stu-id="aa86d-120">Using .NET Framework on Docker can improve your deployment experiences by minimizing deployment issues.</span></span> <span data-ttu-id="aa86d-121">Tento [scénář "zvednutí a posunutí"](https://aka.ms/liftandshiftwithcontainersebook) je důležitý pro uzavření starší verze aplikací, které byly původně vyvinuty s tradičním .NET Framework, jako jsou ASP.NET WebForms, MVC Web Apps nebo WCF (Windows Communication Foundation) služby.</span><span class="sxs-lookup"><span data-stu-id="aa86d-121">This ["lift and shift" scenario](https://aka.ms/liftandshiftwithcontainersebook) is important for containerizing legacy applications that were originally developed with the traditional .NET Framework, like ASP.NET WebForms, MVC web apps or WCF (Windows Communication Foundation) services.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="aa86d-122">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="aa86d-122">Additional resources</span></span>

- <span data-ttu-id="aa86d-123">**Elektronická kniha: modernizovat stávající aplikace .NET Framework s kontejnery Azure a Windows**</span><span class="sxs-lookup"><span data-stu-id="aa86d-123">**E-book: Modernize existing .NET Framework applications with Azure and Windows Containers**</span></span>  
    <https://aka.ms/liftandshiftwithcontainersebook>

- <span data-ttu-id="aa86d-124">**Ukázkové aplikace: moderní verze starších webových aplikací v ASP.NET pomocí kontejnerů Windows**</span><span class="sxs-lookup"><span data-stu-id="aa86d-124">**Sample apps: Modernization of legacy ASP.NET web apps by using Windows Containers**</span></span>  
    <https://aka.ms/eshopmodernizing>

>[!div class="step-by-step"]
><span data-ttu-id="aa86d-125">[Předchozí](index.md) 
> [Další](net-core-container-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="aa86d-125">[Previous](index.md)
[Next](net-core-container-scenarios.md)</span></span>
