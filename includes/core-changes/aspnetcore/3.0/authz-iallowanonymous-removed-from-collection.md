---
ms.openlocfilehash: 0c88d40e34d2d6458bb463a09d716dea42b711fe
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901740"
---
### <a name="authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters"></a>Autorizace: IAllowAnonymous se odebral z AuthorizationFilterContext. filters.

Od ASP.NET Core 3,0 MVC nepřidává [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) pro atributy [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) , které byly zjištěny na řadičích a metodách akcí. Tato změna se řeší místně pro deriváty <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>, ale u implementací <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> a <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> se jedná o zásadní změnu. Takové implementace zabalené v atributu [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) jsou [oblíbeným](https://stackoverflow.com/a/41348219/608220) a podporovaným způsobem, jak dosáhnout silného typu ověřování založeného na atributech, pokud jsou vyžadovány konfigurace i vkládání závislostí.

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="old-behavior"></a>Staré chování

<xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous> se objevila v kolekci [AuthorizationFilterContext. filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) . Testování přítomnosti rozhraní bylo platným přístupem k přepsání nebo zakázání filtru u jednotlivých metod kontroleru.

#### <a name="new-behavior"></a>Nové chování

`IAllowAnonymous` se již nezobrazuje v kolekci `AuthorizationFilterContext.Filters`. `IAsyncAuthorizationFilter` implementace, které jsou závislé na starém chování, obvykle způsobují přerušované odpovědi HTTP 401 Neautorizováno nebo HTTP 403 zakázané.

#### <a name="reason-for-change"></a>Důvod změny

V ASP.NET Core 3,0 byla představena nová strategie směrování koncových bodů.

#### <a name="recommended-action"></a>Doporučená akce

Vyhledejte metadata koncového bodu pro `IAllowAnonymous`. Příklad:

```csharp
var endpoint = context.HttpContext.GetEndpoint();
if (endpoint?.Metadata?.GetMetadata<IAllowAnonymous>() != null)
{
}
```

V [této metodě HasAllowAnonymous](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236)se zobrazuje příklad této techniky.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné

<!--

#### Affected APIs

Not detectable via API analysis

-->
