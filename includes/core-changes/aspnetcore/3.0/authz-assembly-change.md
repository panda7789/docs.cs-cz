---
ms.openlocfilehash: b91cdc7a0d2e4258662155a840500ce21ab35760
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74100819"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a>Autorizace: přetížení AddAuthorization se přesunulo do jiného sestavení.

Základní metody `AddAuthorization`, které se nacházejí v `Microsoft.AspNetCore.Authorization`, byly přejmenovány na `AddAuthorizationCore`. Staré metody `AddAuthorization` stále existují, ale jsou místo toho v sestavení `Microsoft.AspNetCore.Authorization.Policy`. U aplikací, které používají obě metody, by se měl zobrazit žádný vliv. Všimněte si, že `Microsoft.AspNetCore.Authorization.Policy` nyní dodává do sdíleného rozhraní, nikoli jako samostatný balíček, jak je popsáno v tématu [Shared Framework: sestavení byla odebrána z Microsoft. AspNetCore. app](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).

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
