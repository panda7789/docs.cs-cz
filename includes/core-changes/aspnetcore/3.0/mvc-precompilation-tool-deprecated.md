---
ms.openlocfilehash: 641233df165a1c2208a2185f2b6e99077f9a59d3
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394393"
---
### <a name="mvc-precompilation-tool-deprecated"></a><span data-ttu-id="8c2cd-101">MVC: zastaralý nástroj předkompilace</span><span class="sxs-lookup"><span data-stu-id="8c2cd-101">MVC: Precompilation tool deprecated</span></span>

<span data-ttu-id="8c2cd-102">V ASP.NET Core 1,1 byl zaveden balíček `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (nástroj předkompilace MVC), který přidává podporu pro kompilaci souborů Razor v době publikování (soubory *. cshtml* ).</span><span class="sxs-lookup"><span data-stu-id="8c2cd-102">In ASP.NET Core 1.1, the `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (MVC precompilation tool) package was introduced to add support for publish-time compilation of Razor files (*.cshtml* files).</span></span> <span data-ttu-id="8c2cd-103">V ASP.NET Core 2,1 byla [sada Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) představena za účelem rozšíření funkcí nástroje předkompilace.</span><span class="sxs-lookup"><span data-stu-id="8c2cd-103">In ASP.NET Core 2.1, the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) was introduced to expand upon features of the precompilation tool.</span></span> <span data-ttu-id="8c2cd-104">Sada Razor SDK přidala podporu pro kompilaci souborů Razor při sestavení a publikování.</span><span class="sxs-lookup"><span data-stu-id="8c2cd-104">The Razor SDK added support for build- and publish-time compilation of Razor files.</span></span> <span data-ttu-id="8c2cd-105">Sada SDK ověřuje správnost souborů *. cshtml* při sestavování a současně zlepšuje čas spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="8c2cd-105">The SDK verifies the correctness of *.cshtml* files at build time while improving on app startup time.</span></span> <span data-ttu-id="8c2cd-106">Sada Razor SDK je ve výchozím nastavení zapnutá a není nutná žádná gesta, která by ji mohla začít používat.</span><span class="sxs-lookup"><span data-stu-id="8c2cd-106">The Razor SDK is on by default, and no gesture is required to start using it.</span></span>

<span data-ttu-id="8c2cd-107">V ASP.NET Core 3,0 byl odebrán nástroj předkompilace sady ASP.NET Core 1,1-éry MVC.</span><span class="sxs-lookup"><span data-stu-id="8c2cd-107">In ASP.NET Core 3.0, the ASP.NET Core 1.1-era MVC precompilation tool was removed.</span></span> <span data-ttu-id="8c2cd-108">Starší verze balíčků budou dál získávat důležité opravy chyb a zabezpečení ve verzi opravy.</span><span class="sxs-lookup"><span data-stu-id="8c2cd-108">Earlier package versions will continue receiving important bug and security fixes in the patch release.</span></span> 

#### <a name="version-introduced"></a><span data-ttu-id="8c2cd-109">Představená verze</span><span class="sxs-lookup"><span data-stu-id="8c2cd-109">Version introduced</span></span>

<span data-ttu-id="8c2cd-110">3.0</span><span class="sxs-lookup"><span data-stu-id="8c2cd-110">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="8c2cd-111">Staré chování</span><span class="sxs-lookup"><span data-stu-id="8c2cd-111">Old behavior</span></span>

<span data-ttu-id="8c2cd-112">Balíček `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` byl použit k předkompilování zobrazení MVC Razor.</span><span class="sxs-lookup"><span data-stu-id="8c2cd-112">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package was used to pre-compile MVC Razor views.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="8c2cd-113">Nové chování</span><span class="sxs-lookup"><span data-stu-id="8c2cd-113">New behavior</span></span>

<span data-ttu-id="8c2cd-114">Tato funkce je nativně podporovaná sadou SDK Razor.</span><span class="sxs-lookup"><span data-stu-id="8c2cd-114">The Razor SDK natively supports this functionality.</span></span> <span data-ttu-id="8c2cd-115">Balíček `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` už není aktualizovaný.</span><span class="sxs-lookup"><span data-stu-id="8c2cd-115">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package is no longer updated.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="8c2cd-116">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="8c2cd-116">Reason for change</span></span>

<span data-ttu-id="8c2cd-117">Sada Razor SDK poskytuje více funkcí a ověřuje správnost souborů *. cshtml* v době sestavení.</span><span class="sxs-lookup"><span data-stu-id="8c2cd-117">The Razor SDK provides more functionality and verifies the correctness of *.cshtml* files at build time.</span></span> <span data-ttu-id="8c2cd-118">Sada SDK také vylepšuje čas spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="8c2cd-118">The SDK also improves app startup time.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8c2cd-119">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="8c2cd-119">Recommended action</span></span>

<span data-ttu-id="8c2cd-120">Pro uživatele ASP.NET Core 2,1 nebo novější verzi aktualizujte, aby používaly nativní podporu předkompilace v [sadě Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0).</span><span class="sxs-lookup"><span data-stu-id="8c2cd-120">For users of ASP.NET Core 2.1 or later, update to use the native support for precompilation in the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0).</span></span> <span data-ttu-id="8c2cd-121">Pokud chyby nebo chybějící funkce brání migraci do sady Razor SDK, otevřete problém v [ASPNET/AspNetCore](https://github.com/aspnet/AspNetCore/issues).</span><span class="sxs-lookup"><span data-stu-id="8c2cd-121">If bugs or missing features prevent migration to the Razor SDK, open an issue at [aspnet/AspNetCore](https://github.com/aspnet/AspNetCore/issues).</span></span>

#### <a name="category"></a><span data-ttu-id="8c2cd-122">Kategorie</span><span class="sxs-lookup"><span data-stu-id="8c2cd-122">Category</span></span>

<span data-ttu-id="8c2cd-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8c2cd-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8c2cd-124">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="8c2cd-124">Affected APIs</span></span>

<span data-ttu-id="8c2cd-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="8c2cd-125">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis

-->