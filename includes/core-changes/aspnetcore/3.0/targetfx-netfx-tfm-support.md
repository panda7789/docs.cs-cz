---
ms.openlocfilehash: 4c676a185ff4a7a825acb059bf0a5842ca3922fc
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394158"
---
### <a name="target-framework-net-framework-support-dropped"></a><span data-ttu-id="25f34-101">Cílová architektura: Zahozená podpora .NET Framework</span><span class="sxs-lookup"><span data-stu-id="25f34-101">Target framework: .NET Framework support dropped</span></span>

<span data-ttu-id="25f34-102">Počínaje ASP.NET Core 3,0 .NET Framework je Nepodporovaná Cílová architektura.</span><span class="sxs-lookup"><span data-stu-id="25f34-102">Starting with ASP.NET Core 3.0, .NET Framework is an unsupported target framework.</span></span>

#### <a name="change-description"></a><span data-ttu-id="25f34-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="25f34-103">Change description</span></span>

<span data-ttu-id="25f34-104">.NET Framework 4,8 je poslední hlavní verzí .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="25f34-104">.NET Framework 4.8 is the last major version of .NET Framework.</span></span> <span data-ttu-id="25f34-105">Nové aplikace ASP.NET Core by měly být postavené na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="25f34-105">New ASP.NET Core apps should be built on .NET Core.</span></span> <span data-ttu-id="25f34-106">Od verze .NET Core 3,0 můžete si představit ASP.NET Core 3,0 jako součást .NET Core.</span><span class="sxs-lookup"><span data-stu-id="25f34-106">Starting with the .NET Core 3.0 release, you can think of ASP.NET Core 3.0 as being part of .NET Core.</span></span>

<span data-ttu-id="25f34-107">Zákazníci, kteří používají ASP.NET Core s .NET Framework, můžou v plně podporovaném způsobem i nadále používat [LTS vydání verze 2,1](https://www.microsoft.com/net/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="25f34-107">Customers using ASP.NET Core with .NET Framework can continue in a fully supported fashion using the [2.1 LTS release](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span> <span data-ttu-id="25f34-108">Podpora a údržba pro 2,1 pokračuje do 21. srpna 2021.</span><span class="sxs-lookup"><span data-stu-id="25f34-108">Support and servicing for 2.1 continues until at least August 21, 2021.</span></span> <span data-ttu-id="25f34-109">Toto datum je tři roky po deklaraci verze LTS podle [zásady podpory .NET](https://www.microsoft.com/net/platform/support-policy).</span><span class="sxs-lookup"><span data-stu-id="25f34-109">This date is three years after declaration of the LTS release per the [.NET Support Policy](https://www.microsoft.com/net/platform/support-policy).</span></span> <span data-ttu-id="25f34-110">Podpora pro balíčky ASP.NET Core 2,1 **v .NET Framework** se nebude zobrazovat po neomezenou dobu, podobně jako [zásady údržby pro jiné ASP.NET architektury založené na balíčku](https://dotnet.microsoft.com/platform/support/policy/aspnet).</span><span class="sxs-lookup"><span data-stu-id="25f34-110">Support for ASP.NET Core 2.1 packages **on .NET Framework** will extend indefinitely, similar to the [servicing policy for other package-based ASP.NET frameworks](https://dotnet.microsoft.com/platform/support/policy/aspnet).</span></span>

<span data-ttu-id="25f34-111">Další informace o přenosech z .NET Framework do .NET Core najdete v tématu [přenos do .NET Core](~/docs/core/porting/index.md).</span><span class="sxs-lookup"><span data-stu-id="25f34-111">For more information about porting from .NET Framework to .NET Core, see [Porting to .NET Core](~/docs/core/porting/index.md).</span></span>

<span data-ttu-id="25f34-112">balíčky `Microsoft.Extensions` (například protokolování, vkládání závislostí a konfigurace) a Entity Framework Core nejsou ovlivněny.</span><span class="sxs-lookup"><span data-stu-id="25f34-112">`Microsoft.Extensions` packages (such as logging, dependency injection, and configuration) and Entity Framework Core aren't affected.</span></span> <span data-ttu-id="25f34-113">Budou dál podporovat .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="25f34-113">They'll continue to support .NET Standard.</span></span>

<span data-ttu-id="25f34-114">Další informace o motivaci této změny najdete v [původním blogovém příspěvku](https://blogs.msdn.microsoft.com/webdev/2018/10/29/a-first-look-at-changes-coming-in-asp-net-core-3-0).</span><span class="sxs-lookup"><span data-stu-id="25f34-114">For more information on the motivation for this change, see [the original blog post](https://blogs.msdn.microsoft.com/webdev/2018/10/29/a-first-look-at-changes-coming-in-asp-net-core-3-0).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="25f34-115">Představená verze</span><span class="sxs-lookup"><span data-stu-id="25f34-115">Version introduced</span></span>

<span data-ttu-id="25f34-116">3.0</span><span class="sxs-lookup"><span data-stu-id="25f34-116">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="25f34-117">Staré chování</span><span class="sxs-lookup"><span data-stu-id="25f34-117">Old behavior</span></span>

<span data-ttu-id="25f34-118">Aplikace ASP.NET Core mohou běžet buď na rozhraní .NET Core, nebo v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="25f34-118">ASP.NET Core apps could run on either .NET Core or .NET Framework.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="25f34-119">Nové chování</span><span class="sxs-lookup"><span data-stu-id="25f34-119">New behavior</span></span>

<span data-ttu-id="25f34-120">Aplikace ASP.NET Core lze spustit pouze v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="25f34-120">ASP.NET Core apps can only be run on .NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="25f34-121">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="25f34-121">Recommended action</span></span>

<span data-ttu-id="25f34-122">Proveďte jednu z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="25f34-122">Take one of the following actions:</span></span>

- <span data-ttu-id="25f34-123">Udržujte svou aplikaci na ASP.NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="25f34-123">Keep your app on ASP.NET Core 2.1.</span></span>
- <span data-ttu-id="25f34-124">Migrujte svoji aplikaci a závislosti do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="25f34-124">Migrate your app and dependencies to .NET Core.</span></span>

#### <a name="category"></a><span data-ttu-id="25f34-125">Kategorie</span><span class="sxs-lookup"><span data-stu-id="25f34-125">Category</span></span>

<span data-ttu-id="25f34-126">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="25f34-126">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="25f34-127">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="25f34-127">Affected APIs</span></span>

<span data-ttu-id="25f34-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="25f34-128">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
