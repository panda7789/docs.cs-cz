---
ms.openlocfilehash: b4499637cd5fff015335e0cdb3c6cf1c3ea6cff0
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81637181"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a>Ověřování: Newtonsoft.Json typy nahrazeny

V ASP.NET Core 3.0 byly `Newtonsoft.Json` typy používané v `System.Text.Json` ověřování API nahrazeny typy. S výjimkou následujících případů zůstává základní použití balíčků ověřování nedotčeno:

* Třídy odvozené od poskytovatelů OAuth, například z [aspnet-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).
* Pokročilé implementace manipulace s deklaracemi.

Další informace naleznete [v tématu dotnet/aspnetcore#7105](https://github.com/dotnet/aspnetcore/pull/7105). Diskuse naleznete [v tématu dotnet/aspnetcore#7289](https://github.com/dotnet/aspnetcore/issues/7289).

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Pro odvozené implementace OAuth nejběžnější změnou `JObject.Parse` je `JsonDocument.Parse` nahrazení `CreateTicketAsync` v přepsání, jak je znázorněno [zde](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40). `JsonDocument`implementuje `IDisposable`.

Následující seznam popisuje známé změny:

- <xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType>se `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`stává . Všechny odvozené implementace `ClaimAction` jsou podobně ovlivněny.
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType>se stává`MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType>se stává`MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext>má jeden starý konstruktor odstraněn a `JObject` `JsonElement`druhý nahrazen . Vlastnost `User` a `RunClaimActions` metoda byly aktualizovány tak, aby odpovídaly.
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)>nyní přijímá parametr typu `JsonDocument` namísto `JObject`. Vlastnost `Response` byla aktualizována tak, aby odpovídala. `OAuthTokenResponse`je nyní na jedno použití `OAuthHandler`a bude zlikvidován . Odvozené oauth implementace `ExchangeCodeAsync` přepsání není nutné `JsonDocument` `OAuthTokenResponse`vyřadit nebo .
- <xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType>změněna `JObject` `JsonDocument`z na .
- <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType>změněna `JObject` `JsonElement`z na .
- Poslední parametr [TwitterHandler.CreateTicketAsync(ClaimsIdentity,AuthenticationProperties,AccessToken,JObject)](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.authentication.twitter.twitterhandler.createticketasync?view=aspnetcore-2.2#Microsoft_AspNetCore_Authentication_Twitter_TwitterHandler_CreateTicketAsync_System_Security_Claims_ClaimsIdentity_Microsoft_AspNetCore_Authentication_AuthenticationProperties_Microsoft_AspNetCore_Authentication_Twitter_AccessToken_Newtonsoft_Json_Linq_JObject_) byl `JObject` `JsonElement`změněn z na . Metoda nahrazení <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,System.Text.Json.JsonElement)?displayProperty=nameWithType>je .

#### <a name="category"></a>Kategorie

Jádro ASP.NET

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
