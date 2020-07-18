---
ms.openlocfilehash: 2b88ab7cfdd7a0a0a770b305ecd0200afd9a9b4b
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441544"
---
### <a name="authorization-resource-in-endpoint-routing-is-httpcontext"></a>Autorizace: prostředek ve směrování koncového bodu je HttpContext

Při použití směrování koncových bodů v ASP.NET Core 3,1 prostředek, který se používá pro autorizaci, je koncovým bodem. Tento přístup nebyl dostatečný pro získání přístupu k datům trasy ( <xref:Microsoft.AspNetCore.Routing.RouteData> ). Dříve v MVC <xref:Microsoft.AspNetCore.Http.HttpContext> byl předán prostředek, který umožňuje přístup ke koncovému bodu ( <xref:Microsoft.AspNetCore.Http.Endpoint> ) i k datům směrování. Tato změna zajistí, že prostředek předaný autorizaci je vždy `HttpContext` .

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 7

#### <a name="old-behavior"></a>Staré chování

Při použití směrování koncových bodů a atributů middleware autorizace ( <xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware> ) nebo [[autorizovat]](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) je prostředek předaný do autorizace shodný s koncovým bodem.

#### <a name="new-behavior"></a>Nové chování

Směrování koncového bodu projde `HttpContext` k autorizaci.

#### <a name="reason-for-change"></a>Důvod změny

Ke koncovému bodu se můžete dostat z `HttpContext` . Neexistoval ale žádný způsob, jak z koncového bodu získat data, jako jsou data o trasách. Došlo ke ztrátě funkčnosti od směrování mimo koncový bod.

#### <a name="recommended-action"></a>Doporučená akce

Pokud vaše aplikace používá prostředek koncového bodu, zavolejte na, <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> `HttpContext` aby se pokračovalo v přístupu ke koncovému bodu.

V ASP.NET Core 5,0 Preview 8 a novějších verzích se můžete vrátit k původnímu chování pomocí <xref:System.AppContext.SetSwitch%2A> . Příklad:

```csharp
AppContext.SetSwitch(
    "Microsoft.AspNetCore.Authorization.SuppressUseHttpContextAsAuthorizationResource",
    isEnabled: true);
```

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné

<!--

#### Affected APIs

Not detectable via API analysis

-->
