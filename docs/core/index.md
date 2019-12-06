---
title: Průvodce platformou .NET Core
description: .NET Core je modulární a vysoce výkonná implementace .NET pro vytváření aplikací pro Windows, Linux a Mac. Seznamte se s .NET Core, abyste mohli začít.
author: richlander
ms.date: 12/04/2019
ms.custom: updateeachrelease
ms.openlocfilehash: b2622dba53d64c9dcf58e852d57de117fe79eb2e
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837009"
---
# <a name="net-core-guide"></a><span data-ttu-id="204ea-104">Průvodce platformou .NET Core</span><span class="sxs-lookup"><span data-stu-id="204ea-104">.NET Core Guide</span></span>

<span data-ttu-id="204ea-105">[.NET Core](about.md) je [Open Source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT)vývojová platforma pro obecné účely udržovaná Microsoftem a komunitou .NET na [GitHubu](https://github.com/dotnet/core).</span><span class="sxs-lookup"><span data-stu-id="204ea-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="204ea-106">Je to pro různé platformy (podporující Windows, macOS a Linux) a dá se použít k sestavování aplikací pro zařízení, Cloud a IoT.</span><span class="sxs-lookup"><span data-stu-id="204ea-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

<span data-ttu-id="204ea-107">Další informace o .NET Core, včetně jeho vlastností, podporovaných jazycích a architektur a klíčových rozhraní API, najdete v tématu [o .NET Core](about.md) .</span><span class="sxs-lookup"><span data-stu-id="204ea-107">See [About .NET Core](about.md) to learn more about .NET Core, including its characteristics, supported languages and frameworks, and key APIs.</span></span>

<span data-ttu-id="204ea-108">V [kurzech pro .NET Core](tutorials/index.md) se dozvíte, jak vytvořit jednoduchou aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="204ea-108">Check out [.NET Core Tutorials](tutorials/index.md) to learn how to create a simple .NET Core application.</span></span> <span data-ttu-id="204ea-109">Vaše první aplikace je možné začít používat jenom pár minut.</span><span class="sxs-lookup"><span data-stu-id="204ea-109">It only takes a few minutes to get your first app up and running.</span></span> <span data-ttu-id="204ea-110">Pokud chcete v prohlížeči vyzkoušet .NET Core, podívejte se na [čísla v C# ](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online kurzu.</span><span class="sxs-lookup"><span data-stu-id="204ea-110">If you want to try .NET Core in your browser, look at the [Numbers in C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online tutorial.</span></span>

## <a name="download-net-core"></a><span data-ttu-id="204ea-111">Stáhnout .NET Core</span><span class="sxs-lookup"><span data-stu-id="204ea-111">Download .NET Core</span></span>

<span data-ttu-id="204ea-112">Stáhněte si [.NET Core SDK](https://www.microsoft.com/net/download) a vyzkoušejte .NET Core na počítači s Windows, MacOS nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="204ea-112">Download the [.NET Core SDK](https://www.microsoft.com/net/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="204ea-113">A pokud upřednostňujete použití kontejnerů Docker, navštivte web [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="204ea-113">And if you prefer to use Docker containers, visit the [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span>

<span data-ttu-id="204ea-114">Pokud hledáte jinou verzi rozhraní .NET Core, jsou všechny verze .NET Core k dispozici na webu [soubory ke stažení pro .NET](https://dotnet.microsoft.com/download/dotnet-core) Core.</span><span class="sxs-lookup"><span data-stu-id="204ea-114">All .NET Core versions are available at [.NET Core Downloads](https://dotnet.microsoft.com/download/dotnet-core) if you're looking for another .NET Core version.</span></span>

## <a name="net-core-31"></a><span data-ttu-id="204ea-115">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="204ea-115">.NET Core 3.1</span></span>

<span data-ttu-id="204ea-116">Nejnovější verze je .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="204ea-116">The latest version is .NET Core 3.1.</span></span> <span data-ttu-id="204ea-117">Což zahrnuje menší vylepšení .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="204ea-117">Which includes minor improvements over .NET Core 3.0.</span></span> <span data-ttu-id="204ea-118">.NET Core 3,1 je ale dlouhodobě podporovanou verzí.</span><span class="sxs-lookup"><span data-stu-id="204ea-118">However, .NET Core 3.1 is a long-term supported release.</span></span> <span data-ttu-id="204ea-119">Další informace o verzi .NET Core 3,1 najdete v článku [novinky v rozhraní .NET core 3,1](./whats-new/dotnet-core-3-1.md).</span><span class="sxs-lookup"><span data-stu-id="204ea-119">For more information about the .NET Core 3.1 release, see [What's new in .NET Core 3.1](./whats-new/dotnet-core-3-1.md).</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="204ea-120">Vytvoření první aplikace</span><span class="sxs-lookup"><span data-stu-id="204ea-120">Create your first application</span></span>

<span data-ttu-id="204ea-121">Po instalaci .NET Core SDK otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="204ea-121">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="204ea-122">Zadejte následující `dotnet` příkazy pro vytvoření a spuštění C# aplikace:</span><span class="sxs-lookup"><span data-stu-id="204ea-122">Type the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="204ea-123">Měli byste vidět následující výstup:</span><span class="sxs-lookup"><span data-stu-id="204ea-123">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="support"></a><span data-ttu-id="204ea-124">Podpora</span><span class="sxs-lookup"><span data-stu-id="204ea-124">Support</span></span>

<span data-ttu-id="204ea-125">.NET Core [podporuje Microsoft](https://dotnet.microsoft.com/platform/support/policy), ve Windows, MacOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="204ea-125">.NET Core is [supported by Microsoft](https://dotnet.microsoft.com/platform/support/policy), on Windows, macOS, and Linux.</span></span> <span data-ttu-id="204ea-126">Je aktualizovaná z hlediska zabezpečení a kvality několikrát ročně, obvykle měsíčně.</span><span class="sxs-lookup"><span data-stu-id="204ea-126">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="204ea-127">Binární distribuce .NET Core se sestavují a testují na serverech spravovaných Microsoftem v Azure a podporují se stejně jako u jakéhokoli produktu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="204ea-127">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="204ea-128">[Red Hat podporuje .NET Core](http://redhatloves.net/) na Red Hat Enterprise Linux (RHEL).</span><span class="sxs-lookup"><span data-stu-id="204ea-128">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="204ea-129">Red Hat sestaví .NET Core ze zdroje a zpřístupňuje je v [kolekcích softwaru Red Hat](https://developers.redhat.com/products/softwarecollections/overview/).</span><span class="sxs-lookup"><span data-stu-id="204ea-129">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="204ea-130">Red Hat a Microsoft spolupracují, aby se zajistilo, že .NET Core dobře funguje na RHEL.</span><span class="sxs-lookup"><span data-stu-id="204ea-130">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>
