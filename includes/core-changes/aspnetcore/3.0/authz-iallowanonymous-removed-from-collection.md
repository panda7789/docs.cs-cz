---
ms.openlocfilehash: 0c88d40e34d2d6458bb463a09d716dea42b711fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901740"
---
### <a name="authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters"></a><span data-ttu-id="0d7a1-101">Autorizace: IAllowAnonymous odebrán z AuthorizationFilterContext.Filters</span><span class="sxs-lookup"><span data-stu-id="0d7a1-101">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>

<span data-ttu-id="0d7a1-102">Od ASP.NET Core 3.0, MVC nepřidá [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) pro [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) atributy, které byly zjištěny na řadiče a metody akce.</span><span class="sxs-lookup"><span data-stu-id="0d7a1-102">As of ASP.NET Core 3.0, MVC doesn't add [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) for [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) attributes that were discovered on controllers and action methods.</span></span> <span data-ttu-id="0d7a1-103">Tato změna je určena místně pro <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>deriváty , ale je <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> to zásadní změna pro a implementace.</span><span class="sxs-lookup"><span data-stu-id="0d7a1-103">This change is addressed locally for derivatives of <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>, but it's a breaking change for <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> and <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> implementations.</span></span> <span data-ttu-id="0d7a1-104">Tyto implementace zabalené v atributu [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) jsou [oblíbeným](https://stackoverflow.com/a/41348219/608220) a podporovaným způsobem, jak dosáhnout silného typu autorizace založené na atributech, pokud jsou požadovány vkládání konfigurace a závislostí.</span><span class="sxs-lookup"><span data-stu-id="0d7a1-104">Such implementations wrapped in a [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) attribute are a [popular](https://stackoverflow.com/a/41348219/608220) and supported way to achieve strongly-typed, attribute-based authorization when both configuration and dependency injection are required.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0d7a1-105">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="0d7a1-105">Version introduced</span></span>

<span data-ttu-id="0d7a1-106">3.0</span><span class="sxs-lookup"><span data-stu-id="0d7a1-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0d7a1-107">Staré chování</span><span class="sxs-lookup"><span data-stu-id="0d7a1-107">Old behavior</span></span>

<span data-ttu-id="0d7a1-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous>se objevil v [AuthorizationFilterContext.Filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) kolekce.</span><span class="sxs-lookup"><span data-stu-id="0d7a1-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous> appeared in the [AuthorizationFilterContext.Filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) collection.</span></span> <span data-ttu-id="0d7a1-109">Testování přítomnosti rozhraní byl platný přístup k přepsání nebo zakázání filtru na jednotlivé metody kontroleru.</span><span class="sxs-lookup"><span data-stu-id="0d7a1-109">Testing for the interface's presence was a valid approach to override or disable the filter on individual controller methods.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="0d7a1-110">Nové chování</span><span class="sxs-lookup"><span data-stu-id="0d7a1-110">New behavior</span></span>

<span data-ttu-id="0d7a1-111">`IAllowAnonymous`již se v `AuthorizationFilterContext.Filters` kolekci nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="0d7a1-111">`IAllowAnonymous` no longer appears in the `AuthorizationFilterContext.Filters` collection.</span></span> <span data-ttu-id="0d7a1-112">`IAsyncAuthorizationFilter`implementace, které jsou závislé na staré chování obvykle způsobit přerušované HTTP 401 Neoprávněné nebo HTTP 403 Zakázané odpovědi.</span><span class="sxs-lookup"><span data-stu-id="0d7a1-112">`IAsyncAuthorizationFilter` implementations that are dependent on the old behavior typically cause intermittent HTTP 401 Unauthorized or HTTP 403 Forbidden responses.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0d7a1-113">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="0d7a1-113">Reason for change</span></span>

<span data-ttu-id="0d7a1-114">V ASP.NET core 3.0 byla zavedena nová strategie směrování koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="0d7a1-114">A new endpoint routing strategy was introduced in ASP.NET Core 3.0.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0d7a1-115">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="0d7a1-115">Recommended action</span></span>

<span data-ttu-id="0d7a1-116">Vyhledejte metadata koncového bodu pro `IAllowAnonymous`.</span><span class="sxs-lookup"><span data-stu-id="0d7a1-116">Search the endpoint metadata for `IAllowAnonymous`.</span></span> <span data-ttu-id="0d7a1-117">Například:</span><span class="sxs-lookup"><span data-stu-id="0d7a1-117">For example:</span></span>

```csharp
var endpoint = context.HttpContext.GetEndpoint();
if (endpoint?.Metadata?.GetMetadata<IAllowAnonymous>() != null)
{
}
```

<span data-ttu-id="0d7a1-118">Příklad této techniky je vidět v [této HasAllowAnonymous metoda](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).</span><span class="sxs-lookup"><span data-stu-id="0d7a1-118">An example of this technique is seen in [this HasAllowAnonymous method](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).</span></span>

#### <a name="category"></a><span data-ttu-id="0d7a1-119">Kategorie</span><span class="sxs-lookup"><span data-stu-id="0d7a1-119">Category</span></span>

<span data-ttu-id="0d7a1-120">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0d7a1-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0d7a1-121">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="0d7a1-121">Affected APIs</span></span>

<span data-ttu-id="0d7a1-122">Žádný</span><span class="sxs-lookup"><span data-stu-id="0d7a1-122">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
