---
title: Průvodce platformou .NET Core
description: .NET Core je modulární a vysoce výkonná implementace .NET pro vytváření aplikací pro Windows, Linux a Mac. Seznamte se s .NET Core, abyste mohli začít.
author: richlander
ms.date: 09/23/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 95f18ca09852ce139a4b99ed7aef4802d4883e13
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216219"
---
# <a name="net-core-guide"></a><span data-ttu-id="4b519-104">Průvodce platformou .NET Core</span><span class="sxs-lookup"><span data-stu-id="4b519-104">.NET Core Guide</span></span>

<span data-ttu-id="4b519-105">[.NET Core](about.md) je [Open Source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT)vývojová platforma pro obecné účely udržovaná Microsoftem a komunitou .NET na [GitHubu](https://github.com/dotnet/core).</span><span class="sxs-lookup"><span data-stu-id="4b519-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="4b519-106">Je to pro různé platformy (podporující Windows, macOS a Linux) a dá se použít k sestavování aplikací pro zařízení, Cloud a IoT.</span><span class="sxs-lookup"><span data-stu-id="4b519-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

<span data-ttu-id="4b519-107">Další informace o .NET Core, včetně jeho vlastností, podporovaných jazycích a architektur a klíčových rozhraní API, najdete v tématu [o .NET Core](about.md) .</span><span class="sxs-lookup"><span data-stu-id="4b519-107">See [About .NET Core](about.md) to learn more about .NET Core, including its characteristics, supported languages and frameworks, and key APIs.</span></span>

<span data-ttu-id="4b519-108">V [kurzech pro .NET Core](tutorials/index.md) se dozvíte, jak vytvořit jednoduchou aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4b519-108">Check out [.NET Core Tutorials](tutorials/index.md) to learn how to create a simple .NET Core application.</span></span> <span data-ttu-id="4b519-109">Vaše první aplikace je možné začít používat jenom pár minut.</span><span class="sxs-lookup"><span data-stu-id="4b519-109">It only takes a few minutes to get your first app up and running.</span></span> <span data-ttu-id="4b519-110">Pokud chcete v prohlížeči vyzkoušet .NET Core, podívejte se na [čísla v C# ](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online kurzu.</span><span class="sxs-lookup"><span data-stu-id="4b519-110">If you want to try .NET Core in your browser, look at the [Numbers in C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online tutorial.</span></span>

## <a name="download-net-core"></a><span data-ttu-id="4b519-111">Stáhnout .NET Core</span><span class="sxs-lookup"><span data-stu-id="4b519-111">Download .NET Core</span></span>

<span data-ttu-id="4b519-112">Stáhněte si [.NET Core SDK](https://www.microsoft.com/net/download) a vyzkoušejte .NET Core na počítači s Windows, MacOS nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="4b519-112">Download the [.NET Core SDK](https://www.microsoft.com/net/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="4b519-113">A pokud upřednostňujete použití kontejnerů Docker, navštivte web [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="4b519-113">And if you prefer to use Docker containers, visit the [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span>

<span data-ttu-id="4b519-114">Pokud hledáte jinou verzi rozhraní .NET Core, jsou všechny verze .NET Core k dispozici na webu [soubory ke stažení pro .NET](https://dotnet.microsoft.com/download/dotnet-core) Core.</span><span class="sxs-lookup"><span data-stu-id="4b519-114">All .NET Core versions are available at [.NET Core Downloads](https://dotnet.microsoft.com/download/dotnet-core) if you're looking for another .NET Core version.</span></span>

## <a name="net-core-30"></a><span data-ttu-id="4b519-115">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="4b519-115">.NET Core 3.0</span></span>

<span data-ttu-id="4b519-116">Nejnovější verze je .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="4b519-116">The latest version is .NET Core 3.0.</span></span> <span data-ttu-id="4b519-117">Mezi nové funkce patří podpora stolních počítačů s Windows pomocí Windows Presentation Foundation (WPF) a C# model Windows Forms, úplného vytváření zásobníku pro web s Blazor, nová vylepšení pro signál a službu C# Azure Signal Service C# , nové funkce jazyka s 8 a mnoho dalšího.</span><span class="sxs-lookup"><span data-stu-id="4b519-117">New features include Windows Desktop support with Windows Presentation Foundation (WPF) and Windows Forms, full stack C# web development with Blazor, new enhancements to SignalR and Azure SignalR Service, new C# language features with C# 8, and much more.</span></span> <span data-ttu-id="4b519-118">Úplný seznam nových funkcí v rozhraní .NET Core 3,0 najdete v tématu [co je nového v rozhraní .NET core 3,0](./whats-new/dotnet-core-3-0.md).</span><span class="sxs-lookup"><span data-stu-id="4b519-118">For a full listing of the new features in .NET Core 3.0, see [What's new in .NET Core 3.0](./whats-new/dotnet-core-3-0.md).</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="4b519-119">Vytvoření první aplikace</span><span class="sxs-lookup"><span data-stu-id="4b519-119">Create your first application</span></span>

<span data-ttu-id="4b519-120">Po instalaci .NET Core SDK otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="4b519-120">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="4b519-121">Zadáním následujících `dotnet` příkazů vytvořte a spusťte C# aplikaci:</span><span class="sxs-lookup"><span data-stu-id="4b519-121">Type the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="4b519-122">Měl by se zobrazit následující výstup:</span><span class="sxs-lookup"><span data-stu-id="4b519-122">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="support"></a><span data-ttu-id="4b519-123">Podpora</span><span class="sxs-lookup"><span data-stu-id="4b519-123">Support</span></span>

<span data-ttu-id="4b519-124">.NET Core [podporuje Microsoft](https://dotnet.microsoft.com/platform/support/policy), ve Windows, MacOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="4b519-124">.NET Core is [supported by Microsoft](https://dotnet.microsoft.com/platform/support/policy), on Windows, macOS, and Linux.</span></span> <span data-ttu-id="4b519-125">Je aktualizovaná z hlediska zabezpečení a kvality několikrát ročně, obvykle měsíčně.</span><span class="sxs-lookup"><span data-stu-id="4b519-125">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="4b519-126">Binární distribuce .NET Core se sestavují a testují na serverech spravovaných Microsoftem v Azure a podporují se stejně jako u jakéhokoli produktu společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4b519-126">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="4b519-127">[Red Hat podporuje .NET Core](http://redhatloves.net/) na Red Hat Enterprise Linux (RHEL).</span><span class="sxs-lookup"><span data-stu-id="4b519-127">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="4b519-128">Red Hat sestaví .NET Core ze zdroje a zpřístupňuje je v [kolekcích softwaru Red Hat](https://developers.redhat.com/products/softwarecollections/overview/).</span><span class="sxs-lookup"><span data-stu-id="4b519-128">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="4b519-129">Red Hat a Microsoft spolupracují, aby se zajistilo, že .NET Core dobře funguje na RHEL.</span><span class="sxs-lookup"><span data-stu-id="4b519-129">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>
