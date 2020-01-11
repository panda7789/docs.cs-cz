---
ms.openlocfilehash: 58dbb73902c0226fa81acf1a70de2160f406f6c6
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901984"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a>Autorizace: implementace IAuthorizationPolicyProvider vyžadují novou metodu.

V ASP.NET Core 3,0 byla do `IAuthorizationPolicyProvider`přidána nová metoda `GetFallbackPolicyAsync`. Tuto záložní zásadu používá middleware autorizace, pokud není zadána žádná zásada.

Další informace naleznete v tématu [dotnet/aspnetcore # 9759](https://github.com/dotnet/aspnetcore/pull/9759).

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="old-behavior"></a>Staré chování

Implementace `IAuthorizationPolicyProvider` nevyžadovala `GetFallbackPolicyAsync` metodu.

#### <a name="new-behavior"></a>Nové chování

Implementace `IAuthorizationPolicyProvider` vyžadují metodu `GetFallbackPolicyAsync`.

#### <a name="reason-for-change"></a>Důvod změny

Nová metoda byla nutná k tomu, aby nový `AuthorizationMiddleware` mohl použít, když není zadána žádná zásada.

#### <a name="recommended-action"></a>Doporučená akce

Přidejte metodu `GetFallbackPolicyAsync` do implementací `IAuthorizationPolicyProvider`.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
