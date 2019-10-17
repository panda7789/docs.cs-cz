---
ms.openlocfilehash: 8479168b64153d3c729f8814a2649df8d46f2135
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394428"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a><span data-ttu-id="6355b-101">Razor: kompilace za běhu byla přesunuta do balíčku</span><span class="sxs-lookup"><span data-stu-id="6355b-101">Razor: Runtime compilation moved to a package</span></span>

<span data-ttu-id="6355b-102">Podpora pro kompilaci za běhu zobrazení Razor a Razor Pages se přesunula do samostatného balíčku.</span><span class="sxs-lookup"><span data-stu-id="6355b-102">Support for runtime compilation of Razor views and Razor Pages has moved to a separate package.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6355b-103">Představená verze</span><span class="sxs-lookup"><span data-stu-id="6355b-103">Version introduced</span></span>

<span data-ttu-id="6355b-104">3.0</span><span class="sxs-lookup"><span data-stu-id="6355b-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6355b-105">Staré chování</span><span class="sxs-lookup"><span data-stu-id="6355b-105">Old behavior</span></span>

<span data-ttu-id="6355b-106">Kompilace za běhu je k dispozici bez nutnosti dalších balíčků.</span><span class="sxs-lookup"><span data-stu-id="6355b-106">Runtime compilation is available without needing additional packages.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="6355b-107">Nové chování</span><span class="sxs-lookup"><span data-stu-id="6355b-107">New behavior</span></span>

<span data-ttu-id="6355b-108">Funkčnost byla přesunuta do balíčku `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`.</span><span class="sxs-lookup"><span data-stu-id="6355b-108">The functionality has been moved to the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>

<span data-ttu-id="6355b-109">Následující rozhraní API byly dříve k dispozici v `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` pro podporu kompilace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="6355b-109">The following APIs were previously available in `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` to support runtime compilation.</span></span> <span data-ttu-id="6355b-110">Rozhraní API jsou nyní k dispozici prostřednictvím `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`.</span><span class="sxs-lookup"><span data-stu-id="6355b-110">The APIs are now available via `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`.</span></span>

- `RazorViewEngineOptions.FileProviders` -> `MvcRazorRuntimeCompilationOptions.FileProviders`
- `RazorViewEngineOptions.AdditionalCompilationReferences` -> `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`

<span data-ttu-id="6355b-111">Kromě toho se odebrala `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange`.</span><span class="sxs-lookup"><span data-stu-id="6355b-111">In addition, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` has been removed.</span></span> <span data-ttu-id="6355b-112">Opětovná kompilace při změnách souborů je ve výchozím nastavení povolená odkazem na balíček `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`.</span><span class="sxs-lookup"><span data-stu-id="6355b-112">Recompilation on file changes is enabled by default by referencing the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6355b-113">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="6355b-113">Reason for change</span></span>

<span data-ttu-id="6355b-114">Tato změna byla nutná pro odebrání závislostí sdíleného rozhraní ASP.NET Core v Roslyn.</span><span class="sxs-lookup"><span data-stu-id="6355b-114">This change was necessary to remove the ASP.NET Core shared framework dependency on Roslyn.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6355b-115">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="6355b-115">Recommended action</span></span>

<span data-ttu-id="6355b-116">Aplikace, které vyžadují kompilaci za běhu nebo opětovnou kompilaci souborů Razor, by měly provést následující kroky:</span><span class="sxs-lookup"><span data-stu-id="6355b-116">Apps that require runtime compilation or recompilation of Razor files should take the following steps:</span></span>

1. <span data-ttu-id="6355b-117">Přidejte odkaz na balíček `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`.</span><span class="sxs-lookup"><span data-stu-id="6355b-117">Add a reference to the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>
1. <span data-ttu-id="6355b-118">Aktualizujte metodu `Startup.ConfigureServices` projektu tak, aby zahrnovala volání `AddMvcRazorRuntimeCompilation`.</span><span class="sxs-lookup"><span data-stu-id="6355b-118">Update the project's `Startup.ConfigureServices` method to include a call to `AddMvcRazorRuntimeCompilation`.</span></span> <span data-ttu-id="6355b-119">Například v `Startup.ConfigureServices`:</span><span class="sxs-lookup"><span data-stu-id="6355b-119">For example, in `Startup.ConfigureServices`:</span></span>

    ```csharp
    services.AddMvc()
        .AddMvcRazorRuntimeCompilation();
    ```

#### <a name="category"></a><span data-ttu-id="6355b-120">Kategorie</span><span class="sxs-lookup"><span data-stu-id="6355b-120">Category</span></span>

<span data-ttu-id="6355b-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6355b-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6355b-122">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="6355b-122">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions?displayProperty=fullName>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`

-->
