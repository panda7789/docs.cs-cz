---
ms.openlocfilehash: 5741e8cdd51e00d5459c4c1032a56682429aab17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901833"
---
### <a name="mvc-pubternal-types-changed-to-internal"></a><span data-ttu-id="41867-101">MVC: "Pubternal" typy změněny na vnitřní</span><span class="sxs-lookup"><span data-stu-id="41867-101">MVC: "Pubternal" types changed to internal</span></span>

<span data-ttu-id="41867-102">V ASP.NET Core 3.0 byly všechny typy pubternal v MVC aktualizovány tak, aby byly `public` buď v podporovaném oboru názvů, nebo `internal` podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="41867-102">In ASP.NET Core 3.0, all "pubternal" types in MVC were updated to either be `public` in a supported namespace or `internal` as appropriate.</span></span>

#### <a name="change-description"></a><span data-ttu-id="41867-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="41867-103">Change description</span></span>

<span data-ttu-id="41867-104">V ASP.NET Core jsou typy "pubternal" deklarovány jako, `public` ale jsou umístěny v oboru názvů `.Internal`s uznanou suffixed.</span><span class="sxs-lookup"><span data-stu-id="41867-104">In ASP.NET Core, "pubternal" types are declared as `public` but reside in a `.Internal`-suffixed namespace.</span></span> <span data-ttu-id="41867-105">Zatímco tyto `public`typy jsou , nemají žádné zásady podpory a jsou předmětem změny.</span><span class="sxs-lookup"><span data-stu-id="41867-105">While these types are `public`, they have no support policy and are subject to breaking changes.</span></span> <span data-ttu-id="41867-106">Bohužel náhodné použití těchto typů bylo běžné, což má za následek porušení změn těchto projektů a omezení schopnosti udržovat rámec.</span><span class="sxs-lookup"><span data-stu-id="41867-106">Unfortunately, accidental use of these types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="41867-107">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="41867-107">Version introduced</span></span>

<span data-ttu-id="41867-108">3.0</span><span class="sxs-lookup"><span data-stu-id="41867-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="41867-109">Staré chování</span><span class="sxs-lookup"><span data-stu-id="41867-109">Old behavior</span></span>

<span data-ttu-id="41867-110">Některé typy v MVC `public` `.Internal` byly, ale v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="41867-110">Some types in MVC were `public` but in a `.Internal` namespace.</span></span> <span data-ttu-id="41867-111">Tyto typy neměly žádné zásady podpory a byly předmětem porušení změn.</span><span class="sxs-lookup"><span data-stu-id="41867-111">These types had no support policy and were subject to breaking changes.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="41867-112">Nové chování</span><span class="sxs-lookup"><span data-stu-id="41867-112">New behavior</span></span>

<span data-ttu-id="41867-113">Všechny tyto typy jsou `public` aktualizovány buď tak, `internal`aby byly v podporovaném oboru názvů, nebo označeny jako .</span><span class="sxs-lookup"><span data-stu-id="41867-113">All such types are updated either to be `public` in a supported namespace or marked as `internal`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="41867-114">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="41867-114">Reason for change</span></span>

<span data-ttu-id="41867-115">Náhodné použití typů "pubternal" bylo běžné, což vedlo k porušení změn těchto projektů a omezení schopnosti udržovat rámec.</span><span class="sxs-lookup"><span data-stu-id="41867-115">Accidental use of the "pubternal" types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="41867-116">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="41867-116">Recommended action</span></span>

<span data-ttu-id="41867-117">Pokud používáte typy, které `public` se skutečně staly a byly přesunuty do nového podporovaného oboru názvů, aktualizujte odkazy tak, aby odpovídaly novým oborům názvů.</span><span class="sxs-lookup"><span data-stu-id="41867-117">If you're using types that have become truly `public` and have been moved into a new, supported namespace, update your references to match the new namespaces.</span></span>

<span data-ttu-id="41867-118">Pokud používáte typy, které byly `internal`označeny jako , budete muset najít alternativu.</span><span class="sxs-lookup"><span data-stu-id="41867-118">If you're using types that have become marked as `internal`, you'll need to find an alternative.</span></span> <span data-ttu-id="41867-119">Dříve "pubternal" typy nebyly nikdy podporovány pro veřejné použití.</span><span class="sxs-lookup"><span data-stu-id="41867-119">The previously "pubternal" types were never supported for public use.</span></span> <span data-ttu-id="41867-120">Pokud existují určité typy v těchto oborech názvů, které jsou důležité pro vaše aplikace, soubor problém [na dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span><span class="sxs-lookup"><span data-stu-id="41867-120">If there are specific types in these namespaces that are critical to your apps, file an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span> <span data-ttu-id="41867-121">Lze vzít v úvahu vytvoření `public`požadovaných typů .</span><span class="sxs-lookup"><span data-stu-id="41867-121">Considerations may be made for making the requested types `public`.</span></span>

#### <a name="category"></a><span data-ttu-id="41867-122">Kategorie</span><span class="sxs-lookup"><span data-stu-id="41867-122">Category</span></span>

<span data-ttu-id="41867-123">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="41867-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="41867-124">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="41867-124">Affected APIs</span></span>

<span data-ttu-id="41867-125">Tato změna zahrnuje typy v následujících oborech názvů:</span><span class="sxs-lookup"><span data-stu-id="41867-125">This change includes types in the following namespaces:</span></span>

- `Microsoft.AspNetCore.Mvc.Cors.Internal`
- `Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `Microsoft.AspNetCore.Mvc.Internal`
- `Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `Microsoft.AspNetCore.Mvc.Razor.Internal`
- `Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Mvc.Cors.Internal`
- `N:Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `N:Microsoft.AspNetCore.Mvc.Internal`
- `N:Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `N:Microsoft.AspNetCore.Mvc.Razor.Internal`
- `N:Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `N:Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `N:Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

-->
