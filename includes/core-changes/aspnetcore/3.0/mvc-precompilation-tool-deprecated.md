---
ms.openlocfilehash: 1e081c9f37fbd7ab754ce44ba89d7aa5cabfc219
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902043"
---
### <a name="mvc-precompilation-tool-deprecated"></a><span data-ttu-id="e2681-101">MVC: Nástroj předběžné kompilace se zastaral</span><span class="sxs-lookup"><span data-stu-id="e2681-101">MVC: Precompilation tool deprecated</span></span>

<span data-ttu-id="e2681-102">V ASP.NET Core 1.1 byl zaveden balíček `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (MVC precompilation tool), který přidává podporu pro kompilaci souborů Razor (*.cshtml).*</span><span class="sxs-lookup"><span data-stu-id="e2681-102">In ASP.NET Core 1.1, the `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (MVC precompilation tool) package was introduced to add support for publish-time compilation of Razor files (*.cshtml* files).</span></span> <span data-ttu-id="e2681-103">V ASP.NET Core 2.1 byla zavedena [sada Razor SDK,](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) která rozšiřuje funkce nástroje pro předkompilaci.</span><span class="sxs-lookup"><span data-stu-id="e2681-103">In ASP.NET Core 2.1, the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) was introduced to expand upon features of the precompilation tool.</span></span> <span data-ttu-id="e2681-104">Sada Razor SDK přidala podporu pro kompilaci souborů Razor v době sestavení a publikování.</span><span class="sxs-lookup"><span data-stu-id="e2681-104">The Razor SDK added support for build- and publish-time compilation of Razor files.</span></span> <span data-ttu-id="e2681-105">Sada SDK ověřuje správnost souborů *.cshtml* v době sestavení a zároveň zlepšuje dobu spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="e2681-105">The SDK verifies the correctness of *.cshtml* files at build time while improving on app startup time.</span></span> <span data-ttu-id="e2681-106">Sada Razor SDK je ve výchozím nastavení zapnutá a není nutné žádné gesto, které by ji začalo používat.</span><span class="sxs-lookup"><span data-stu-id="e2681-106">The Razor SDK is on by default, and no gesture is required to start using it.</span></span>

<span data-ttu-id="e2681-107">V ASP.NET Core 3.0 byl ASP.NET nástroj předkompilace MVC core 1.1 éry odebrán.</span><span class="sxs-lookup"><span data-stu-id="e2681-107">In ASP.NET Core 3.0, the ASP.NET Core 1.1-era MVC precompilation tool was removed.</span></span> <span data-ttu-id="e2681-108">Starší verze balíčků budou i nadále dostávat důležité opravy chyb a zabezpečení ve verzi opravy.</span><span class="sxs-lookup"><span data-stu-id="e2681-108">Earlier package versions will continue receiving important bug and security fixes in the patch release.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e2681-109">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="e2681-109">Version introduced</span></span>

<span data-ttu-id="e2681-110">3.0</span><span class="sxs-lookup"><span data-stu-id="e2681-110">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e2681-111">Staré chování</span><span class="sxs-lookup"><span data-stu-id="e2681-111">Old behavior</span></span>

<span data-ttu-id="e2681-112">Balíček `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` byl použit k předkompilaci zobrazení MVC Razor.</span><span class="sxs-lookup"><span data-stu-id="e2681-112">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package was used to pre-compile MVC Razor views.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="e2681-113">Nové chování</span><span class="sxs-lookup"><span data-stu-id="e2681-113">New behavior</span></span>

<span data-ttu-id="e2681-114">Sada Razor SDK nativně podporuje tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="e2681-114">The Razor SDK natively supports this functionality.</span></span> <span data-ttu-id="e2681-115">Balíček `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` již není aktualizován.</span><span class="sxs-lookup"><span data-stu-id="e2681-115">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package is no longer updated.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e2681-116">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="e2681-116">Reason for change</span></span>

<span data-ttu-id="e2681-117">Sada Razor SDK poskytuje další funkce a ověřuje správnost souborů *.cshtml* v době sestavení.</span><span class="sxs-lookup"><span data-stu-id="e2681-117">The Razor SDK provides more functionality and verifies the correctness of *.cshtml* files at build time.</span></span> <span data-ttu-id="e2681-118">Sada SDK také zlepšuje dobu spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="e2681-118">The SDK also improves app startup time.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e2681-119">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="e2681-119">Recommended action</span></span>

<span data-ttu-id="e2681-120">Pro uživatele ASP.NET Jádrem 2.1 nebo novějším aktualizujte tak, aby používala nativní podporu pro předkompilaci v [sada Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0).</span><span class="sxs-lookup"><span data-stu-id="e2681-120">For users of ASP.NET Core 2.1 or later, update to use the native support for precompilation in the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0).</span></span> <span data-ttu-id="e2681-121">Pokud chyby nebo chybějící funkce brání migraci do sady Razor SDK, otevřete problém na [adrese dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span><span class="sxs-lookup"><span data-stu-id="e2681-121">If bugs or missing features prevent migration to the Razor SDK, open an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span>

#### <a name="category"></a><span data-ttu-id="e2681-122">Kategorie</span><span class="sxs-lookup"><span data-stu-id="e2681-122">Category</span></span>

<span data-ttu-id="e2681-123">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e2681-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e2681-124">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e2681-124">Affected APIs</span></span>

<span data-ttu-id="e2681-125">Žádný</span><span class="sxs-lookup"><span data-stu-id="e2681-125">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis

-->
