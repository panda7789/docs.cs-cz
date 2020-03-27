---
title: Úvod a přehled .NET Core
description: .NET Core je modulární, vysoce výkonná implementace rozhraní .NET pro vytváření aplikací pro Windows, Linux a macOS. Další informace o .NET Core pro started a) začínáme.
author: richlander
ms.date: 03/25/2020
ms.custom: updateeachrelease
ms.openlocfilehash: edd3864d3c3c5c0e9fd8c26ee806ffc9e100423d
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80351699"
---
# <a name="introduction-to-net-core"></a><span data-ttu-id="289b7-104">Úvod do rozhraní .NET Core</span><span class="sxs-lookup"><span data-stu-id="289b7-104">Introduction to .NET Core</span></span>

<span data-ttu-id="289b7-105">[.NET Core](about.md) je [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), univerzální vývojová platforma spravovaná společností Microsoft a komunitou .NET na [GitHubu](https://github.com/dotnet/core).</span><span class="sxs-lookup"><span data-stu-id="289b7-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="289b7-106">Je to multiplatformní (podporující Windows, macOS a Linux) a dá se použít k vytváření aplikací pro zařízení, cloud a IoT.</span><span class="sxs-lookup"><span data-stu-id="289b7-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

## <a name="download-net-core"></a><span data-ttu-id="289b7-107">Stáhnout jádro rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="289b7-107">Download .NET Core</span></span>

<span data-ttu-id="289b7-108">Stáhněte si [sdk .NET Core SDK](https://dotnet.microsoft.com/download) a vyzkoušejte .NET Core na počítači se systémem Windows, macOS nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="289b7-108">Download the [.NET Core SDK](https://dotnet.microsoft.com/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="289b7-109">Pokud dáváte přednost použití kontejnerů Dockeru, navštivte [centrum .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="289b7-109">If you prefer to use Docker containers, visit the [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span>

## <a name="net-core-31"></a><span data-ttu-id="289b7-110">.NET Jádro 3.1</span><span class="sxs-lookup"><span data-stu-id="289b7-110">.NET Core 3.1</span></span>

<span data-ttu-id="289b7-111">Nejnovější verze je .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="289b7-111">The latest version is .NET Core 3.1.</span></span> <span data-ttu-id="289b7-112">3.1 zahrnuje drobná vylepšení oproti .NET Core 3.0, ale .NET Core 3.1 je [dlouhodobě podporovaná verze](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="289b7-112">3.1 includes minor improvements over .NET Core 3.0, however, .NET Core 3.1 is a [long-term supported release](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span> <span data-ttu-id="289b7-113">Další informace o verzi .NET Core 3.1 naleznete [v tématu Co je nového v rozhraní .NET Core 3.1](./whats-new/dotnet-core-3-1.md).</span><span class="sxs-lookup"><span data-stu-id="289b7-113">For more information about the .NET Core 3.1 release, see [What's new in .NET Core 3.1](./whats-new/dotnet-core-3-1.md).</span></span>

<span data-ttu-id="289b7-114">Pokud hledáte jinou verzi rozhraní .NET Core, všechny verze jsou k dispozici na [.NET Core ke stažení](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="289b7-114">If you're looking for another version of .NET Core, all the versions are available at [.NET Core downloads](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="289b7-115">Vytvoření první aplikace</span><span class="sxs-lookup"><span data-stu-id="289b7-115">Create your first application</span></span>

<span data-ttu-id="289b7-116">Po instalaci sady .NET Core SDK otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="289b7-116">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="289b7-117">Chcete-li `dotnet` vytvořit a spustit aplikaci jazyka C#, zadejte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="289b7-117">Enter the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="289b7-118">Měl by se zobrazit následující výstup:</span><span class="sxs-lookup"><span data-stu-id="289b7-118">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="support"></a><span data-ttu-id="289b7-119">Podpora</span><span class="sxs-lookup"><span data-stu-id="289b7-119">Support</span></span>

<span data-ttu-id="289b7-120">.NET Core je [podporován společností Microsoft](https://dotnet.microsoft.com/platform/support/policy) v systémech Windows, macOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="289b7-120">.NET Core is [supported by Microsoft](https://dotnet.microsoft.com/platform/support/policy) on Windows, macOS, and Linux.</span></span> <span data-ttu-id="289b7-121">Je aktualizován pro zabezpečení a kvalitu několikrát do roka, obvykle měsíčně.</span><span class="sxs-lookup"><span data-stu-id="289b7-121">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="289b7-122">Binární distribuce .NET Core jsou sestavené a testované na serverech spravovaných společností Microsoft v Azure a podporované stejně jako všechny produkty společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="289b7-122">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="289b7-123">[Red Hat podporuje .NET Core](http://redhatloves.net/) na Red Hat Enterprise Linux (RHEL).</span><span class="sxs-lookup"><span data-stu-id="289b7-123">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="289b7-124">Red Hat staví .NET Core ze zdroje a zpřístupňuje jej v [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span><span class="sxs-lookup"><span data-stu-id="289b7-124">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="289b7-125">Red Hat a Microsoft spolupracují, aby zajistily, že .NET Core funguje dobře na RHEL.</span><span class="sxs-lookup"><span data-stu-id="289b7-125">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>

## <a name="next-steps"></a><span data-ttu-id="289b7-126">Další kroky</span><span class="sxs-lookup"><span data-stu-id="289b7-126">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="289b7-127">Kurzy jádra .NET</span><span class="sxs-lookup"><span data-stu-id="289b7-127">.NET Core tutorials</span></span>](tutorials/index.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="289b7-128">Vyzkoušejte v prohlížeči rozhraní .NET Core</span><span class="sxs-lookup"><span data-stu-id="289b7-128">Try .NET Core in your browser</span></span>](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
