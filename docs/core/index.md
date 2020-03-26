---
title: Průvodce platformou .NET Core
description: .NET Core je modulární, vysoce výkonná implementace rozhraní .NET pro vytváření aplikací pro Windows, Linux a macOS. Další informace o .NET Core pro started a) začínáme.
author: richlander
ms.date: 12/04/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 6d2ce5951fa01ca3945ce0e64aa58fbadc8ab5af
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546546"
---
# <a name="net-core-guide"></a><span data-ttu-id="92118-104">Průvodce platformou .NET Core</span><span class="sxs-lookup"><span data-stu-id="92118-104">.NET Core guide</span></span>

<span data-ttu-id="92118-105">[.NET Core](about.md) je [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), univerzální vývojová platforma spravovaná společností Microsoft a komunitou .NET na [GitHubu](https://github.com/dotnet/core).</span><span class="sxs-lookup"><span data-stu-id="92118-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="92118-106">Je to multiplatformní (podporující Windows, macOS a Linux) a dá se použít k vytváření aplikací pro zařízení, cloud a IoT.</span><span class="sxs-lookup"><span data-stu-id="92118-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

<span data-ttu-id="92118-107">Další informace o jádru .NET Core, včetně jeho charakteristik, podporovaných jazyků a architektur a klíčových rozhraní API, najdete v tématu [O .NET Core.](about.md)</span><span class="sxs-lookup"><span data-stu-id="92118-107">See [About .NET Core](about.md) to learn more about .NET Core, including its characteristics, supported languages and frameworks, and key APIs.</span></span>

<span data-ttu-id="92118-108">Podívejte se na [.NET Core Návody se dozvíte,](tutorials/index.md) jak vytvořit jednoduchou aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="92118-108">Check out [.NET Core Tutorials](tutorials/index.md) to learn how to create a simple .NET Core application.</span></span> <span data-ttu-id="92118-109">Spuštění první aplikace trvá jen několik minut.</span><span class="sxs-lookup"><span data-stu-id="92118-109">It only takes a few minutes to get your first app up and running.</span></span> <span data-ttu-id="92118-110">Pokud chcete vyzkoušet .NET Core ve vašem prohlížeči, podívejte se na [čísla v c#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online kurzu.</span><span class="sxs-lookup"><span data-stu-id="92118-110">If you want to try .NET Core in your browser, look at the [Numbers in C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online tutorial.</span></span>

## <a name="download-net-core"></a><span data-ttu-id="92118-111">Stáhnout jádro rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="92118-111">Download .NET Core</span></span>

<span data-ttu-id="92118-112">Stáhněte si [sdk .NET Core SDK](https://dotnet.microsoft.com/download) a vyzkoušejte .NET Core na počítači se systémem Windows, macOS nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="92118-112">Download the [.NET Core SDK](https://dotnet.microsoft.com/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="92118-113">A pokud dáváte přednost použití kontejnerů Dockeru, navštivte [centrum .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="92118-113">And if you prefer to use Docker containers, visit the [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span>

<span data-ttu-id="92118-114">Všechny verze .NET Core jsou k dispozici na [.NET Core ke stažení,](https://dotnet.microsoft.com/download/dotnet-core) pokud hledáte jinou verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="92118-114">All .NET Core versions are available at [.NET Core Downloads](https://dotnet.microsoft.com/download/dotnet-core) if you're looking for another .NET Core version.</span></span>

## <a name="net-core-31"></a><span data-ttu-id="92118-115">.NET Jádro 3.1</span><span class="sxs-lookup"><span data-stu-id="92118-115">.NET Core 3.1</span></span>

<span data-ttu-id="92118-116">Nejnovější verze je .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="92118-116">The latest version is .NET Core 3.1.</span></span> <span data-ttu-id="92118-117">3.1 zahrnuje drobná vylepšení oproti .NET Core 3.0, ale .NET Core 3.1 je [dlouhodobě podporovaná verze](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="92118-117">3.1 includes minor improvements over .NET Core 3.0, however, .NET Core 3.1 is a [long-term supported release](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span> <span data-ttu-id="92118-118">Další informace o verzi .NET Core 3.1 naleznete [v tématu Co je nového v rozhraní .NET Core 3.1](./whats-new/dotnet-core-3-1.md).</span><span class="sxs-lookup"><span data-stu-id="92118-118">For more information about the .NET Core 3.1 release, see [What's new in .NET Core 3.1](./whats-new/dotnet-core-3-1.md).</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="92118-119">Vytvoření první aplikace</span><span class="sxs-lookup"><span data-stu-id="92118-119">Create your first application</span></span>

<span data-ttu-id="92118-120">Po instalaci sady .NET Core SDK otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="92118-120">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="92118-121">Chcete-li `dotnet` vytvořit a spustit aplikaci jazyka C#, zadejte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="92118-121">Enter the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="92118-122">Měl by se zobrazit následující výstup:</span><span class="sxs-lookup"><span data-stu-id="92118-122">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="support"></a><span data-ttu-id="92118-123">Podpora</span><span class="sxs-lookup"><span data-stu-id="92118-123">Support</span></span>

<span data-ttu-id="92118-124">.NET Core je [podporován společností Microsoft](https://dotnet.microsoft.com/platform/support/policy), ve Windows, macOS a Linuxu.</span><span class="sxs-lookup"><span data-stu-id="92118-124">.NET Core is [supported by Microsoft](https://dotnet.microsoft.com/platform/support/policy), on Windows, macOS, and Linux.</span></span> <span data-ttu-id="92118-125">Je aktualizován pro zabezpečení a kvalitu několikrát do roka, obvykle měsíčně.</span><span class="sxs-lookup"><span data-stu-id="92118-125">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="92118-126">Binární distribuce .NET Core jsou sestavené a testované na serverech spravovaných společností Microsoft v Azure a podporované stejně jako všechny produkty společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="92118-126">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="92118-127">[Red Hat podporuje .NET Core](http://redhatloves.net/) na Red Hat Enterprise Linux (RHEL).</span><span class="sxs-lookup"><span data-stu-id="92118-127">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="92118-128">Red Hat staví .NET Core ze zdroje a zpřístupňuje jej v [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span><span class="sxs-lookup"><span data-stu-id="92118-128">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="92118-129">Red Hat a Microsoft spolupracují, aby zajistily, že .NET Core funguje dobře na RHEL.</span><span class="sxs-lookup"><span data-stu-id="92118-129">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>
