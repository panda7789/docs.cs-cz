---
ms.openlocfilehash: cd13e7560ee98e0c862c5e2293521c6aaa273455
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344279"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a><span data-ttu-id="a2d4d-101">Razor: kompilace za běhu byla přesunuta do balíčku</span><span class="sxs-lookup"><span data-stu-id="a2d4d-101">Razor: Runtime compilation moved to a package</span></span>

<span data-ttu-id="a2d4d-102">Podpora pro kompilaci za běhu zobrazení Razor a Razor Pages se přesunula do samostatného balíčku.</span><span class="sxs-lookup"><span data-stu-id="a2d4d-102">Support for runtime compilation of Razor views and Razor Pages has moved to a separate package.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a2d4d-103">Představená verze</span><span class="sxs-lookup"><span data-stu-id="a2d4d-103">Version introduced</span></span>

<span data-ttu-id="a2d4d-104">3,0</span><span class="sxs-lookup"><span data-stu-id="a2d4d-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a2d4d-105">Staré chování</span><span class="sxs-lookup"><span data-stu-id="a2d4d-105">Old behavior</span></span>

<span data-ttu-id="a2d4d-106">Kompilace za běhu je k dispozici bez nutnosti dalších balíčků.</span><span class="sxs-lookup"><span data-stu-id="a2d4d-106">Runtime compilation is available without needing additional packages.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a2d4d-107">Nové chování</span><span class="sxs-lookup"><span data-stu-id="a2d4d-107">New behavior</span></span>

<span data-ttu-id="a2d4d-108">Funkce se přesunula do balíčku [Microsoft. AspNetCore. Mvc. Razor. RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/) .</span><span class="sxs-lookup"><span data-stu-id="a2d4d-108">The functionality has been moved to the [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/) package.</span></span>

<span data-ttu-id="a2d4d-109">Následující rozhraní API byly dříve k dispozici v `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` pro podporu kompilace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="a2d4d-109">The following APIs were previously available in `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` to support runtime compilation.</span></span> <span data-ttu-id="a2d4d-110">Rozhraní API jsou nyní k dispozici prostřednictvím `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`.</span><span class="sxs-lookup"><span data-stu-id="a2d4d-110">The APIs are now available via `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`.</span></span>

- <span data-ttu-id="a2d4d-111">`RazorViewEngineOptions.FileProviders` je teď `MvcRazorRuntimeCompilationOptions.FileProviders`</span><span class="sxs-lookup"><span data-stu-id="a2d4d-111">`RazorViewEngineOptions.FileProviders` is now `MvcRazorRuntimeCompilationOptions.FileProviders`</span></span>
- <span data-ttu-id="a2d4d-112">`RazorViewEngineOptions.AdditionalCompilationReferences` je teď `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`</span><span class="sxs-lookup"><span data-stu-id="a2d4d-112">`RazorViewEngineOptions.AdditionalCompilationReferences` is now `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`</span></span>

<span data-ttu-id="a2d4d-113">Kromě toho se odebral `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange`.</span><span class="sxs-lookup"><span data-stu-id="a2d4d-113">In addition, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` has been removed.</span></span> <span data-ttu-id="a2d4d-114">Opětovná kompilace při změnách souborů je ve výchozím nastavení povolená odkazem na balíček `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`.</span><span class="sxs-lookup"><span data-stu-id="a2d4d-114">Recompilation on file changes is enabled by default by referencing the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a2d4d-115">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="a2d4d-115">Reason for change</span></span>

<span data-ttu-id="a2d4d-116">Tato změna byla nutná pro odebrání závislostí sdíleného rozhraní ASP.NET Core v Roslyn.</span><span class="sxs-lookup"><span data-stu-id="a2d4d-116">This change was necessary to remove the ASP.NET Core shared framework dependency on Roslyn.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a2d4d-117">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="a2d4d-117">Recommended action</span></span>

<span data-ttu-id="a2d4d-118">Aplikace, které vyžadují kompilaci za běhu nebo opětovnou kompilaci souborů Razor, by měly provést následující kroky:</span><span class="sxs-lookup"><span data-stu-id="a2d4d-118">Apps that require runtime compilation or recompilation of Razor files should take the following steps:</span></span>

1. <span data-ttu-id="a2d4d-119">Přidejte odkaz na balíček `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`.</span><span class="sxs-lookup"><span data-stu-id="a2d4d-119">Add a reference to the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>
1. <span data-ttu-id="a2d4d-120">Aktualizujte metodu `Startup.ConfigureServices` projektu tak, aby zahrnovala volání `AddRazorRuntimeCompilation`.</span><span class="sxs-lookup"><span data-stu-id="a2d4d-120">Update the project's `Startup.ConfigureServices` method to include a call to `AddRazorRuntimeCompilation`.</span></span> <span data-ttu-id="a2d4d-121">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a2d4d-121">For example:</span></span>

    ```csharp
    services.AddMvc()
        .AddRazorRuntimeCompilation();
    ```

#### <a name="category"></a><span data-ttu-id="a2d4d-122">Kategorie</span><span class="sxs-lookup"><span data-stu-id="a2d4d-122">Category</span></span>

<span data-ttu-id="a2d4d-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a2d4d-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a2d4d-124">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="a2d4d-124">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions?displayProperty=fullName>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`

-->
