---
ms.openlocfilehash: 60ebcd9fc9ca18c33d31b82ba5020426d22a7d5a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901966"
---
### <a name="authentication-httpcontextauthentication-property-removed"></a>Ověřování: Vlastnost HttpContext.Authentication byla odebrána.

Zastaralá `Authentication` vlastnost byla `HttpContext` odebrána.

#### <a name="change-description"></a>Popis změny

Jako součást [dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504)byla odebrána `Authentication` zastaralá vlastnost. `HttpContext` Ubytovací `Authentication` zařízení je od roku 2.0 zastaralé. [Průvodce migrací](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions) byl publikován pro migraci kódu pomocí této zastaralé vlastnosti do nových náhradních api. Zbývající nepoužívané třídy / API související se starým ASP.NET zásobníku [dotnet/aspnetcore@d7a7c65](https://github.com/dotnet/aspnetcore/commit/d7a7c65)ověřování Jádra 1.x byly odebrány v potvrzení .

Diskuse naleznete [v tématu dotnet/aspnetcore#6533](https://github.com/dotnet/aspnetcore/issues/6533).

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="reason-for-change"></a>Důvod změny

ASP.NET core 1.0 API byly nahrazeny <xref:Microsoft.AspNetCore.Authentication.AuthenticationHttpContextExtensions?displayProperty=fullName>rozšiřujícími metodami v .

#### <a name="recommended-action"></a>Doporučená akce

Podívejte se na [průvodce migrací](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions).

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.AspNetCore.Http.Authentication.AuthenticateInfo?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Authentication.AuthenticationManager?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Authentication.AuthenticationProperties?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.AuthenticateContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.ChallengeBehavior?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.ChallengeContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.DescribeSchemesContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.IAuthenticationHandler?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.IHttpAuthenticationFeature.Handler?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.SignInContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.SignOutContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.HttpContext.Authentication?displayProperty=fullName>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Authentication.AuthenticateInfo`
- `T:Microsoft.AspNetCore.Http.Authentication.AuthenticationManager`
- `T:Microsoft.AspNetCore.Http.Authentication.AuthenticationProperties`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.AuthenticateContext`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.ChallengeBehavior`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.ChallengeContext`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.DescribeSchemesContext`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.IAuthenticationHandler`
- `P:Microsoft.AspNetCore.Http.Features.Authentication.IHttpAuthenticationFeature.Handler`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.SignInContext`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.SignOutContext`
- `P:Microsoft.AspNetCore.Http.HttpContext.Authentication`

-->
