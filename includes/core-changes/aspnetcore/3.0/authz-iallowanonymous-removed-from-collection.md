---
ms.openlocfilehash: 0c88d40e34d2d6458bb463a09d716dea42b711fe
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901740"
---
### <a name="authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters"></a><span data-ttu-id="c47fc-101">Autorizace: IAllowAnonymous se odebral z AuthorizationFilterContext. filters.</span><span class="sxs-lookup"><span data-stu-id="c47fc-101">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>

<span data-ttu-id="c47fc-102">Od ASP.NET Core 3,0 MVC nepřidává [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) pro atributy [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) , které byly zjištěny na řadičích a metodách akcí.</span><span class="sxs-lookup"><span data-stu-id="c47fc-102">As of ASP.NET Core 3.0, MVC doesn't add [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) for [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) attributes that were discovered on controllers and action methods.</span></span> <span data-ttu-id="c47fc-103">Tato změna se řeší místně pro deriváty <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>, ale u implementací <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> a <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> se jedná o zásadní změnu.</span><span class="sxs-lookup"><span data-stu-id="c47fc-103">This change is addressed locally for derivatives of <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>, but it's a breaking change for <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> and <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> implementations.</span></span> <span data-ttu-id="c47fc-104">Takové implementace zabalené v atributu [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) jsou [oblíbeným](https://stackoverflow.com/a/41348219/608220) a podporovaným způsobem, jak dosáhnout silného typu ověřování založeného na atributech, pokud jsou vyžadovány konfigurace i vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="c47fc-104">Such implementations wrapped in a [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) attribute are a [popular](https://stackoverflow.com/a/41348219/608220) and supported way to achieve strongly-typed, attribute-based authorization when both configuration and dependency injection are required.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c47fc-105">Představená verze</span><span class="sxs-lookup"><span data-stu-id="c47fc-105">Version introduced</span></span>

<span data-ttu-id="c47fc-106">3,0</span><span class="sxs-lookup"><span data-stu-id="c47fc-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="c47fc-107">Staré chování</span><span class="sxs-lookup"><span data-stu-id="c47fc-107">Old behavior</span></span>

<span data-ttu-id="c47fc-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous> se objevila v kolekci [AuthorizationFilterContext. filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) .</span><span class="sxs-lookup"><span data-stu-id="c47fc-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous> appeared in the [AuthorizationFilterContext.Filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) collection.</span></span> <span data-ttu-id="c47fc-109">Testování přítomnosti rozhraní bylo platným přístupem k přepsání nebo zakázání filtru u jednotlivých metod kontroleru.</span><span class="sxs-lookup"><span data-stu-id="c47fc-109">Testing for the interface's presence was a valid approach to override or disable the filter on individual controller methods.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="c47fc-110">Nové chování</span><span class="sxs-lookup"><span data-stu-id="c47fc-110">New behavior</span></span>

<span data-ttu-id="c47fc-111">`IAllowAnonymous` se již nezobrazuje v kolekci `AuthorizationFilterContext.Filters`.</span><span class="sxs-lookup"><span data-stu-id="c47fc-111">`IAllowAnonymous` no longer appears in the `AuthorizationFilterContext.Filters` collection.</span></span> <span data-ttu-id="c47fc-112">`IAsyncAuthorizationFilter` implementace, které jsou závislé na starém chování, obvykle způsobují přerušované odpovědi HTTP 401 Neautorizováno nebo HTTP 403 zakázané.</span><span class="sxs-lookup"><span data-stu-id="c47fc-112">`IAsyncAuthorizationFilter` implementations that are dependent on the old behavior typically cause intermittent HTTP 401 Unauthorized or HTTP 403 Forbidden responses.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="c47fc-113">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="c47fc-113">Reason for change</span></span>

<span data-ttu-id="c47fc-114">V ASP.NET Core 3,0 byla představena nová strategie směrování koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="c47fc-114">A new endpoint routing strategy was introduced in ASP.NET Core 3.0.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c47fc-115">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="c47fc-115">Recommended action</span></span>

<span data-ttu-id="c47fc-116">Vyhledejte metadata koncového bodu pro `IAllowAnonymous`.</span><span class="sxs-lookup"><span data-stu-id="c47fc-116">Search the endpoint metadata for `IAllowAnonymous`.</span></span> <span data-ttu-id="c47fc-117">Příklad:</span><span class="sxs-lookup"><span data-stu-id="c47fc-117">For example:</span></span>

```csharp
var endpoint = context.HttpContext.GetEndpoint();
if (endpoint?.Metadata?.GetMetadata<IAllowAnonymous>() != null)
{
}
```

<span data-ttu-id="c47fc-118">V [této metodě HasAllowAnonymous](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236)se zobrazuje příklad této techniky.</span><span class="sxs-lookup"><span data-stu-id="c47fc-118">An example of this technique is seen in [this HasAllowAnonymous method](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).</span></span>

#### <a name="category"></a><span data-ttu-id="c47fc-119">Kategorie</span><span class="sxs-lookup"><span data-stu-id="c47fc-119">Category</span></span>

<span data-ttu-id="c47fc-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c47fc-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c47fc-121">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="c47fc-121">Affected APIs</span></span>

<span data-ttu-id="c47fc-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="c47fc-122">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->