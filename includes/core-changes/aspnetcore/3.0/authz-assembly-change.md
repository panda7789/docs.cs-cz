---
ms.openlocfilehash: b91cdc7a0d2e4258662155a840500ce21ab35760
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74100819"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a>Autorizace: AddAuthorization přetížení přesunuta do jiného sestavení

Základní `AddAuthorization` metody, které se `Microsoft.AspNetCore.Authorization` používaly k `AddAuthorizationCore`pobývání v byly přejmenovány na . Staré `AddAuthorization` metody stále existují, ale `Microsoft.AspNetCore.Authorization.Policy` jsou v sestavení místo. Aplikace používající obě metody by neměly mít žádný vliv. Všimněte `Microsoft.AspNetCore.Authorization.Policy` si, že nyní dodává ve sdíleném rámci spíše než samostatný balíček, jak je popsáno ve [sdílené masce: Sestavení odebrána z Microsoft.AspNetCore.App](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování
`AddAuthorization`metody existovaly `Microsoft.AspNetCore.Authorization`v .

#### <a name="new-behavior"></a>Nové chování

`AddAuthorization`existují metody `Microsoft.AspNetCore.Authorization.Policy`v . `AddAuthorizationCore`je nový název pro staré metody.

#### <a name="reason-for-change"></a>Důvod změny

`AddAuthorization`je lepší název metody pro přidání všech běžných služeb potřebných pro autorizaci.

#### <a name="recommended-action"></a>Doporučená akce

Buď přidejte `Microsoft.AspNetCore.Authorization.Policy` odkaz `AddAuthorizationCore` na nebo použijte místo.

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
