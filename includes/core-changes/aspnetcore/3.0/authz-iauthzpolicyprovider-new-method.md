---
ms.openlocfilehash: 58dbb73902c0226fa81acf1a70de2160f406f6c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901984"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a><span data-ttu-id="73030-101">Autorizace: Implementace IAuthorizationPolicyProvider vyžadují novou metodu</span><span class="sxs-lookup"><span data-stu-id="73030-101">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>

<span data-ttu-id="73030-102">V ASP.NET Core 3.0 `GetFallbackPolicyAsync` byla do `IAuthorizationPolicyProvider`aplikace přidána nová metoda .</span><span class="sxs-lookup"><span data-stu-id="73030-102">In ASP.NET Core 3.0, a new `GetFallbackPolicyAsync` method was added to `IAuthorizationPolicyProvider`.</span></span> <span data-ttu-id="73030-103">Tato záložní zásada je používána middleware autorizace, pokud není zadána žádná zásada.</span><span class="sxs-lookup"><span data-stu-id="73030-103">This fallback policy is used by the authorization middleware when no policy is specified.</span></span>

<span data-ttu-id="73030-104">Další informace naleznete [v tématu dotnet/aspnetcore#9759](https://github.com/dotnet/aspnetcore/pull/9759).</span><span class="sxs-lookup"><span data-stu-id="73030-104">For more information, see [dotnet/aspnetcore#9759](https://github.com/dotnet/aspnetcore/pull/9759).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="73030-105">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="73030-105">Version introduced</span></span>

<span data-ttu-id="73030-106">3.0</span><span class="sxs-lookup"><span data-stu-id="73030-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="73030-107">Staré chování</span><span class="sxs-lookup"><span data-stu-id="73030-107">Old behavior</span></span>

<span data-ttu-id="73030-108">Implementace `IAuthorizationPolicyProvider` nevyžadovaly metodu. `GetFallbackPolicyAsync`</span><span class="sxs-lookup"><span data-stu-id="73030-108">Implementations of `IAuthorizationPolicyProvider` didn't require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="73030-109">Nové chování</span><span class="sxs-lookup"><span data-stu-id="73030-109">New behavior</span></span>

<span data-ttu-id="73030-110">Implementace vyžadují `IAuthorizationPolicyProvider` metodu. `GetFallbackPolicyAsync`</span><span class="sxs-lookup"><span data-stu-id="73030-110">Implementations of `IAuthorizationPolicyProvider` require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="73030-111">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="73030-111">Reason for change</span></span>

<span data-ttu-id="73030-112">Pro nové `AuthorizationMiddleware` použití nové metody byla zapotřebí nová metoda, pokud není zadána žádná zásada.</span><span class="sxs-lookup"><span data-stu-id="73030-112">A new method was needed for the new `AuthorizationMiddleware` to use when no policy is specified.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="73030-113">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="73030-113">Recommended action</span></span>

<span data-ttu-id="73030-114">Přidejte `GetFallbackPolicyAsync` metodu do `IAuthorizationPolicyProvider`implementace aplikace .</span><span class="sxs-lookup"><span data-stu-id="73030-114">Add the `GetFallbackPolicyAsync` method to your implementations of `IAuthorizationPolicyProvider`.</span></span>

#### <a name="category"></a><span data-ttu-id="73030-115">Kategorie</span><span class="sxs-lookup"><span data-stu-id="73030-115">Category</span></span>

<span data-ttu-id="73030-116">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="73030-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="73030-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="73030-117">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
