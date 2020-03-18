---
ms.openlocfilehash: 494e792d63a611cdaedf3e40aa607cfbb0420ae4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901835"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a><span data-ttu-id="6368c-101">Ověřování: Newtonsoft.Json typy nahrazeny</span><span class="sxs-lookup"><span data-stu-id="6368c-101">Authentication: Newtonsoft.Json types replaced</span></span>

<span data-ttu-id="6368c-102">V ASP.NET Core 3.0 byly `Newtonsoft.Json` typy používané v `System.Text.Json` ověřování API nahrazeny typy.</span><span class="sxs-lookup"><span data-stu-id="6368c-102">In ASP.NET Core 3.0, `Newtonsoft.Json` types used in Authentication APIs have been replaced with `System.Text.Json` types.</span></span> <span data-ttu-id="6368c-103">S výjimkou následujících případů zůstává základní použití balíčků ověřování nedotčeno:</span><span class="sxs-lookup"><span data-stu-id="6368c-103">Except for the following cases, basic usage of the Authentication packages remains unaffected:</span></span>

* <span data-ttu-id="6368c-104">Třídy odvozené od poskytovatelů OAuth, například z [aspnet-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).</span><span class="sxs-lookup"><span data-stu-id="6368c-104">Classes derived from the OAuth providers, such as those from [aspnet-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).</span></span>
* <span data-ttu-id="6368c-105">Pokročilé implementace manipulace s deklaracemi.</span><span class="sxs-lookup"><span data-stu-id="6368c-105">Advanced claim manipulation implementations.</span></span>

<span data-ttu-id="6368c-106">Další informace naleznete [v tématu dotnet/aspnetcore#7105](https://github.com/dotnet/aspnetcore/pull/7105).</span><span class="sxs-lookup"><span data-stu-id="6368c-106">For more information, see [dotnet/aspnetcore#7105](https://github.com/dotnet/aspnetcore/pull/7105).</span></span> <span data-ttu-id="6368c-107">Diskuse naleznete [v tématu dotnet/aspnetcore#7289](https://github.com/dotnet/aspnetcore/issues/7289).</span><span class="sxs-lookup"><span data-stu-id="6368c-107">For discussion, see [dotnet/aspnetcore#7289](https://github.com/dotnet/aspnetcore/issues/7289).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6368c-108">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="6368c-108">Version introduced</span></span>

<span data-ttu-id="6368c-109">3.0</span><span class="sxs-lookup"><span data-stu-id="6368c-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6368c-110">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="6368c-110">Recommended action</span></span>

<span data-ttu-id="6368c-111">Pro odvozené implementace OAuth nejběžnější změnou `JObject.Parse` je `JsonDocument.Parse` nahrazení `CreateTicketAsync` v přepsání, jak je znázorněno [zde](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40).</span><span class="sxs-lookup"><span data-stu-id="6368c-111">For derived OAuth implementations, the most common change is to replace `JObject.Parse` with `JsonDocument.Parse` in the `CreateTicketAsync` override as shown [here](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40).</span></span> <span data-ttu-id="6368c-112">`JsonDocument`implementuje `IDisposable`.</span><span class="sxs-lookup"><span data-stu-id="6368c-112">`JsonDocument` implements `IDisposable`.</span></span>

<span data-ttu-id="6368c-113">Následující seznam popisuje známé změny:</span><span class="sxs-lookup"><span data-stu-id="6368c-113">The following list outlines known changes:</span></span>

- <span data-ttu-id="6368c-114"><xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType>se `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`stává .</span><span class="sxs-lookup"><span data-stu-id="6368c-114"><xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> becomes `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`.</span></span> <span data-ttu-id="6368c-115">Všechny odvozené implementace `ClaimAction` jsou podobně ovlivněny.</span><span class="sxs-lookup"><span data-stu-id="6368c-115">All derived implementations of `ClaimAction` are similarly affected.</span></span>
- <span data-ttu-id="6368c-116"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType>se stává`MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`</span><span class="sxs-lookup"><span data-stu-id="6368c-116"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> becomes `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`</span></span>
- <span data-ttu-id="6368c-117"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType>se stává`MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`</span><span class="sxs-lookup"><span data-stu-id="6368c-117"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> becomes `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`</span></span>
- <span data-ttu-id="6368c-118"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext>má jeden starý konstruktor odstraněn a `JObject` `JsonElement`druhý nahrazen .</span><span class="sxs-lookup"><span data-stu-id="6368c-118"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> has had one old constructor removed and the other replaced `JObject` with `JsonElement`.</span></span> <span data-ttu-id="6368c-119">Vlastnost `User` a `RunClaimActions` metoda byly aktualizovány tak, aby odpovídaly.</span><span class="sxs-lookup"><span data-stu-id="6368c-119">The `User` property and `RunClaimActions` method have been updated to match.</span></span>
- <span data-ttu-id="6368c-120"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)>nyní přijímá parametr typu `JsonDocument` namísto `JObject`.</span><span class="sxs-lookup"><span data-stu-id="6368c-120"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> now accepts a parameter of type `JsonDocument` instead of `JObject`.</span></span> <span data-ttu-id="6368c-121">Vlastnost `Response` byla aktualizována tak, aby odpovídala.</span><span class="sxs-lookup"><span data-stu-id="6368c-121">The `Response` property has been updated to match.</span></span> <span data-ttu-id="6368c-122">`OAuthTokenResponse`je nyní na jedno použití `OAuthHandler`a bude zlikvidován .</span><span class="sxs-lookup"><span data-stu-id="6368c-122">`OAuthTokenResponse` is now disposable and will be disposed by `OAuthHandler`.</span></span> <span data-ttu-id="6368c-123">Odvozené oauth implementace `ExchangeCodeAsync` přepsání není nutné `JsonDocument` `OAuthTokenResponse`vyřadit nebo .</span><span class="sxs-lookup"><span data-stu-id="6368c-123">Derived OAuth implementations overriding `ExchangeCodeAsync` don't need to dispose the `JsonDocument` or `OAuthTokenResponse`.</span></span>
- <span data-ttu-id="6368c-124"><xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType>změněna `JObject` `JsonDocument`z na .</span><span class="sxs-lookup"><span data-stu-id="6368c-124"><xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> changed from `JObject` to `JsonDocument`.</span></span>
- <span data-ttu-id="6368c-125"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType>změněna `JObject` `JsonElement`z na .</span><span class="sxs-lookup"><span data-stu-id="6368c-125"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> changed from `JObject` to `JsonElement`.</span></span>
- <span data-ttu-id="6368c-126"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType>změněno `JObject` z `JsonElement`přijetí na .</span><span class="sxs-lookup"><span data-stu-id="6368c-126"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType> changed from accepting `JObject` to `JsonElement`.</span></span>

#### <a name="category"></a><span data-ttu-id="6368c-127">Kategorie</span><span class="sxs-lookup"><span data-stu-id="6368c-127">Category</span></span>

<span data-ttu-id="6368c-128">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6368c-128">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6368c-129">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="6368c-129">Affected APIs</span></span>

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
