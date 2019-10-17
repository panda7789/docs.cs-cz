---
ms.openlocfilehash: ad451329d7b9ec15bc8b3c49159346d79944d692
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394163"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a>Ověřování: nahrazené typy Newtonsoft. JSON

V ASP.NET Core 3,0 byly nahrazeny typy `Newtonsoft.Json` používané v rozhraních API pro ověřování pomocí typů `System.Text.Json`. S výjimkou následujících případů zůstane základní použití ověřovacích balíčků neovlivněné:

* Třídy odvozené od zprostředkovatelů OAuth, jako jsou například z [ASPNET-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).
* Pokročilé implementace manipulace s deklaracemi identity

Další informace najdete v tématu [ASPNET/AspNetCore # 7105](https://github.com/aspnet/AspNetCore/pull/7105). Diskuzi najdete v tématu [ASPNET/AspNetCore # 7289](https://github.com/aspnet/AspNetCore/issues/7289).

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

U odvozených implementací OAuth je nejběžnější změna nahrazena `JObject.Parse` s `JsonDocument.Parse` v přepsání `CreateTicketAsync`, jak je znázorněno [zde](https://github.com/aspnet/AspNetCore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40). `JsonDocument` implementuje `IDisposable`.

Následující seznam popisuje známé změny:

- <xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> se zobrazí `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`. Podobně jsou ovlivněny všechny odvozené implementace `ClaimAction`.
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> se naplní `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> se naplní `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> se odebral jeden starý konstruktor a druhý nahradil `JObject` s `JsonElement`. Vlastnost `User` a metoda `RunClaimActions` byly aktualizovány tak, aby odpovídaly.
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> nyní přijímá parametr typu `JsonDocument` namísto `JObject`. Vlastnost `Response` byla aktualizována tak, aby odpovídala. `OAuthTokenResponse` je nyní jednorázově a bude odstraněn `OAuthHandler`. Odvozené implementace OAuth přepisují `ExchangeCodeAsync` nemusíte nakládat `JsonDocument` nebo `OAuthTokenResponse`.
- <xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> se změnil z `JObject` na `JsonDocument`.
- <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> se změnil z `JObject` na `JsonElement`.
- <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType> se změnil z přijetí `JObject` na `JsonElement`.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.AspNetCore.Authentication.Facebook?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.MicrosoftAccount?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.OAuth?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.OpenIdConnect?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.Twitter?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Authentication.Facebook`
- `N:Microsoft.AspNetCore.Authentication.Google`
- `N:Microsoft.AspNetCore.Authentication.MicrosoftAccount`
- `N:Microsoft.AspNetCore.Authentication.OAuth`
- `N:Microsoft.AspNetCore.Authentication.OpenIdConnect`
- `N:Microsoft.AspNetCore.Authentication.Twitter`

-->
