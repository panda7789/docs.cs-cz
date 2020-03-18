---
ms.openlocfilehash: 58dbb73902c0226fa81acf1a70de2160f406f6c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901984"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a>Autorizace: Implementace IAuthorizationPolicyProvider vyžadují novou metodu

V ASP.NET Core 3.0 `GetFallbackPolicyAsync` byla do `IAuthorizationPolicyProvider`aplikace přidána nová metoda . Tato záložní zásada je používána middleware autorizace, pokud není zadána žádná zásada.

Další informace naleznete [v tématu dotnet/aspnetcore#9759](https://github.com/dotnet/aspnetcore/pull/9759).

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Implementace `IAuthorizationPolicyProvider` nevyžadovaly metodu. `GetFallbackPolicyAsync`

#### <a name="new-behavior"></a>Nové chování

Implementace vyžadují `IAuthorizationPolicyProvider` metodu. `GetFallbackPolicyAsync`

#### <a name="reason-for-change"></a>Důvod změny

Pro nové `AuthorizationMiddleware` použití nové metody byla zapotřebí nová metoda, pokud není zadána žádná zásada.

#### <a name="recommended-action"></a>Doporučená akce

Přidejte `GetFallbackPolicyAsync` metodu do `IAuthorizationPolicyProvider`implementace aplikace .

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
