---
ms.openlocfilehash: 0c88d40e34d2d6458bb463a09d716dea42b711fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901740"
---
### <a name="authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters"></a>Autorizace: IAllowAnonymous odebrán z AuthorizationFilterContext.Filters

Od ASP.NET Core 3.0, MVC nepřidá [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) pro [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) atributy, které byly zjištěny na řadiče a metody akce. Tato změna je určena místně pro <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>deriváty , ale je <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> to zásadní změna pro a implementace. Tyto implementace zabalené v atributu [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) jsou [oblíbeným](https://stackoverflow.com/a/41348219/608220) a podporovaným způsobem, jak dosáhnout silného typu autorizace založené na atributech, pokud jsou požadovány vkládání konfigurace a závislostí.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

<xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous>se objevil v [AuthorizationFilterContext.Filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) kolekce. Testování přítomnosti rozhraní byl platný přístup k přepsání nebo zakázání filtru na jednotlivé metody kontroleru.

#### <a name="new-behavior"></a>Nové chování

`IAllowAnonymous`již se v `AuthorizationFilterContext.Filters` kolekci nezobrazí. `IAsyncAuthorizationFilter`implementace, které jsou závislé na staré chování obvykle způsobit přerušované HTTP 401 Neoprávněné nebo HTTP 403 Zakázané odpovědi.

#### <a name="reason-for-change"></a>Důvod změny

V ASP.NET core 3.0 byla zavedena nová strategie směrování koncových bodů.

#### <a name="recommended-action"></a>Doporučená akce

Vyhledejte metadata koncového bodu pro `IAllowAnonymous`. Například:

```csharp
var endpoint = context.HttpContext.GetEndpoint();
if (endpoint?.Metadata?.GetMetadata<IAllowAnonymous>() != null)
{
}
```

Příklad této techniky je vidět v [této HasAllowAnonymous metoda](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádný

<!--

#### Affected APIs

Not detectable via API analysis

-->
