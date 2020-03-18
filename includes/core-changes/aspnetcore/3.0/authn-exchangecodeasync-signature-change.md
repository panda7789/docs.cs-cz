---
ms.openlocfilehash: a4e20e0468d861138ad801c9dbfa15340b3f388c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393906"
---
### <a name="authentication-oauthhandler-exchangecodeasync-signature-changed"></a>Ověřování: Podpis OAuthHandler ExchangeCodeAsync byl změněn.

V ASP.NET jádrem 3.0 `OAuthHandler.ExchangeCodeAsync` byl podpis změněn z:

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(string code, string redirectUri) { throw null; }
```

Do:

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(Microsoft.AspNetCore.Authentication.OAuth.OAuthCodeExchangeContext context) { throw null; }
```

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

Řetězce `code` `redirectUri` a byly předány jako samostatné argumenty.

#### <a name="new-behavior"></a>Nové chování

`Code`a `RedirectUri` jsou `OAuthCodeExchangeContext` vlastnosti, které `OAuthCodeExchangeContext` lze nastavit prostřednictvím konstruktoru. Nový `OAuthCodeExchangeContext` typ je jediným argumentem předanou společnosti `OAuthHandler.ExchangeCodeAsync`.

#### <a name="reason-for-change"></a>Důvod změny

Tato změna umožňuje další parametry, které mají být poskytnuty v nenarušující způsobem. Není třeba vytvářet nové `ExchangeCodeAsync` přetížení.

#### <a name="recommended-action"></a>Doporučená akce

Vytvořte `OAuthCodeExchangeContext` s `code` příslušnými `redirectUri` a hodnotami. Musí <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> být poskytnuta instance. Tato `OAuthCodeExchangeContext` jedna instance může `OAuthHandler.ExchangeCodeAsync` být předána namísto více argumentů.

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

<xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler%601.ExchangeCodeAsync(System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler`1.ExchangeCodeAsync(System.String,System.String)`

-->
