---
ms.openlocfilehash: 65bac44c84589fb55d2b04c39088c2825c451a6b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394065"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a>Autorizace: přetížení AddAuthorization se přesunulo do jiného sestavení.

Základní metody `AddAuthorization`, které se nacházejí v `Microsoft.AspNetCore.Authorization`, byly přejmenovány na `AddAuthorizationCore`. Staré metody `AddAuthorization` stále existují, ale místo toho jsou v balíčku `Microsoft.AspNetCore.Authorization.Policy`. U aplikací, které používají obě metody, by se měl zobrazit žádný vliv. Aplikace, které balíček zásad nepoužívaly, se musí přepnout na použití `AddAuthorizationCore`.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="old-behavior"></a>Staré chování

v `Microsoft.AspNetCore.Authorization` existovaly metody `AddAuthorization`.

#### <a name="new-behavior"></a>Nové chování

v `Microsoft.AspNetCore.Authorization.Policy` existují metody `AddAuthorization`. `AddAuthorizationCore` je nový název pro staré metody.

#### <a name="reason-for-change"></a>Důvod změny

`AddAuthorization` je lepší název metody pro přidání všech běžných služeb potřebných pro autorizaci.

#### <a name="recommended-action"></a>Doporučená akce

Buď přidejte odkaz na `Microsoft.AspNetCore.Authorization.Policy`, nebo použijte místo toho `AddAuthorizationCore`.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
