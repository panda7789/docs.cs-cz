---
ms.openlocfilehash: b60f74947a537c602c7bd1a89587b76bd847c82a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937281"
---
### <a name="target-framework-net-framework-support-dropped"></a><span data-ttu-id="eb4f8-101">Cílová architektura: Podpora rozhraní .NET Framework byla vynechána.</span><span class="sxs-lookup"><span data-stu-id="eb4f8-101">Target framework: .NET Framework support dropped</span></span>

<span data-ttu-id="eb4f8-102">Počínaje ASP.NET jádrem 3.0 je rozhraní .NET Framework nepodporovanou cílovou architekturou.</span><span class="sxs-lookup"><span data-stu-id="eb4f8-102">Starting with ASP.NET Core 3.0, .NET Framework is an unsupported target framework.</span></span>

#### <a name="change-description"></a><span data-ttu-id="eb4f8-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="eb4f8-103">Change description</span></span>

<span data-ttu-id="eb4f8-104">Rozhraní .NET Framework 4.8 je poslední hlavní verzí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eb4f8-104">.NET Framework 4.8 is the last major version of .NET Framework.</span></span> <span data-ttu-id="eb4f8-105">Nové aplikace ASP.NET Core by měly být postaveny na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="eb4f8-105">New ASP.NET Core apps should be built on .NET Core.</span></span> <span data-ttu-id="eb4f8-106">Počínaje verzí .NET Core 3.0 si můžete myslet, ASP.NET Core 3.0 jako součást .NET Core.</span><span class="sxs-lookup"><span data-stu-id="eb4f8-106">Starting with the .NET Core 3.0 release, you can think of ASP.NET Core 3.0 as being part of .NET Core.</span></span>

<span data-ttu-id="eb4f8-107">Zákazníci používající ASP.NET Core s rozhraním .NET Framework mohou pokračovat plně podporovaným způsobem pomocí [verze 2.1 LTS](https://www.microsoft.com/net/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="eb4f8-107">Customers using ASP.NET Core with .NET Framework can continue in a fully supported fashion using the [2.1 LTS release](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span> <span data-ttu-id="eb4f8-108">Podpora a servis pro 2.1 pokračuje nejméně do srpna 21, 2021.</span><span class="sxs-lookup"><span data-stu-id="eb4f8-108">Support and servicing for 2.1 continues until at least August 21, 2021.</span></span> <span data-ttu-id="eb4f8-109">Toto datum je tři roky po prohlášení o vydání LTS podle [zásad podpory .NET](https://www.microsoft.com/net/platform/support-policy).</span><span class="sxs-lookup"><span data-stu-id="eb4f8-109">This date is three years after declaration of the LTS release per the [.NET Support Policy](https://www.microsoft.com/net/platform/support-policy).</span></span> <span data-ttu-id="eb4f8-110">Podpora balíčků ASP.NET Core 2.1 **v rozhraní .NET Framework** se rozšíří na neurčito, podobně jako [zásady údržby pro jiné ASP.NET architektury založené na balíčcích](https://dotnet.microsoft.com/platform/support/policy/aspnet).</span><span class="sxs-lookup"><span data-stu-id="eb4f8-110">Support for ASP.NET Core 2.1 packages **on .NET Framework** will extend indefinitely, similar to the [servicing policy for other package-based ASP.NET frameworks](https://dotnet.microsoft.com/platform/support/policy/aspnet).</span></span>

<span data-ttu-id="eb4f8-111">Další informace o přenosu z rozhraní .NET Framework do jádra .NET naleznete v [tématu Porting to .NET Core](~/docs/core/porting/index.md).</span><span class="sxs-lookup"><span data-stu-id="eb4f8-111">For more information about porting from .NET Framework to .NET Core, see [Porting to .NET Core](~/docs/core/porting/index.md).</span></span>

<span data-ttu-id="eb4f8-112">`Microsoft.Extensions`balíčky (například protokolování, vkládání závislostí a konfigurace) a jádro entity frameworku nejsou ovlivněny.</span><span class="sxs-lookup"><span data-stu-id="eb4f8-112">`Microsoft.Extensions` packages (such as logging, dependency injection, and configuration) and Entity Framework Core aren't affected.</span></span> <span data-ttu-id="eb4f8-113">Budou i nadále podporovat standard .NET.</span><span class="sxs-lookup"><span data-stu-id="eb4f8-113">They'll continue to support .NET Standard.</span></span>

<span data-ttu-id="eb4f8-114">Další informace o motivaci k této změně naleznete [v původním příspěvku blogu](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="eb4f8-114">For more information on the motivation for this change, see [the original blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="eb4f8-115">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="eb4f8-115">Version introduced</span></span>

<span data-ttu-id="eb4f8-116">3.0</span><span class="sxs-lookup"><span data-stu-id="eb4f8-116">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="eb4f8-117">Staré chování</span><span class="sxs-lookup"><span data-stu-id="eb4f8-117">Old behavior</span></span>

<span data-ttu-id="eb4f8-118">ASP.NET core aplikace může běžet na rozhraní .NET Core nebo .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eb4f8-118">ASP.NET Core apps could run on either .NET Core or .NET Framework.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="eb4f8-119">Nové chování</span><span class="sxs-lookup"><span data-stu-id="eb4f8-119">New behavior</span></span>

<span data-ttu-id="eb4f8-120">ASP.NET základní aplikace lze spustit pouze na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="eb4f8-120">ASP.NET Core apps can only be run on .NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="eb4f8-121">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="eb4f8-121">Recommended action</span></span>

<span data-ttu-id="eb4f8-122">Proveďte jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="eb4f8-122">Take one of the following actions:</span></span>

- <span data-ttu-id="eb4f8-123">Mějte svou aplikaci na ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="eb4f8-123">Keep your app on ASP.NET Core 2.1.</span></span>
- <span data-ttu-id="eb4f8-124">Migrujte aplikaci a závislosti do jádra .NET Core.</span><span class="sxs-lookup"><span data-stu-id="eb4f8-124">Migrate your app and dependencies to .NET Core.</span></span>

#### <a name="category"></a><span data-ttu-id="eb4f8-125">Kategorie</span><span class="sxs-lookup"><span data-stu-id="eb4f8-125">Category</span></span>

<span data-ttu-id="eb4f8-126">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="eb4f8-126">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="eb4f8-127">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="eb4f8-127">Affected APIs</span></span>

<span data-ttu-id="eb4f8-128">Žádný</span><span class="sxs-lookup"><span data-stu-id="eb4f8-128">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
