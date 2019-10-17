---
ms.openlocfilehash: ad451329d7b9ec15bc8b3c49159346d79944d692
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394163"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a><span data-ttu-id="ae977-101">Ověřování: nahrazené typy Newtonsoft. JSON</span><span class="sxs-lookup"><span data-stu-id="ae977-101">Authentication: Newtonsoft.Json types replaced</span></span>

<span data-ttu-id="ae977-102">V ASP.NET Core 3,0 byly nahrazeny typy `Newtonsoft.Json` používané v rozhraních API pro ověřování pomocí typů `System.Text.Json`.</span><span class="sxs-lookup"><span data-stu-id="ae977-102">In ASP.NET Core 3.0, `Newtonsoft.Json` types used in Authentication APIs have been replaced with `System.Text.Json` types.</span></span> <span data-ttu-id="ae977-103">S výjimkou následujících případů zůstane základní použití ověřovacích balíčků neovlivněné:</span><span class="sxs-lookup"><span data-stu-id="ae977-103">Except for the following cases, basic usage of the Authentication packages remains unaffected:</span></span>

* <span data-ttu-id="ae977-104">Třídy odvozené od zprostředkovatelů OAuth, jako jsou například z [ASPNET-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).</span><span class="sxs-lookup"><span data-stu-id="ae977-104">Classes derived from the OAuth providers, such as those from [aspnet-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).</span></span>
* <span data-ttu-id="ae977-105">Pokročilé implementace manipulace s deklaracemi identity</span><span class="sxs-lookup"><span data-stu-id="ae977-105">Advanced claim manipulation implementations.</span></span>

<span data-ttu-id="ae977-106">Další informace najdete v tématu [ASPNET/AspNetCore # 7105](https://github.com/aspnet/AspNetCore/pull/7105).</span><span class="sxs-lookup"><span data-stu-id="ae977-106">For more information, see [aspnet/AspNetCore#7105](https://github.com/aspnet/AspNetCore/pull/7105).</span></span> <span data-ttu-id="ae977-107">Diskuzi najdete v tématu [ASPNET/AspNetCore # 7289](https://github.com/aspnet/AspNetCore/issues/7289).</span><span class="sxs-lookup"><span data-stu-id="ae977-107">For discussion, see [aspnet/AspNetCore#7289](https://github.com/aspnet/AspNetCore/issues/7289).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ae977-108">Představená verze</span><span class="sxs-lookup"><span data-stu-id="ae977-108">Version introduced</span></span>

<span data-ttu-id="ae977-109">3.0</span><span class="sxs-lookup"><span data-stu-id="ae977-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ae977-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="ae977-110">Recommended action</span></span>

<span data-ttu-id="ae977-111">U odvozených implementací OAuth je nejběžnější změna nahrazena `JObject.Parse` s `JsonDocument.Parse` v přepsání `CreateTicketAsync`, jak je znázorněno [zde](https://github.com/aspnet/AspNetCore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40).</span><span class="sxs-lookup"><span data-stu-id="ae977-111">For derived OAuth implementations, the most common change is to replace `JObject.Parse` with `JsonDocument.Parse` in the `CreateTicketAsync` override as shown [here](https://github.com/aspnet/AspNetCore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40).</span></span> <span data-ttu-id="ae977-112">`JsonDocument` implementuje `IDisposable`.</span><span class="sxs-lookup"><span data-stu-id="ae977-112">`JsonDocument` implements `IDisposable`.</span></span>

<span data-ttu-id="ae977-113">Následující seznam popisuje známé změny:</span><span class="sxs-lookup"><span data-stu-id="ae977-113">The following list outlines known changes:</span></span>

- <span data-ttu-id="ae977-114"><xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> se zobrazí `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`.</span><span class="sxs-lookup"><span data-stu-id="ae977-114"><xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> becomes `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`.</span></span> <span data-ttu-id="ae977-115">Podobně jsou ovlivněny všechny odvozené implementace `ClaimAction`.</span><span class="sxs-lookup"><span data-stu-id="ae977-115">All derived implementations of `ClaimAction` are similarly affected.</span></span>
- <span data-ttu-id="ae977-116"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> se naplní `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`</span><span class="sxs-lookup"><span data-stu-id="ae977-116"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> becomes `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`</span></span>
- <span data-ttu-id="ae977-117"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> se naplní `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`</span><span class="sxs-lookup"><span data-stu-id="ae977-117"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> becomes `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`</span></span>
- <span data-ttu-id="ae977-118"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> se odebral jeden starý konstruktor a druhý nahradil `JObject` s `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="ae977-118"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> has had one old constructor removed and the other replaced `JObject` with `JsonElement`.</span></span> <span data-ttu-id="ae977-119">Vlastnost `User` a metoda `RunClaimActions` byly aktualizovány tak, aby odpovídaly.</span><span class="sxs-lookup"><span data-stu-id="ae977-119">The `User` property and `RunClaimActions` method have been updated to match.</span></span>
- <span data-ttu-id="ae977-120"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> nyní přijímá parametr typu `JsonDocument` namísto `JObject`.</span><span class="sxs-lookup"><span data-stu-id="ae977-120"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> now accepts a parameter of type `JsonDocument` instead of `JObject`.</span></span> <span data-ttu-id="ae977-121">Vlastnost `Response` byla aktualizována tak, aby odpovídala.</span><span class="sxs-lookup"><span data-stu-id="ae977-121">The `Response` property has been updated to match.</span></span> <span data-ttu-id="ae977-122">`OAuthTokenResponse` je nyní jednorázově a bude odstraněn `OAuthHandler`.</span><span class="sxs-lookup"><span data-stu-id="ae977-122">`OAuthTokenResponse` is now disposable and will be disposed by `OAuthHandler`.</span></span> <span data-ttu-id="ae977-123">Odvozené implementace OAuth přepisují `ExchangeCodeAsync` nemusíte nakládat `JsonDocument` nebo `OAuthTokenResponse`.</span><span class="sxs-lookup"><span data-stu-id="ae977-123">Derived OAuth implementations overriding `ExchangeCodeAsync` don't need to dispose the `JsonDocument` or `OAuthTokenResponse`.</span></span>
- <span data-ttu-id="ae977-124"><xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> se změnil z `JObject` na `JsonDocument`.</span><span class="sxs-lookup"><span data-stu-id="ae977-124"><xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> changed from `JObject` to `JsonDocument`.</span></span>
- <span data-ttu-id="ae977-125"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> se změnil z `JObject` na `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="ae977-125"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> changed from `JObject` to `JsonElement`.</span></span>
- <span data-ttu-id="ae977-126"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType> se změnil z přijetí `JObject` na `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="ae977-126"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType> changed from accepting `JObject` to `JsonElement`.</span></span>

#### <a name="category"></a><span data-ttu-id="ae977-127">Kategorie</span><span class="sxs-lookup"><span data-stu-id="ae977-127">Category</span></span>

<span data-ttu-id="ae977-128">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ae977-128">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ae977-129">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="ae977-129">Affected APIs</span></span>

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
