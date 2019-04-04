---
title: Průvodce platformou .NET Core
description: .NET core je modulární a vysoce výkonnou implementace .NET pro vytváření aplikací pro Windows, Linux a Mac. Další informace o .NET Core, abyste mohli začít.
author: richlander
ms.date: 08/01/2018
ms.custom: updateeachrelease
ms.openlocfilehash: 79a0c09074159160dd01b0c7970612f7058cc3fc
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/04/2019
ms.locfileid: "58920620"
---
# <a name="net-core-guide"></a><span data-ttu-id="63c7a-104">Průvodce platformou .NET Core</span><span class="sxs-lookup"><span data-stu-id="63c7a-104">.NET Core Guide</span></span>

<span data-ttu-id="63c7a-105">[.NET core](about.md) je [open source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT), pro obecné účely Vývojová platforma udržuje od Microsoftu a komunity .NET na [Githubu](https://github.com/dotnet/core).</span><span class="sxs-lookup"><span data-stu-id="63c7a-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="63c7a-106">Je multiplatformní (podporují Windows, macOS a Linux) a je možné vytvářet zařízení, cloud a aplikace IoT.</span><span class="sxs-lookup"><span data-stu-id="63c7a-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

<span data-ttu-id="63c7a-107">Zobrazit [o .NET Core](about.md) získat další informace o .NET Core, včetně jeho vlastnosti, podporované jazyky a platformy a klíč rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="63c7a-107">See [About .NET Core](about.md) to learn more about .NET Core, including its characteristics, supported languages and frameworks, and key APIs.</span></span>

<span data-ttu-id="63c7a-108">Podívejte se na [kurzy k .NET Core](tutorials/index.md) se naučíte vytvořit jednoduchou aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="63c7a-108">Check out [.NET Core Tutorials](tutorials/index.md) to learn how to create a simple .NET Core application.</span></span> <span data-ttu-id="63c7a-109">Trvá jenom pár minut a zprovoznění svoji první aplikaci.</span><span class="sxs-lookup"><span data-stu-id="63c7a-109">It only takes a few minutes to get your first app up and running.</span></span> <span data-ttu-id="63c7a-110">Pokud chcete vyzkoušet .NET Core v prohlížeči, podívejte se na [čísla ve C# ](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online kurz ke službě.</span><span class="sxs-lookup"><span data-stu-id="63c7a-110">If you want to try .NET Core in your browser, look at the [Numbers in C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online tutorial.</span></span>

## <a name="download-net-core-22"></a><span data-ttu-id="63c7a-111">Stáhnout .NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="63c7a-111">Download .NET Core 2.2</span></span>

<span data-ttu-id="63c7a-112">Stáhněte si [.NET Core 2.2 SDK](https://www.microsoft.com/net/download) vyzkoušet .NET Core na počítači Windows, macOS nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="63c7a-112">Download the [.NET Core  2.2 SDK](https://www.microsoft.com/net/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="63c7a-113">Navštivte [dotnet/jádro](https://hub.docker.com/_/microsoft-dotnet-core/) Pokud byste radši chtěli použít kontejnery Dockeru.</span><span class="sxs-lookup"><span data-stu-id="63c7a-113">Visit [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) if you prefer to use Docker containers.</span></span>

<span data-ttu-id="63c7a-114">Všechny verze .NET Core najdete na adrese [soubory ke stažení rozhraní .NET Core](https://www.microsoft.com/net/download/archives) Pokud potřebujete jinou verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="63c7a-114">All .NET Core versions are available at [.NET Core Downloads](https://www.microsoft.com/net/download/archives) if you're looking for another .NET Core version.</span></span>

## <a name="net-core-22"></a><span data-ttu-id="63c7a-115">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="63c7a-115">.NET Core 2.2</span></span>

<span data-ttu-id="63c7a-116">Nejnovější verze je [.NET Core 2.2](whats-new/dotnet-core-2-2.md).</span><span class="sxs-lookup"><span data-stu-id="63c7a-116">The latest version is [.NET Core 2.2](whats-new/dotnet-core-2-2.md).</span></span> <span data-ttu-id="63c7a-117">Mezi nové funkce patří: závisí na architektuře nasazení, spuštění háky, ověřování AAD s Azure SQL a podpora Windows ARM32.</span><span class="sxs-lookup"><span data-stu-id="63c7a-117">New features include: framework-dependent deployments, startup hooks, AAD authentication with Azure SQL, and support for Windows ARM32.</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="63c7a-118">Vytvoření první aplikace</span><span class="sxs-lookup"><span data-stu-id="63c7a-118">Create your first application</span></span>

<span data-ttu-id="63c7a-119">Po instalaci rozhraní .NET Core SDK, otevřete příkazový řádek.</span><span class="sxs-lookup"><span data-stu-id="63c7a-119">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="63c7a-120">Zadejte následující příkaz `dotnet` příkazy k vytvoření a spuštění aplikace v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="63c7a-120">Type the following `dotnet` commands to create and run a C# application.</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="63c7a-121">Byste měli vidět následující výstup:</span><span class="sxs-lookup"><span data-stu-id="63c7a-121">You should see the following output:</span></span>

```console
Hello World!
```

## <a name="support"></a><span data-ttu-id="63c7a-122">Podpora</span><span class="sxs-lookup"><span data-stu-id="63c7a-122">Support</span></span>

<span data-ttu-id="63c7a-123">.NET core je [společnost Microsoft podporuje](https://www.microsoft.com/net/support/policy), ve Windows, macOS a Linuxu.</span><span class="sxs-lookup"><span data-stu-id="63c7a-123">.NET Core is [supported by Microsoft](https://www.microsoft.com/net/support/policy), on Windows, macOS and Linux.</span></span> <span data-ttu-id="63c7a-124">To je aktualizována o zabezpečení a kvalitní několikrát za rok, obvykle měsíčně.</span><span class="sxs-lookup"><span data-stu-id="63c7a-124">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="63c7a-125">Binární distribuce .NET core jsou integrované a otestovali na Microsoft udržuje serverů v Azure a podporované stejně jako libovolný produkt společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="63c7a-125">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="63c7a-126">[Red Hat podporuje .NET Core](http://redhatloves.net/) na Red Hat Enterprise Linux (RHEL).</span><span class="sxs-lookup"><span data-stu-id="63c7a-126">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="63c7a-127">Red Hat sestavení .NET Core ze zdroje a zpřístupňuje je v [kolekce softwaru Red Hat](https://developers.redhat.com/products/softwarecollections/overview/).</span><span class="sxs-lookup"><span data-stu-id="63c7a-127">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="63c7a-128">Red Hat a Microsoft spolupracují na Ujistěte se, že v RHEL dobře funguje .NET Core.</span><span class="sxs-lookup"><span data-stu-id="63c7a-128">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>
