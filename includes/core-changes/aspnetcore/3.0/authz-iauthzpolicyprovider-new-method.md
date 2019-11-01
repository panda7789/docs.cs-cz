---
ms.openlocfilehash: 74b989a2413d2192f7cf5208e400eaed879ea096
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198398"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a><span data-ttu-id="6f10e-101">Autorizace: implementace IAuthorizationPolicyProvider vyžadují novou metodu.</span><span class="sxs-lookup"><span data-stu-id="6f10e-101">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>

<span data-ttu-id="6f10e-102">V ASP.NET Core 3,0 byla do `IAuthorizationPolicyProvider` přidána nová metoda `GetFallbackPolicyAsync`.</span><span class="sxs-lookup"><span data-stu-id="6f10e-102">In ASP.NET Core 3.0, a new `GetFallbackPolicyAsync` method was added to `IAuthorizationPolicyProvider`.</span></span> <span data-ttu-id="6f10e-103">Tuto záložní zásadu používá middleware autorizace, pokud není zadána žádná zásada.</span><span class="sxs-lookup"><span data-stu-id="6f10e-103">This fallback policy is used by the authorization middleware when no policy is specified.</span></span>

<span data-ttu-id="6f10e-104">Další informace najdete v tématu [ASPNET/AspNetCore # 9759](https://github.com/aspnet/AspNetCore/pull/9759).</span><span class="sxs-lookup"><span data-stu-id="6f10e-104">For more information, see [aspnet/AspNetCore#9759](https://github.com/aspnet/AspNetCore/pull/9759).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6f10e-105">Představená verze</span><span class="sxs-lookup"><span data-stu-id="6f10e-105">Version introduced</span></span>

<span data-ttu-id="6f10e-106">3.0</span><span class="sxs-lookup"><span data-stu-id="6f10e-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6f10e-107">Staré chování</span><span class="sxs-lookup"><span data-stu-id="6f10e-107">Old behavior</span></span>

<span data-ttu-id="6f10e-108">Implementace `IAuthorizationPolicyProvider` nevyžadovaly metodu `GetFallbackPolicyAsync`.</span><span class="sxs-lookup"><span data-stu-id="6f10e-108">Implementations of `IAuthorizationPolicyProvider` didn't require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="6f10e-109">Nové chování</span><span class="sxs-lookup"><span data-stu-id="6f10e-109">New behavior</span></span>

<span data-ttu-id="6f10e-110">Implementace `IAuthorizationPolicyProvider` vyžadují metodu `GetFallbackPolicyAsync`.</span><span class="sxs-lookup"><span data-stu-id="6f10e-110">Implementations of `IAuthorizationPolicyProvider` require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6f10e-111">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="6f10e-111">Reason for change</span></span>

<span data-ttu-id="6f10e-112">Nová metoda byla nutná pro nové `AuthorizationMiddleware` pro použití, pokud nejsou zadány žádné zásady.</span><span class="sxs-lookup"><span data-stu-id="6f10e-112">A new method was needed for the new `AuthorizationMiddleware` to use when no policy is specified.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6f10e-113">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="6f10e-113">Recommended action</span></span>

<span data-ttu-id="6f10e-114">Přidejte metodu `GetFallbackPolicyAsync` do implementací `IAuthorizationPolicyProvider`.</span><span class="sxs-lookup"><span data-stu-id="6f10e-114">Add the `GetFallbackPolicyAsync` method to your implementations of `IAuthorizationPolicyProvider`.</span></span>

#### <a name="category"></a><span data-ttu-id="6f10e-115">Kategorie</span><span class="sxs-lookup"><span data-stu-id="6f10e-115">Category</span></span>

<span data-ttu-id="6f10e-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6f10e-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6f10e-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="6f10e-117">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
