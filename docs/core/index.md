---
title: Průvodce platformou .NET Core
description: .NET Core je modulární a vysoce výkonná implementace .NET pro vytváření aplikací pro Windows, Linux a macOS. Seznamte se s .NET Core, abyste mohli začít.
author: richlander
ms.date: 12/04/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 3db98d21a7cdc80d8a98b23782a81ffa37520937
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740755"
---
# <a name="net-core-guide"></a><span data-ttu-id="4a893-104">Průvodce platformou .NET Core</span><span class="sxs-lookup"><span data-stu-id="4a893-104">.NET Core guide</span></span>

<span data-ttu-id="4a893-105">[.NET Core](about.md) je [Open Source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)vývojová platforma pro obecné účely udržovaná Microsoftem a komunitou .NET na [GitHubu](https://github.com/dotnet/core).</span><span class="sxs-lookup"><span data-stu-id="4a893-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="4a893-106">Je to pro různé platformy (podporující Windows, macOS a Linux) a dá se použít k sestavování aplikací pro zařízení, Cloud a IoT.</span><span class="sxs-lookup"><span data-stu-id="4a893-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

<span data-ttu-id="4a893-107">Další informace o .NET Core, včetně jeho vlastností, podporovaných jazycích a architektur a klíčových rozhraní API, najdete v tématu [o .NET Core](about.md) .</span><span class="sxs-lookup"><span data-stu-id="4a893-107">See [About .NET Core](about.md) to learn more about .NET Core, including its characteristics, supported languages and frameworks, and key APIs.</span></span>

<span data-ttu-id="4a893-108">V [kurzech pro .NET Core](tutorials/index.md) se dozvíte, jak vytvořit jednoduchou aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4a893-108">Check out [.NET Core Tutorials](tutorials/index.md) to learn how to create a simple .NET Core application.</span></span> <span data-ttu-id="4a893-109">Vaše první aplikace je možné začít používat jenom pár minut.</span><span class="sxs-lookup"><span data-stu-id="4a893-109">It only takes a few minutes to get your first app up and running.</span></span> <span data-ttu-id="4a893-110">Pokud chcete v prohlížeči vyzkoušet .NET Core, podívejte se na [čísla v C# ](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online kurzu.</span><span class="sxs-lookup"><span data-stu-id="4a893-110">If you want to try .NET Core in your browser, look at the [Numbers in C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online tutorial.</span></span>

## <a name="download-net-core"></a><span data-ttu-id="4a893-111">Stáhnout .NET Core</span><span class="sxs-lookup"><span data-stu-id="4a893-111">Download .NET Core</span></span>

<span data-ttu-id="4a893-112">Stáhněte si [.NET Core SDK](https://www.microsoft.com/net/download) a vyzkoušejte .NET Core na počítači s Windows, MacOS nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="4a893-112">Download the [.NET Core SDK](https://www.microsoft.com/net/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="4a893-113">A pokud upřednostňujete použití kontejnerů Docker, navštivte web [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="4a893-113">And if you prefer to use Docker containers, visit the [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span>

<span data-ttu-id="4a893-114">Pokud hledáte jinou verzi rozhraní .NET Core, jsou všechny verze .NET Core k dispozici na webu [soubory ke stažení pro .NET](https://dotnet.microsoft.com/download/dotnet-core) Core.</span><span class="sxs-lookup"><span data-stu-id="4a893-114">All .NET Core versions are available at [.NET Core Downloads](https://dotnet.microsoft.com/download/dotnet-core) if you're looking for another .NET Core version.</span></span>

## <a name="net-core-31"></a><span data-ttu-id="4a893-115">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="4a893-115">.NET Core 3.1</span></span>

<span data-ttu-id="4a893-116">Nejnovější verze je .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="4a893-116">The latest version is .NET Core 3.1.</span></span> <span data-ttu-id="4a893-117">3,1 obsahuje menší vylepšení .NET Core 3,0, ale .NET Core 3,1 je [dlouhodobě podporovanou verzí](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="4a893-117">3.1 includes minor improvements over .NET Core 3.0, however, .NET Core 3.1 is a [long-term supported release](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span> <span data-ttu-id="4a893-118">Další informace o verzi .NET Core 3,1 najdete v článku [novinky v rozhraní .NET core 3,1](./whats-new/dotnet-core-3-1.md).</span><span class="sxs-lookup"><span data-stu-id="4a893-118">For more information about the .NET Core 3.1 release, see [What's new in .NET Core 3.1](./whats-new/dotnet-core-3-1.md).</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="4a893-119">Vytvoření první aplikace</span><span class="sxs-lookup"><span data-stu-id="4a893-119">Create your first application</span></span>

<span data-ttu-id="4a893-120">Po instalaci .NET Core SDK otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="4a893-120">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="4a893-121">Chcete-li vytvořit a spustit C# aplikaci, zadejte následující příkazy `dotnet`:</span><span class="sxs-lookup"><span data-stu-id="4a893-121">Enter the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="4a893-122">Měli byste vidět následující výstup:</span><span class="sxs-lookup"><span data-stu-id="4a893-122">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="support"></a><span data-ttu-id="4a893-123">Podpora</span><span class="sxs-lookup"><span data-stu-id="4a893-123">Support</span></span>

<span data-ttu-id="4a893-124">.NET Core [podporuje Microsoft](https://dotnet.microsoft.com/platform/support/policy), ve Windows, MacOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="4a893-124">.NET Core is [supported by Microsoft](https://dotnet.microsoft.com/platform/support/policy), on Windows, macOS, and Linux.</span></span> <span data-ttu-id="4a893-125">Je aktualizovaná z hlediska zabezpečení a kvality několikrát ročně, obvykle měsíčně.</span><span class="sxs-lookup"><span data-stu-id="4a893-125">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="4a893-126">Binární distribuce .NET Core se sestavují a testují na serverech spravovaných Microsoftem v Azure a podporují se stejně jako u jakéhokoli produktu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4a893-126">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="4a893-127">[Red Hat podporuje .NET Core](http://redhatloves.net/) na Red Hat Enterprise Linux (RHEL).</span><span class="sxs-lookup"><span data-stu-id="4a893-127">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="4a893-128">Red Hat sestaví .NET Core ze zdroje a zpřístupňuje je v [kolekcích softwaru Red Hat](https://developers.redhat.com/products/softwarecollections/overview/).</span><span class="sxs-lookup"><span data-stu-id="4a893-128">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="4a893-129">Red Hat a Microsoft spolupracují, aby se zajistilo, že .NET Core dobře funguje na RHEL.</span><span class="sxs-lookup"><span data-stu-id="4a893-129">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>
