---
ms.openlocfilehash: 09fd95ba5f3aee59f2abdfbb4e64eb6202e2b873
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394184"
---
### <a name="mvc-pubternal-types-changed-to-internal"></a><span data-ttu-id="9084b-101">MVC: typy "Pubternal" se změnily na interní</span><span class="sxs-lookup"><span data-stu-id="9084b-101">MVC: "Pubternal" types changed to internal</span></span>

<span data-ttu-id="9084b-102">V ASP.NET Core 3,0 se všechny typy "pubternal" v MVC aktualizovaly buď jako `public` v podporovaném oboru názvů, nebo v případě potřeby `internal`.</span><span class="sxs-lookup"><span data-stu-id="9084b-102">In ASP.NET Core 3.0, all "pubternal" types in MVC were updated to either be `public` in a supported namespace or `internal` as appropriate.</span></span>

#### <a name="change-description"></a><span data-ttu-id="9084b-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="9084b-103">Change description</span></span>

<span data-ttu-id="9084b-104">V ASP.NET Core jsou typy "pubternal" deklarovány jako `public`, ale nacházejí se v oboru názvů `.Internal`s příponou.</span><span class="sxs-lookup"><span data-stu-id="9084b-104">In ASP.NET Core, "pubternal" types are declared as `public` but reside in a `.Internal`-suffixed namespace.</span></span> <span data-ttu-id="9084b-105">I když jsou tyto typy `public`, nemají žádné zásady podpory a podléhají změnám.</span><span class="sxs-lookup"><span data-stu-id="9084b-105">While these types are `public`, they have no support policy and are subject to breaking changes.</span></span> <span data-ttu-id="9084b-106">Omlouváme se, ale náhodné použití těchto typů je běžné, což vedlo k zásadním změnám těchto projektů a omezení schopnosti zachovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9084b-106">Unfortunately, accidental use of these types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9084b-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="9084b-107">Version introduced</span></span>

<span data-ttu-id="9084b-108">3,0</span><span class="sxs-lookup"><span data-stu-id="9084b-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="9084b-109">Staré chování</span><span class="sxs-lookup"><span data-stu-id="9084b-109">Old behavior</span></span>

<span data-ttu-id="9084b-110">Některé typy v MVC byly `public`, ale v oboru názvů `.Internal`.</span><span class="sxs-lookup"><span data-stu-id="9084b-110">Some types in MVC were `public` but in a `.Internal` namespace.</span></span> <span data-ttu-id="9084b-111">Tyto typy neobsahovaly žádné zásady podpory a měly by podléhat nezměněným změnám.</span><span class="sxs-lookup"><span data-stu-id="9084b-111">These types had no support policy and were subject to breaking changes.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="9084b-112">Nové chování</span><span class="sxs-lookup"><span data-stu-id="9084b-112">New behavior</span></span>

<span data-ttu-id="9084b-113">Všechny tyto typy jsou aktualizovány tak, aby byly `public` v podporovaném oboru názvů nebo označené jako `internal`.</span><span class="sxs-lookup"><span data-stu-id="9084b-113">All such types are updated either to be `public` in a supported namespace or marked as `internal`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="9084b-114">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="9084b-114">Reason for change</span></span>

<span data-ttu-id="9084b-115">Náhodné použití typů "pubternal" bylo běžné, což vede k zásadním změnám těchto projektů a omezení schopnosti zachovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9084b-115">Accidental use of the "pubternal" types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9084b-116">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="9084b-116">Recommended action</span></span>

<span data-ttu-id="9084b-117">Pokud používáte typy, které se stanou skutečně `public` a byly přesunuty do nového podporovaného oboru názvů, aktualizujte odkazy tak, aby odpovídaly novým oborům názvů.</span><span class="sxs-lookup"><span data-stu-id="9084b-117">If you're using types that have become truly `public` and have been moved into a new, supported namespace, update your references to match the new namespaces.</span></span>

<span data-ttu-id="9084b-118">Pokud používáte typy, které se stanou označenými jako `internal`, budete muset najít alternativu.</span><span class="sxs-lookup"><span data-stu-id="9084b-118">If you're using types that have become marked as `internal`, you'll need to find an alternative.</span></span> <span data-ttu-id="9084b-119">Předchozí typy "pubternal" nebyly nikdy podporovány pro veřejné použití.</span><span class="sxs-lookup"><span data-stu-id="9084b-119">The previously "pubternal" types were never supported for public use.</span></span> <span data-ttu-id="9084b-120">Pokud existují konkrétní typy v těchto oborech názvů, které jsou pro vaše aplikace klíčové, zajistěte problém v [ASPNET/AspNetCore](https://github.com/aspnet/AspNetCore/issues).</span><span class="sxs-lookup"><span data-stu-id="9084b-120">If there are specific types in these namespaces that are critical to your apps, file an issue at [aspnet/AspNetCore](https://github.com/aspnet/AspNetCore/issues).</span></span> <span data-ttu-id="9084b-121">Mohou být provedeny důvody pro vytvoření požadovaných typů `public`.</span><span class="sxs-lookup"><span data-stu-id="9084b-121">Considerations may be made for making the requested types `public`.</span></span>

#### <a name="category"></a><span data-ttu-id="9084b-122">Kategorie</span><span class="sxs-lookup"><span data-stu-id="9084b-122">Category</span></span>

<span data-ttu-id="9084b-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9084b-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9084b-124">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="9084b-124">Affected APIs</span></span>

<span data-ttu-id="9084b-125">Tato změna zahrnuje typy v následujících oborech názvů:</span><span class="sxs-lookup"><span data-stu-id="9084b-125">This change includes types in the following namespaces:</span></span>

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
