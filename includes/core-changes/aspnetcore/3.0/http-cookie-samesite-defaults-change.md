---
ms.openlocfilehash: 15ba678431b97e7c961c119d83546569bdf9bad2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74282532"
---
### <a name="http-some-cookie-samesite-defaults-changed-to-none"></a><span data-ttu-id="f984b-101">HTTP: některé výchozí hodnoty souborů cookie SameSite se změnily na žádné.</span><span class="sxs-lookup"><span data-stu-id="f984b-101">HTTP: Some cookie SameSite defaults changed to None</span></span>

<span data-ttu-id="f984b-102">`SameSite` je možnost souborů cookie, které mohou napomoci zmírnit útokům prostřednictvím CSRF (více lokalit).</span><span class="sxs-lookup"><span data-stu-id="f984b-102">`SameSite` is an option for cookies that can help mitigate some Cross-Site Request Forgery (CSRF) attacks.</span></span> <span data-ttu-id="f984b-103">Při počátečním zavedení této možnosti se v různých ASP.NET Core rozhraní API používaly nekonzistentní výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f984b-103">When this option was initially introduced, inconsistent defaults were used across various ASP.NET Core APIs.</span></span> <span data-ttu-id="f984b-104">Nekonzistence vedla k matoucímu výsledku.</span><span class="sxs-lookup"><span data-stu-id="f984b-104">The inconsistency has led to confusing results.</span></span> <span data-ttu-id="f984b-105">Od ASP.NET Core 3,0 jsou tyto výchozí hodnoty lépe zarovnané.</span><span class="sxs-lookup"><span data-stu-id="f984b-105">As of ASP.NET Core 3.0, these defaults are better aligned.</span></span> <span data-ttu-id="f984b-106">K této funkci se musíte vyjádřit na základě jednotlivých komponent.</span><span class="sxs-lookup"><span data-stu-id="f984b-106">You must opt in to this feature on a per-component basis.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f984b-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="f984b-107">Version introduced</span></span>

<span data-ttu-id="f984b-108">3,0</span><span class="sxs-lookup"><span data-stu-id="f984b-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f984b-109">Staré chování</span><span class="sxs-lookup"><span data-stu-id="f984b-109">Old behavior</span></span>

<span data-ttu-id="f984b-110">Podobná ASP.NET Core rozhraní API používala jiné výchozí hodnoty <xref:Microsoft.AspNetCore.Http.SameSiteMode>.</span><span class="sxs-lookup"><span data-stu-id="f984b-110">Similar ASP.NET Core APIs used different default <xref:Microsoft.AspNetCore.Http.SameSiteMode> values.</span></span> <span data-ttu-id="f984b-111">Příklad nekonzistence se zobrazuje v `HttpResponse.Cookies.Append(String, String)` a `HttpResponse.Cookies.Append(String, String, CookieOptions)`, která je nastavená na `SameSiteMode.None` a `SameSiteMode.Lax`, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="f984b-111">An example of the inconsistency is seen in `HttpResponse.Cookies.Append(String, String)` and `HttpResponse.Cookies.Append(String, String, CookieOptions)`, which defaulted to `SameSiteMode.None` and `SameSiteMode.Lax`, respectively.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f984b-112">Nové chování</span><span class="sxs-lookup"><span data-stu-id="f984b-112">New behavior</span></span>

<span data-ttu-id="f984b-113">Všechna ovlivněná rozhraní API jsou ve výchozím nastavení `SameSiteMode.None`.</span><span class="sxs-lookup"><span data-stu-id="f984b-113">All the affected APIs default to `SameSiteMode.None`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f984b-114">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="f984b-114">Reason for change</span></span>

<span data-ttu-id="f984b-115">Výchozí hodnota byla změněna, aby byla `SameSite` funkce výslovného souhlasu.</span><span class="sxs-lookup"><span data-stu-id="f984b-115">The default value was changed to make `SameSite` an opt-in feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f984b-116">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="f984b-116">Recommended action</span></span>

<span data-ttu-id="f984b-117">Každá komponenta, která generuje soubory cookie, musí rozhodnout, zda je `SameSite` vhodná pro své scénáře.</span><span class="sxs-lookup"><span data-stu-id="f984b-117">Each component that emits cookies needs to decide if `SameSite` is appropriate for its scenarios.</span></span> <span data-ttu-id="f984b-118">Zkontrolujte využití ovlivněných rozhraní API a podle potřeby `SameSite` znovu nakonfigurujte.</span><span class="sxs-lookup"><span data-stu-id="f984b-118">Review your usage of the affected APIs and reconfigure `SameSite` as needed.</span></span>

#### <a name="category"></a><span data-ttu-id="f984b-119">Kategorie</span><span class="sxs-lookup"><span data-stu-id="f984b-119">Category</span></span>

<span data-ttu-id="f984b-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f984b-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f984b-121">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="f984b-121">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)`
- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`

-->
