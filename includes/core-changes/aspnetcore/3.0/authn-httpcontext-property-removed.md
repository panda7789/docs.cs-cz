---
ms.openlocfilehash: 60ebcd9fc9ca18c33d31b82ba5020426d22a7d5a
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901966"
---
### <a name="authentication-httpcontextauthentication-property-removed"></a><span data-ttu-id="b3138-101">Ověřování: vlastnost HttpContext. Authentication byla odebrána.</span><span class="sxs-lookup"><span data-stu-id="b3138-101">Authentication: HttpContext.Authentication property removed</span></span>

<span data-ttu-id="b3138-102">Vystaralá vlastnost `Authentication` v `HttpContext` byla odebrána.</span><span class="sxs-lookup"><span data-stu-id="b3138-102">The deprecated `Authentication` property on `HttpContext` has been removed.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b3138-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="b3138-103">Change description</span></span>

<span data-ttu-id="b3138-104">Jako součást [dotnet/aspnetcore # 6504](https://github.com/dotnet/aspnetcore/pull/6504)byla odebrána vystaralá vlastnost `Authentication` v `HttpContext`.</span><span class="sxs-lookup"><span data-stu-id="b3138-104">As part of [dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504), the deprecated `Authentication` property on `HttpContext` has been removed.</span></span> <span data-ttu-id="b3138-105">Vlastnost `Authentication` se od 2,0 nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="b3138-105">The `Authentication` property has been deprecated since 2.0.</span></span> <span data-ttu-id="b3138-106">[Průvodce migrací](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions) byl publikován pro migraci kódu pomocí této zastaralé vlastnosti do nových náhradních rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="b3138-106">A [migration guide](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions) was published to migrate code using this deprecated property to the new replacement APIs.</span></span> <span data-ttu-id="b3138-107">Zbývající nepoužívané třídy/rozhraní API související se starým ASP.NET Core 1. x zásobník ověřování byly v [dotnet/aspnetcore@d7a7c65](https://github.com/dotnet/aspnetcore/commit/d7a7c65)pro zápis odebrány.</span><span class="sxs-lookup"><span data-stu-id="b3138-107">The remaining unused classes / APIs related to the old ASP.NET Core 1.x authentication stack were removed in commit [dotnet/aspnetcore@d7a7c65](https://github.com/dotnet/aspnetcore/commit/d7a7c65).</span></span>

<span data-ttu-id="b3138-108">Diskuzi najdete v tématu [dotnet/aspnetcore # 6533](https://github.com/dotnet/aspnetcore/issues/6533).</span><span class="sxs-lookup"><span data-stu-id="b3138-108">For discussion, see [dotnet/aspnetcore#6533](https://github.com/dotnet/aspnetcore/issues/6533).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b3138-109">Představená verze</span><span class="sxs-lookup"><span data-stu-id="b3138-109">Version introduced</span></span>

<span data-ttu-id="b3138-110">3,0</span><span class="sxs-lookup"><span data-stu-id="b3138-110">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b3138-111">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="b3138-111">Reason for change</span></span>

<span data-ttu-id="b3138-112">Rozhraní API ASP.NET Core 1,0 byla nahrazena metodami rozšíření v <xref:Microsoft.AspNetCore.Authentication.AuthenticationHttpContextExtensions?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="b3138-112">ASP.NET Core 1.0 APIs have been replaced by extension methods in <xref:Microsoft.AspNetCore.Authentication.AuthenticationHttpContextExtensions?displayProperty=fullName>.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b3138-113">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="b3138-113">Recommended action</span></span>

<span data-ttu-id="b3138-114">Viz [Průvodce migrací](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions).</span><span class="sxs-lookup"><span data-stu-id="b3138-114">See the [migration guide](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions).</span></span>

#### <a name="category"></a><span data-ttu-id="b3138-115">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b3138-115">Category</span></span>

<span data-ttu-id="b3138-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b3138-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b3138-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b3138-117">Affected APIs</span></span>

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
