---
ms.openlocfilehash: a4e20e0468d861138ad801c9dbfa15340b3f388c
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393906"
---
### <a name="authentication-oauthhandler-exchangecodeasync-signature-changed"></a>Ověřování: změnil se podpis OAuthHandler ExchangeCodeAsync.

V ASP.NET Core 3,0 se signatura `OAuthHandler.ExchangeCodeAsync` změnila z:

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(string code, string redirectUri) { throw null; }
```

Do:

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(Microsoft.AspNetCore.Authentication.OAuth.OAuthCodeExchangeContext context) { throw null; }
```

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Řetězce `code` a `redirectUri` byly předány jako samostatné argumenty.

#### <a name="new-behavior"></a>Nové chování

`Code` a `RedirectUri` jsou vlastnosti `OAuthCodeExchangeContext`, které lze nastavit prostřednictvím konstruktoru `OAuthCodeExchangeContext`. Nový typ `OAuthCodeExchangeContext` je jediným argumentem předaným do `OAuthHandler.ExchangeCodeAsync`.

#### <a name="reason-for-change"></a>Důvod změny

Tato změna umožňuje, aby byly další parametry poskytovány nediskriminujícím způsobem. Není nutné vytvářet nová přetížení `ExchangeCodeAsync`.

#### <a name="recommended-action"></a>Doporučená akce

Sestavte `OAuthCodeExchangeContext` s příslušnými hodnotami `code` a `redirectUri`. Je třeba zadat instanci <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties>. Tuto jednu instanci `OAuthCodeExchangeContext` lze předat `OAuthHandler.ExchangeCodeAsync` místo více argumentů.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler%601.ExchangeCodeAsync(System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler`1.ExchangeCodeAsync(System.String,System.String)`

-->
