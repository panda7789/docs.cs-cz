---
title: Průvodce platformou .NET Core
description: .NET core je modulární a vysoce výkonnou implementace .NET pro vytváření aplikací pro Windows, Linux a Mac. Další informace o .NET Core, abyste mohli začít.
author: richlander
ms.author: mairaw
ms.date: 08/01/2018
ms.custom: updateeachrelease
ms.openlocfilehash: b302b6fc7e097a811c718d2244f603246cb5c259
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121035"
---
# <a name="net-core-guide"></a><span data-ttu-id="3cad0-104">Průvodce platformou .NET Core</span><span class="sxs-lookup"><span data-stu-id="3cad0-104">.NET Core Guide</span></span>

<span data-ttu-id="3cad0-105">[.NET core](about.md) je [open source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT) pro obecné účely Vývojová platforma udržuje od Microsoftu a komunity .NET na [Githubu](https://github.com/dotnet/core).</span><span class="sxs-lookup"><span data-stu-id="3cad0-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT) general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="3cad0-106">Je multiplatformní, podpora Windows, macOS a Linux a je možné v zařízení, cloud a aplikace IoT.</span><span class="sxs-lookup"><span data-stu-id="3cad0-106">It's cross-platform, supporting Windows, macOS and Linux, and can be used in device, cloud, and IoT applications.</span></span>

<span data-ttu-id="3cad0-107">Zobrazit [o .NET Core](about.md) získat další informace o .NET Core, včetně jeho vlastnosti, podporované jazyky a platformy a klíč rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="3cad0-107">See [About .NET Core](about.md) to learn more about .NET Core, including its characteristics, supported languages and frameworks, and key APIs.</span></span>

<span data-ttu-id="3cad0-108">Podívejte se na [kurzy k .NET Core](tutorials/index.md) se naučíte vytvořit jednoduchou aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3cad0-108">Check out [.NET Core Tutorials](tutorials/index.md) to learn how to create a simple .NET Core application.</span></span> <span data-ttu-id="3cad0-109">Trvá jenom pár minut a zprovoznění svoji první aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3cad0-109">It only takes a few minutes to get your first app up and running.</span></span> <span data-ttu-id="3cad0-110">Pokud chcete vyzkoušet .NET Core v prohlížeči, podívejte se na [čísla v C#](https://docs.microsoft.com/dotnet/csharp/quick-starts/numbers-in-csharp) rychlý start.</span><span class="sxs-lookup"><span data-stu-id="3cad0-110">If you want to try .NET Core in your browser, look at the [Numbers in C#](https://docs.microsoft.com/dotnet/csharp/quick-starts/numbers-in-csharp) quickstart.</span></span>

## <a name="download-net-core-21"></a><span data-ttu-id="3cad0-111">Stáhnout .NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3cad0-111">Download .NET Core 2.1</span></span>

<span data-ttu-id="3cad0-112">Stáhněte si [sady SDK .NET Core 2.1](https://www.microsoft.com/net/download) vyzkoušet .NET Core na počítači Windows, macOS nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="3cad0-112">Download the [.NET Core  2.1 SDK](https://www.microsoft.com/net/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="3cad0-113">Navštivte [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) Pokud byste radši chtěli použít kontejnery Dockeru.</span><span class="sxs-lookup"><span data-stu-id="3cad0-113">Visit [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) if you prefer to use Docker containers.</span></span>

<span data-ttu-id="3cad0-114">Všechny verze .NET Core najdete na adrese [soubory ke stažení rozhraní .NET Core](https://www.microsoft.com/net/download/archives) Pokud potřebujete jinou verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3cad0-114">All .NET Core versions are available at [.NET Core Downloads](https://www.microsoft.com/net/download/archives) if you're looking for another .NET Core version.</span></span>

## <a name="net-core-21"></a><span data-ttu-id="3cad0-115">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="3cad0-115">.NET Core 2.1</span></span>

<span data-ttu-id="3cad0-116">Nejnovější verze je [.NET Core 2.1](whats-new/dotnet-core-2-1.md).</span><span class="sxs-lookup"><span data-stu-id="3cad0-116">The latest version is [.NET Core 2.1](whats-new/dotnet-core-2-1.md).</span></span> <span data-ttu-id="3cad0-117">Mezi nové funkce patří: globální nástroje, výkonné rozhraní API (například <xref:System.Span%601?displayProperty=nameWithType>), vrstvené kompilace JIT [sestavení](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) a [vylepšení výkonu modulu runtime](https://blogs.msdn.microsoft.com/dotnet/2018/04/18/performance-improvements-in-net-core-2-1/)a podpora pro Alpine a ARM32.</span><span class="sxs-lookup"><span data-stu-id="3cad0-117">New features include: global tools, high-performance APIs (such as <xref:System.Span%601?displayProperty=nameWithType>), tiered JIT compilation, [build](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) and [runtime performance improvements](https://blogs.msdn.microsoft.com/dotnet/2018/04/18/performance-improvements-in-net-core-2-1/), and support for Alpine and ARM32.</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="3cad0-118">Vytvoření první aplikace</span><span class="sxs-lookup"><span data-stu-id="3cad0-118">Create your first application</span></span>

<span data-ttu-id="3cad0-119">Po instalaci rozhraní .NET Core SDK, otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="3cad0-119">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="3cad0-120">Zadejte následující příkaz `dotnet` příkazy k vytvoření a spuštění aplikace v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="3cad0-120">Type the following `dotnet` commands to create and run a C# application.</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="3cad0-121">Byste měli vidět následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3cad0-121">You should see the following output:</span></span>

```console
Hello World!
```

## <a name="support"></a><span data-ttu-id="3cad0-122">Podpora</span><span class="sxs-lookup"><span data-stu-id="3cad0-122">Support</span></span>

<span data-ttu-id="3cad0-123">.NET core je [společnost Microsoft podporuje](https://www.microsoft.com/net/support/policy), ve Windows, macOS a Linuxu.</span><span class="sxs-lookup"><span data-stu-id="3cad0-123">.NET Core is [supported by Microsoft](https://www.microsoft.com/net/support/policy), on Windows, macOS and Linux.</span></span> <span data-ttu-id="3cad0-124">To je aktualizována o zabezpečení a kvalitní několikrát za rok, obvykle měsíčně.</span><span class="sxs-lookup"><span data-stu-id="3cad0-124">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="3cad0-125">Binární distribuce .NET core jsou integrované a otestovali na Microsoft udržuje serverů v Azure a podporované stejně jako libovolný produkt společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3cad0-125">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="3cad0-126">[Red Hat podporuje .NET Core](http://redhatloves.net/) na Red Hat Enterprise Linux (RHEL).</span><span class="sxs-lookup"><span data-stu-id="3cad0-126">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="3cad0-127">Red Hat sestavení .NET Core ze zdroje a zpřístupňuje je v [kolekce softwaru Red Hat](https://developers.redhat.com/products/softwarecollections/overview/).</span><span class="sxs-lookup"><span data-stu-id="3cad0-127">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="3cad0-128">Red Hat a Microsoft spolupracují na Ujistěte se, že v RHEL dobře funguje .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3cad0-128">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>
