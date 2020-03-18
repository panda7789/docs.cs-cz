---
ms.openlocfilehash: 15ba678431b97e7c961c119d83546569bdf9bad2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74282532"
---
### <a name="http-some-cookie-samesite-defaults-changed-to-none"></a><span data-ttu-id="894fb-101">HTTP: Některé výchozí hodnoty cookie SameSite se změnily na Žádné</span><span class="sxs-lookup"><span data-stu-id="894fb-101">HTTP: Some cookie SameSite defaults changed to None</span></span>

<span data-ttu-id="894fb-102">`SameSite`je možnost pro soubory cookie, které mohou pomoci zmírnit některé útoky na vyžádání mezi stránkami (CSRF).</span><span class="sxs-lookup"><span data-stu-id="894fb-102">`SameSite` is an option for cookies that can help mitigate some Cross-Site Request Forgery (CSRF) attacks.</span></span> <span data-ttu-id="894fb-103">Když byla tato možnost původně zavedena, byly použity nekonzistentní výchozí hodnoty v různých ASP.NET základní chod y API.</span><span class="sxs-lookup"><span data-stu-id="894fb-103">When this option was initially introduced, inconsistent defaults were used across various ASP.NET Core APIs.</span></span> <span data-ttu-id="894fb-104">Nekonzistence vedla k matoucím výsledkům.</span><span class="sxs-lookup"><span data-stu-id="894fb-104">The inconsistency has led to confusing results.</span></span> <span data-ttu-id="894fb-105">Od ASP.NET jádra 3.0 jsou tyto výchozí hodnoty lépe zarovnány.</span><span class="sxs-lookup"><span data-stu-id="894fb-105">As of ASP.NET Core 3.0, these defaults are better aligned.</span></span> <span data-ttu-id="894fb-106">K této funkci se musíte přihlásit pro jednotlivé komponenty.</span><span class="sxs-lookup"><span data-stu-id="894fb-106">You must opt in to this feature on a per-component basis.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="894fb-107">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="894fb-107">Version introduced</span></span>

<span data-ttu-id="894fb-108">3.0</span><span class="sxs-lookup"><span data-stu-id="894fb-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="894fb-109">Staré chování</span><span class="sxs-lookup"><span data-stu-id="894fb-109">Old behavior</span></span>

<span data-ttu-id="894fb-110">Podobná ASP.NET jádrová api <xref:Microsoft.AspNetCore.Http.SameSiteMode> používají různé výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="894fb-110">Similar ASP.NET Core APIs used different default <xref:Microsoft.AspNetCore.Http.SameSiteMode> values.</span></span> <span data-ttu-id="894fb-111">Příklad nekonzistence je zobrazen `HttpResponse.Cookies.Append(String, String)` `HttpResponse.Cookies.Append(String, String, CookieOptions)`v a , `SameSiteMode.None` `SameSiteMode.Lax`které defaulted a , v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="894fb-111">An example of the inconsistency is seen in `HttpResponse.Cookies.Append(String, String)` and `HttpResponse.Cookies.Append(String, String, CookieOptions)`, which defaulted to `SameSiteMode.None` and `SameSiteMode.Lax`, respectively.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="894fb-112">Nové chování</span><span class="sxs-lookup"><span data-stu-id="894fb-112">New behavior</span></span>

<span data-ttu-id="894fb-113">Všechna ovlivněná nastavení `SameSiteMode.None`API jsou ve výchozím nastavení nastavena na hodnotu .</span><span class="sxs-lookup"><span data-stu-id="894fb-113">All the affected APIs default to `SameSiteMode.None`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="894fb-114">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="894fb-114">Reason for change</span></span>

<span data-ttu-id="894fb-115">Výchozí hodnota byla změněna tak, aby byla nastavena `SameSite` funkce pro přihlášení.</span><span class="sxs-lookup"><span data-stu-id="894fb-115">The default value was changed to make `SameSite` an opt-in feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="894fb-116">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="894fb-116">Recommended action</span></span>

<span data-ttu-id="894fb-117">Každá komponenta, která vydává `SameSite` soubory cookie, se musí rozhodnout, zda je pro její scénáře vhodná.</span><span class="sxs-lookup"><span data-stu-id="894fb-117">Each component that emits cookies needs to decide if `SameSite` is appropriate for its scenarios.</span></span> <span data-ttu-id="894fb-118">Zkontrolujte využití postižených rozhraní API `SameSite` a podle potřeby je překonfigurujte.</span><span class="sxs-lookup"><span data-stu-id="894fb-118">Review your usage of the affected APIs and reconfigure `SameSite` as needed.</span></span>

#### <a name="category"></a><span data-ttu-id="894fb-119">Kategorie</span><span class="sxs-lookup"><span data-stu-id="894fb-119">Category</span></span>

<span data-ttu-id="894fb-120">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="894fb-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="894fb-121">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="894fb-121">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)`
- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`

-->
