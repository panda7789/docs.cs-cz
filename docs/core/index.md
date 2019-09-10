---
title: Průvodce platformou .NET Core
description: .NET Core je modulární a vysoce výkonná implementace .NET pro vytváření aplikací pro Windows, Linux a Mac. Seznamte se s .NET Core, abyste mohli začít.
author: richlander
ms.date: 08/01/2018
ms.custom: updateeachrelease
ms.openlocfilehash: 0007c1c6a9939c46f123535f9053ac1d4ced7266
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848942"
---
# <a name="net-core-guide"></a><span data-ttu-id="0568d-104">Průvodce platformou .NET Core</span><span class="sxs-lookup"><span data-stu-id="0568d-104">.NET Core Guide</span></span>

<span data-ttu-id="0568d-105">[.NET Core](about.md) je [Open Source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT)vývojová platforma pro obecné účely udržovaná Microsoftem a komunitou .NET na [GitHubu](https://github.com/dotnet/core).</span><span class="sxs-lookup"><span data-stu-id="0568d-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="0568d-106">Je to pro různé platformy (podporující Windows, macOS a Linux) a dá se použít k sestavování aplikací pro zařízení, Cloud a IoT.</span><span class="sxs-lookup"><span data-stu-id="0568d-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

<span data-ttu-id="0568d-107">Další informace o .NET Core, včetně jeho vlastností, podporovaných jazycích a architektur a klíčových rozhraní API, najdete v tématu [o .NET Core](about.md) .</span><span class="sxs-lookup"><span data-stu-id="0568d-107">See [About .NET Core](about.md) to learn more about .NET Core, including its characteristics, supported languages and frameworks, and key APIs.</span></span>

<span data-ttu-id="0568d-108">V [kurzech pro .NET Core](tutorials/index.md) se dozvíte, jak vytvořit jednoduchou aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0568d-108">Check out [.NET Core Tutorials](tutorials/index.md) to learn how to create a simple .NET Core application.</span></span> <span data-ttu-id="0568d-109">Vaše první aplikace je možné začít používat jenom pár minut.</span><span class="sxs-lookup"><span data-stu-id="0568d-109">It only takes a few minutes to get your first app up and running.</span></span> <span data-ttu-id="0568d-110">Pokud chcete v prohlížeči vyzkoušet .NET Core, podívejte se na [čísla v C# ](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online kurzu.</span><span class="sxs-lookup"><span data-stu-id="0568d-110">If you want to try .NET Core in your browser, look at the [Numbers in C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online tutorial.</span></span>

## <a name="download-net-core-22"></a><span data-ttu-id="0568d-111">Stáhnout .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="0568d-111">Download .NET Core 2.2</span></span>

<span data-ttu-id="0568d-112">Stáhněte si [sadu .NET core 2,2 SDK](https://dotnet.microsoft.com/download) a vyzkoušejte .NET Core na počítači s Windows, MacOS nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="0568d-112">Download the [.NET Core  2.2 SDK](https://dotnet.microsoft.com/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="0568d-113">Pokud upřednostňujete použití kontejnerů Docker, přejděte na [dotnet/Core](https://hub.docker.com/_/microsoft-dotnet-core/) .</span><span class="sxs-lookup"><span data-stu-id="0568d-113">Visit [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) if you prefer to use Docker containers.</span></span>

<span data-ttu-id="0568d-114">Pokud hledáte jinou verzi rozhraní .NET Core, jsou všechny verze .NET Core k dispozici na webu [soubory ke stažení pro .NET](https://dotnet.microsoft.com/download/dotnet-core) Core.</span><span class="sxs-lookup"><span data-stu-id="0568d-114">All .NET Core versions are available at [.NET Core Downloads](https://dotnet.microsoft.com/download/dotnet-core) if you're looking for another .NET Core version.</span></span>

## <a name="net-core-22"></a><span data-ttu-id="0568d-115">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="0568d-115">.NET Core 2.2</span></span>

<span data-ttu-id="0568d-116">Nejnovější verze je [.NET Core 2,2](whats-new/dotnet-core-2-2.md).</span><span class="sxs-lookup"><span data-stu-id="0568d-116">The latest version is [.NET Core 2.2](whats-new/dotnet-core-2-2.md).</span></span> <span data-ttu-id="0568d-117">Mezi nové funkce patří: nasazení závislá na rozhraní, spouštěcí háky, ověřování AAD s Azure SQL a podpora pro Windows ARM32.</span><span class="sxs-lookup"><span data-stu-id="0568d-117">New features include: framework-dependent deployments, startup hooks, AAD authentication with Azure SQL, and support for Windows ARM32.</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="0568d-118">Vytvoření první aplikace</span><span class="sxs-lookup"><span data-stu-id="0568d-118">Create your first application</span></span>

<span data-ttu-id="0568d-119">Po instalaci .NET Core SDK otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="0568d-119">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="0568d-120">Zadáním následujících `dotnet` příkazů vytvořte a spusťte C# aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0568d-120">Type the following `dotnet` commands to create and run a C# application.</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="0568d-121">Měl by se zobrazit následující výstup:</span><span class="sxs-lookup"><span data-stu-id="0568d-121">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="support"></a><span data-ttu-id="0568d-122">Podpora</span><span class="sxs-lookup"><span data-stu-id="0568d-122">Support</span></span>

<span data-ttu-id="0568d-123">.NET Core [podporuje Microsoft](https://dotnet.microsoft.com/platform/support/policy), v systémech Windows, MacOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="0568d-123">.NET Core is [supported by Microsoft](https://dotnet.microsoft.com/platform/support/policy), on Windows, macOS and Linux.</span></span> <span data-ttu-id="0568d-124">Je aktualizovaná z hlediska zabezpečení a kvality několikrát ročně, obvykle měsíčně.</span><span class="sxs-lookup"><span data-stu-id="0568d-124">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="0568d-125">Binární distribuce .NET Core se sestavují a testují na serverech spravovaných Microsoftem v Azure a podporují se stejně jako u jakéhokoli produktu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0568d-125">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="0568d-126">[Red Hat podporuje .NET Core](http://redhatloves.net/) na Red Hat Enterprise Linux (RHEL).</span><span class="sxs-lookup"><span data-stu-id="0568d-126">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="0568d-127">Red Hat sestaví .NET Core ze zdroje a zpřístupňuje je v [kolekcích softwaru Red Hat](https://developers.redhat.com/products/softwarecollections/overview/).</span><span class="sxs-lookup"><span data-stu-id="0568d-127">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="0568d-128">Red Hat a Microsoft spolupracují, aby se zajistilo, že .NET Core dobře funguje na RHEL.</span><span class="sxs-lookup"><span data-stu-id="0568d-128">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>
