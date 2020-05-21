---
ms.openlocfilehash: 8395428e1729a00fc1af72cf53fe689ee95b5fdf
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721121"
---
### <a name="mvc-precompilation-tool-deprecated"></a><span data-ttu-id="d1abf-101">MVC: zastaralý nástroj předkompilace</span><span class="sxs-lookup"><span data-stu-id="d1abf-101">MVC: Precompilation tool deprecated</span></span>

<span data-ttu-id="d1abf-102">V ASP.NET Core 1,1 `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` byl vytvořen balíček nástroje pro předkompilaci MVC, který přidává podporu pro kompilaci souborů Razor v době publikování (soubory *. cshtml* ).</span><span class="sxs-lookup"><span data-stu-id="d1abf-102">In ASP.NET Core 1.1, the `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (MVC precompilation tool) package was introduced to add support for publish-time compilation of Razor files (*.cshtml* files).</span></span> <span data-ttu-id="d1abf-103">V ASP.NET Core 2,1 byla [sada Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) představena za účelem rozšíření funkcí nástroje předkompilace.</span><span class="sxs-lookup"><span data-stu-id="d1abf-103">In ASP.NET Core 2.1, the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) was introduced to expand upon features of the precompilation tool.</span></span> <span data-ttu-id="d1abf-104">Sada Razor SDK přidala podporu pro kompilaci souborů Razor při sestavení a publikování.</span><span class="sxs-lookup"><span data-stu-id="d1abf-104">The Razor SDK added support for build- and publish-time compilation of Razor files.</span></span> <span data-ttu-id="d1abf-105">Sada SDK ověřuje správnost souborů *. cshtml* při sestavování a současně zlepšuje čas spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="d1abf-105">The SDK verifies the correctness of *.cshtml* files at build time while improving on app startup time.</span></span> <span data-ttu-id="d1abf-106">Sada Razor SDK je ve výchozím nastavení zapnutá a není nutná žádná gesta, která by ji mohla začít používat.</span><span class="sxs-lookup"><span data-stu-id="d1abf-106">The Razor SDK is on by default, and no gesture is required to start using it.</span></span>

<span data-ttu-id="d1abf-107">V ASP.NET Core 3,0 byl odebrán nástroj předkompilace sady ASP.NET Core 1,1-éry MVC.</span><span class="sxs-lookup"><span data-stu-id="d1abf-107">In ASP.NET Core 3.0, the ASP.NET Core 1.1-era MVC precompilation tool was removed.</span></span> <span data-ttu-id="d1abf-108">Starší verze balíčků budou dál získávat důležité opravy chyb a zabezpečení ve verzi opravy.</span><span class="sxs-lookup"><span data-stu-id="d1abf-108">Earlier package versions will continue receiving important bug and security fixes in the patch release.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d1abf-109">Představená verze</span><span class="sxs-lookup"><span data-stu-id="d1abf-109">Version introduced</span></span>

<span data-ttu-id="d1abf-110">3.0</span><span class="sxs-lookup"><span data-stu-id="d1abf-110">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d1abf-111">Staré chování</span><span class="sxs-lookup"><span data-stu-id="d1abf-111">Old behavior</span></span>

<span data-ttu-id="d1abf-112">`Microsoft.AspNetCore.Mvc.Razor.ViewCompilation`Balíček se použil k předkompilování zobrazení MVC Razor.</span><span class="sxs-lookup"><span data-stu-id="d1abf-112">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package was used to pre-compile MVC Razor views.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d1abf-113">Nové chování</span><span class="sxs-lookup"><span data-stu-id="d1abf-113">New behavior</span></span>

<span data-ttu-id="d1abf-114">Tato funkce je nativně podporovaná sadou SDK Razor.</span><span class="sxs-lookup"><span data-stu-id="d1abf-114">The Razor SDK natively supports this functionality.</span></span> <span data-ttu-id="d1abf-115">`Microsoft.AspNetCore.Mvc.Razor.ViewCompilation`Balíček už není aktualizovaný.</span><span class="sxs-lookup"><span data-stu-id="d1abf-115">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package is no longer updated.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d1abf-116">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="d1abf-116">Reason for change</span></span>

<span data-ttu-id="d1abf-117">Sada Razor SDK poskytuje více funkcí a ověřuje správnost souborů *. cshtml* v době sestavení.</span><span class="sxs-lookup"><span data-stu-id="d1abf-117">The Razor SDK provides more functionality and verifies the correctness of *.cshtml* files at build time.</span></span> <span data-ttu-id="d1abf-118">Sada SDK také vylepšuje čas spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="d1abf-118">The SDK also improves app startup time.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d1abf-119">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="d1abf-119">Recommended action</span></span>

<span data-ttu-id="d1abf-120">Pro uživatele ASP.NET Core 2,1 nebo novější verzi aktualizujte, aby používaly nativní podporu předkompilace v [sadě Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0).</span><span class="sxs-lookup"><span data-stu-id="d1abf-120">For users of ASP.NET Core 2.1 or later, update to use the native support for precompilation in the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0).</span></span> <span data-ttu-id="d1abf-121">Pokud chyby nebo chybějící funkce brání migraci do sady Razor SDK, otevřete problém v [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span><span class="sxs-lookup"><span data-stu-id="d1abf-121">If bugs or missing features prevent migration to the Razor SDK, open an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span>

#### <a name="category"></a><span data-ttu-id="d1abf-122">Kategorie</span><span class="sxs-lookup"><span data-stu-id="d1abf-122">Category</span></span>

<span data-ttu-id="d1abf-123">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d1abf-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d1abf-124">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="d1abf-124">Affected APIs</span></span>

<span data-ttu-id="d1abf-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="d1abf-125">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
