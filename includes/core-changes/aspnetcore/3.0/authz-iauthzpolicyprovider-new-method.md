---
ms.openlocfilehash: a16d443a37fb0bb5f6bdc4a39e7dcb4f91c54ead
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393980"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a><span data-ttu-id="62821-101">Autorizace: implementace IAuthorizationPolicyProvider vyžadují novou metodu.</span><span class="sxs-lookup"><span data-stu-id="62821-101">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>

<span data-ttu-id="62821-102">V ASP.NET Core 3,0 byla do `IAuthorizationPolicyProvider` přidána nová metoda `GetFallbackPolicyAsync`.</span><span class="sxs-lookup"><span data-stu-id="62821-102">In ASP.NET Core 3.0, a new `GetFallbackPolicyAsync` method was added to `IAuthorizationPolicyProvider`.</span></span> <span data-ttu-id="62821-103">Tuto záložní zásadu používá middleware autorizace, pokud není zadána žádná zásada.</span><span class="sxs-lookup"><span data-stu-id="62821-103">This fallback policy is used by the authorization middleware when no policy is specified.</span></span>

<span data-ttu-id="62821-104">Další informace najdete v tématu [ASPNET/AspNetCore # 9759](https://github.com/aspnet/AspNetCore/pull/9759).</span><span class="sxs-lookup"><span data-stu-id="62821-104">For more information, see [aspnet/AspNetCore#9759](https://github.com/aspnet/AspNetCore/pull/9759).</span></span> 

#### <a name="version-introduced"></a><span data-ttu-id="62821-105">Představená verze</span><span class="sxs-lookup"><span data-stu-id="62821-105">Version introduced</span></span>

<span data-ttu-id="62821-106">3.0</span><span class="sxs-lookup"><span data-stu-id="62821-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="62821-107">Staré chování</span><span class="sxs-lookup"><span data-stu-id="62821-107">Old behavior</span></span>

<span data-ttu-id="62821-108">Implementace `IAuthorizationPolicyProvider` nevyžadovaly metodu `GetFallbackPolicyAsync`.</span><span class="sxs-lookup"><span data-stu-id="62821-108">Implementations of `IAuthorizationPolicyProvider` didn't require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="62821-109">Nové chování</span><span class="sxs-lookup"><span data-stu-id="62821-109">New behavior</span></span>

<span data-ttu-id="62821-110">Implementace `IAuthorizationPolicyProvider` vyžadují metodu `GetFallbackPolicyAsync`.</span><span class="sxs-lookup"><span data-stu-id="62821-110">Implementations of `IAuthorizationPolicyProvider` require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="62821-111">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="62821-111">Reason for change</span></span>

<span data-ttu-id="62821-112">Nová metoda byla nutná pro nové `AuthorizationMiddleware` pro použití, pokud nejsou zadány žádné zásady.</span><span class="sxs-lookup"><span data-stu-id="62821-112">A new method was needed for the new `AuthorizationMiddleware` to use when no policy is specified.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="62821-113">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="62821-113">Recommended action</span></span>

<span data-ttu-id="62821-114">Přidejte metodu `GetFallbackPolicyAsync` do implementací `IAuthorizationPolicyProvider`.</span><span class="sxs-lookup"><span data-stu-id="62821-114">Add the `GetFallbackPolicyAsync` method to your implementations of `IAuthorizationPolicyProvider`.</span></span>

#### <a name="category"></a><span data-ttu-id="62821-115">Kategorie</span><span class="sxs-lookup"><span data-stu-id="62821-115">Category</span></span>

<span data-ttu-id="62821-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="62821-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="62821-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="62821-117">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
