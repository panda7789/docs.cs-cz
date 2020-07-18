---
ms.openlocfilehash: 17a167e5245914329195d61ab45ae2d8ecb617d6
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416259"
---
### <a name="blazor-target-framework-of-nuget-packages-changed"></a><span data-ttu-id="9170a-101">Blazor: Cílová architektura balíčků NuGet se změnila</span><span class="sxs-lookup"><span data-stu-id="9170a-101">Blazor: Target framework of NuGet packages changed</span></span>

<span data-ttu-id="9170a-102">Projekty Blazor 3,2 WebAssembly byly zkompilovány do cíle .NET Standard 2,1 ( `<TargetFramework>netstandard2.1</TargetFramework>` ).</span><span class="sxs-lookup"><span data-stu-id="9170a-102">Blazor 3.2 WebAssembly projects were compiled to target .NET Standard 2.1 (`<TargetFramework>netstandard2.1</TargetFramework>`).</span></span> <span data-ttu-id="9170a-103">V ASP.NET Core 5,0 jsou oba projekty Blazor serveru i Blazor pro sestavení na platformě .NET 5,0 ( `<TargetFramework>net5.0</TargetFramework>` ).</span><span class="sxs-lookup"><span data-stu-id="9170a-103">In ASP.NET Core 5.0, both Blazor Server and Blazor WebAssembly projects target .NET 5.0 (`<TargetFramework>net5.0</TargetFramework>`).</span></span> <span data-ttu-id="9170a-104">Pro lepší zarovnání s cílovým rozhraním se změna v následujících balíčcích Blazor už necílí .NET Standard 2,1:</span><span class="sxs-lookup"><span data-stu-id="9170a-104">To better align with the target framework change, the following Blazor packages no longer target .NET Standard 2.1:</span></span>

* [<span data-ttu-id="9170a-105">Microsoft. AspNetCore. Components</span><span class="sxs-lookup"><span data-stu-id="9170a-105">Microsoft.AspNetCore.Components</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components)
* [<span data-ttu-id="9170a-106">Microsoft. AspNetCore. Components. Authorization</span><span class="sxs-lookup"><span data-stu-id="9170a-106">Microsoft.AspNetCore.Components.Authorization</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Authorization)
* [<span data-ttu-id="9170a-107">Microsoft. AspNetCore. Components. Forms</span><span class="sxs-lookup"><span data-stu-id="9170a-107">Microsoft.AspNetCore.Components.Forms</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Forms)
* [<span data-ttu-id="9170a-108">Microsoft. AspNetCore. Components. Web</span><span class="sxs-lookup"><span data-stu-id="9170a-108">Microsoft.AspNetCore.Components.Web</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web)
* [<span data-ttu-id="9170a-109">Microsoft. AspNetCore. Components. WebAssembly</span><span class="sxs-lookup"><span data-stu-id="9170a-109">Microsoft.AspNetCore.Components.WebAssembly</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly)
* [<span data-ttu-id="9170a-110">Microsoft. AspNetCore. Components. WebAssembly. Authentication</span><span class="sxs-lookup"><span data-stu-id="9170a-110">Microsoft.AspNetCore.Components.WebAssembly.Authentication</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly.Authentication)
* [<span data-ttu-id="9170a-111">Microsoft.JSspolupráce</span><span class="sxs-lookup"><span data-stu-id="9170a-111">Microsoft.JSInterop</span></span>](https://www.nuget.org/packages/Microsoft.JSInterop)
* [<span data-ttu-id="9170a-112">Microsoft.JSInterop. WebAssembly</span><span class="sxs-lookup"><span data-stu-id="9170a-112">Microsoft.JSInterop.WebAssembly</span></span>](https://www.nuget.org/packages/Microsoft.JSInterop.WebAssembly)
* [<span data-ttu-id="9170a-113">Microsoft. Authentication. WebAssembly. Msal</span><span class="sxs-lookup"><span data-stu-id="9170a-113">Microsoft.Authentication.WebAssembly.Msal</span></span>](https://www.nuget.org/packages/Microsoft.Authentication.WebAssembly.Msal)

<span data-ttu-id="9170a-114">Diskuzi najdete v tématu problém GitHubu [dotnet/aspnetcore # 23424](https://github.com/dotnet/aspnetcore/issues/23424).</span><span class="sxs-lookup"><span data-stu-id="9170a-114">For discussion, see GitHub issue [dotnet/aspnetcore#23424](https://github.com/dotnet/aspnetcore/issues/23424).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9170a-115">Představená verze</span><span class="sxs-lookup"><span data-stu-id="9170a-115">Version introduced</span></span>

<span data-ttu-id="9170a-116">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="9170a-116">5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="9170a-117">Staré chování</span><span class="sxs-lookup"><span data-stu-id="9170a-117">Old behavior</span></span>

<span data-ttu-id="9170a-118">V Blazor 3,1 a 3,2 jsou cílové balíčky .NET Standard 2,1 a .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="9170a-118">In Blazor 3.1 and 3.2, packages target .NET Standard 2.1 and .NET Core 3.1.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="9170a-119">Nové chování</span><span class="sxs-lookup"><span data-stu-id="9170a-119">New behavior</span></span>

<span data-ttu-id="9170a-120">V ASP.NET Core 5,0 balíčky cílí na rozhraní .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="9170a-120">In ASP.NET Core 5.0, packages target .NET 5.0.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="9170a-121">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="9170a-121">Reason for change</span></span>

<span data-ttu-id="9170a-122">Změna byla provedena pro lepší zarovnání s požadavky rozhraní .NET Target Framework.</span><span class="sxs-lookup"><span data-stu-id="9170a-122">The change was made to better align with .NET target framework requirements.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9170a-123">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="9170a-123">Recommended action</span></span>

<span data-ttu-id="9170a-124">Projekty Blazor 3,2 WebAssembly by měly cílit na .NET 5,0 jako součást aktualizace odkazů na balíčky na 5. x.x.</span><span class="sxs-lookup"><span data-stu-id="9170a-124">Blazor 3.2 WebAssembly projects should target .NET 5.0 as part of updating their package references to 5.x.x.</span></span> <span data-ttu-id="9170a-125">Knihovny, které odkazují na jeden z těchto balíčků, mohou cílit buď na rozhraní .NET 5,0, nebo na více cílů v závislosti na jejich požadavcích.</span><span class="sxs-lookup"><span data-stu-id="9170a-125">Libraries that reference one of these packages can either target .NET 5.0 or multi-target depending on their requirements.</span></span>

#### <a name="category"></a><span data-ttu-id="9170a-126">Kategorie</span><span class="sxs-lookup"><span data-stu-id="9170a-126">Category</span></span>

<span data-ttu-id="9170a-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9170a-127">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9170a-128">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="9170a-128">Affected APIs</span></span>

<span data-ttu-id="9170a-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="9170a-129">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
