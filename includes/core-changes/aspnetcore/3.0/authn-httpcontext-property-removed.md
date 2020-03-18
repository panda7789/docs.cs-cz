---
ms.openlocfilehash: 60ebcd9fc9ca18c33d31b82ba5020426d22a7d5a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901966"
---
### <a name="authentication-httpcontextauthentication-property-removed"></a><span data-ttu-id="e102c-101">Ověřování: Vlastnost HttpContext.Authentication byla odebrána.</span><span class="sxs-lookup"><span data-stu-id="e102c-101">Authentication: HttpContext.Authentication property removed</span></span>

<span data-ttu-id="e102c-102">Zastaralá `Authentication` vlastnost byla `HttpContext` odebrána.</span><span class="sxs-lookup"><span data-stu-id="e102c-102">The deprecated `Authentication` property on `HttpContext` has been removed.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e102c-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="e102c-103">Change description</span></span>

<span data-ttu-id="e102c-104">Jako součást [dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504)byla odebrána `Authentication` zastaralá vlastnost. `HttpContext`</span><span class="sxs-lookup"><span data-stu-id="e102c-104">As part of [dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504), the deprecated `Authentication` property on `HttpContext` has been removed.</span></span> <span data-ttu-id="e102c-105">Ubytovací `Authentication` zařízení je od roku 2.0 zastaralé.</span><span class="sxs-lookup"><span data-stu-id="e102c-105">The `Authentication` property has been deprecated since 2.0.</span></span> <span data-ttu-id="e102c-106">[Průvodce migrací](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions) byl publikován pro migraci kódu pomocí této zastaralé vlastnosti do nových náhradních api.</span><span class="sxs-lookup"><span data-stu-id="e102c-106">A [migration guide](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions) was published to migrate code using this deprecated property to the new replacement APIs.</span></span> <span data-ttu-id="e102c-107">Zbývající nepoužívané třídy / API související se starým ASP.NET zásobníku [dotnet/aspnetcore@d7a7c65](https://github.com/dotnet/aspnetcore/commit/d7a7c65)ověřování Jádra 1.x byly odebrány v potvrzení .</span><span class="sxs-lookup"><span data-stu-id="e102c-107">The remaining unused classes / APIs related to the old ASP.NET Core 1.x authentication stack were removed in commit [dotnet/aspnetcore@d7a7c65](https://github.com/dotnet/aspnetcore/commit/d7a7c65).</span></span>

<span data-ttu-id="e102c-108">Diskuse naleznete [v tématu dotnet/aspnetcore#6533](https://github.com/dotnet/aspnetcore/issues/6533).</span><span class="sxs-lookup"><span data-stu-id="e102c-108">For discussion, see [dotnet/aspnetcore#6533](https://github.com/dotnet/aspnetcore/issues/6533).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e102c-109">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="e102c-109">Version introduced</span></span>

<span data-ttu-id="e102c-110">3.0</span><span class="sxs-lookup"><span data-stu-id="e102c-110">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e102c-111">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="e102c-111">Reason for change</span></span>

<span data-ttu-id="e102c-112">ASP.NET core 1.0 API byly nahrazeny <xref:Microsoft.AspNetCore.Authentication.AuthenticationHttpContextExtensions?displayProperty=fullName>rozšiřujícími metodami v .</span><span class="sxs-lookup"><span data-stu-id="e102c-112">ASP.NET Core 1.0 APIs have been replaced by extension methods in <xref:Microsoft.AspNetCore.Authentication.AuthenticationHttpContextExtensions?displayProperty=fullName>.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e102c-113">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="e102c-113">Recommended action</span></span>

<span data-ttu-id="e102c-114">Podívejte se na [průvodce migrací](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions).</span><span class="sxs-lookup"><span data-stu-id="e102c-114">See the [migration guide](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions).</span></span>

#### <a name="category"></a><span data-ttu-id="e102c-115">Kategorie</span><span class="sxs-lookup"><span data-stu-id="e102c-115">Category</span></span>

<span data-ttu-id="e102c-116">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e102c-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e102c-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e102c-117">Affected APIs</span></span>

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
