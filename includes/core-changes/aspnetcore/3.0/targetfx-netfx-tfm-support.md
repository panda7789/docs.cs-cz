---
ms.openlocfilehash: b60f74947a537c602c7bd1a89587b76bd847c82a
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937281"
---
### <a name="target-framework-net-framework-support-dropped"></a><span data-ttu-id="560da-101">Target framework: .NET Framework support dropped</span><span class="sxs-lookup"><span data-stu-id="560da-101">Target framework: .NET Framework support dropped</span></span>

<span data-ttu-id="560da-102">Starting with ASP.NET Core 3.0, .NET Framework is an unsupported target framework.</span><span class="sxs-lookup"><span data-stu-id="560da-102">Starting with ASP.NET Core 3.0, .NET Framework is an unsupported target framework.</span></span>

#### <a name="change-description"></a><span data-ttu-id="560da-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="560da-103">Change description</span></span>

<span data-ttu-id="560da-104">.NET Framework 4.8 is the last major version of .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="560da-104">.NET Framework 4.8 is the last major version of .NET Framework.</span></span> <span data-ttu-id="560da-105">New ASP.NET Core apps should be built on .NET Core.</span><span class="sxs-lookup"><span data-stu-id="560da-105">New ASP.NET Core apps should be built on .NET Core.</span></span> <span data-ttu-id="560da-106">Starting with the .NET Core 3.0 release, you can think of ASP.NET Core 3.0 as being part of .NET Core.</span><span class="sxs-lookup"><span data-stu-id="560da-106">Starting with the .NET Core 3.0 release, you can think of ASP.NET Core 3.0 as being part of .NET Core.</span></span>

<span data-ttu-id="560da-107">Customers using ASP.NET Core with .NET Framework can continue in a fully supported fashion using the [2.1 LTS release](https://www.microsoft.com/net/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="560da-107">Customers using ASP.NET Core with .NET Framework can continue in a fully supported fashion using the [2.1 LTS release](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span> <span data-ttu-id="560da-108">Support and servicing for 2.1 continues until at least August 21, 2021.</span><span class="sxs-lookup"><span data-stu-id="560da-108">Support and servicing for 2.1 continues until at least August 21, 2021.</span></span> <span data-ttu-id="560da-109">This date is three years after declaration of the LTS release per the [.NET Support Policy](https://www.microsoft.com/net/platform/support-policy).</span><span class="sxs-lookup"><span data-stu-id="560da-109">This date is three years after declaration of the LTS release per the [.NET Support Policy](https://www.microsoft.com/net/platform/support-policy).</span></span> <span data-ttu-id="560da-110">Support for ASP.NET Core 2.1 packages **on .NET Framework** will extend indefinitely, similar to the [servicing policy for other package-based ASP.NET frameworks](https://dotnet.microsoft.com/platform/support/policy/aspnet).</span><span class="sxs-lookup"><span data-stu-id="560da-110">Support for ASP.NET Core 2.1 packages **on .NET Framework** will extend indefinitely, similar to the [servicing policy for other package-based ASP.NET frameworks](https://dotnet.microsoft.com/platform/support/policy/aspnet).</span></span>

<span data-ttu-id="560da-111">For more information about porting from .NET Framework to .NET Core, see [Porting to .NET Core](~/docs/core/porting/index.md).</span><span class="sxs-lookup"><span data-stu-id="560da-111">For more information about porting from .NET Framework to .NET Core, see [Porting to .NET Core](~/docs/core/porting/index.md).</span></span>

<span data-ttu-id="560da-112">`Microsoft.Extensions` packages (such as logging, dependency injection, and configuration) and Entity Framework Core aren't affected.</span><span class="sxs-lookup"><span data-stu-id="560da-112">`Microsoft.Extensions` packages (such as logging, dependency injection, and configuration) and Entity Framework Core aren't affected.</span></span> <span data-ttu-id="560da-113">They'll continue to support .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="560da-113">They'll continue to support .NET Standard.</span></span>

<span data-ttu-id="560da-114">For more information on the motivation for this change, see [the original blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="560da-114">For more information on the motivation for this change, see [the original blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="560da-115">Version introduced</span><span class="sxs-lookup"><span data-stu-id="560da-115">Version introduced</span></span>

<span data-ttu-id="560da-116">3,0</span><span class="sxs-lookup"><span data-stu-id="560da-116">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="560da-117">Old behavior</span><span class="sxs-lookup"><span data-stu-id="560da-117">Old behavior</span></span>

<span data-ttu-id="560da-118">ASP.NET Core apps could run on either .NET Core or .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="560da-118">ASP.NET Core apps could run on either .NET Core or .NET Framework.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="560da-119">New behavior</span><span class="sxs-lookup"><span data-stu-id="560da-119">New behavior</span></span>

<span data-ttu-id="560da-120">ASP.NET Core apps can only be run on .NET Core.</span><span class="sxs-lookup"><span data-stu-id="560da-120">ASP.NET Core apps can only be run on .NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="560da-121">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="560da-121">Recommended action</span></span>

<span data-ttu-id="560da-122">Proveďte jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="560da-122">Take one of the following actions:</span></span>

- <span data-ttu-id="560da-123">Keep your app on ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="560da-123">Keep your app on ASP.NET Core 2.1.</span></span>
- <span data-ttu-id="560da-124">Migrate your app and dependencies to .NET Core.</span><span class="sxs-lookup"><span data-stu-id="560da-124">Migrate your app and dependencies to .NET Core.</span></span>

#### <a name="category"></a><span data-ttu-id="560da-125">Kategorie</span><span class="sxs-lookup"><span data-stu-id="560da-125">Category</span></span>

<span data-ttu-id="560da-126">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="560da-126">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="560da-127">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="560da-127">Affected APIs</span></span>

<span data-ttu-id="560da-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="560da-128">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
