---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394352"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a><span data-ttu-id="35386-101">Identita: SignInAsync vyvolá výjimku pro neověřenou identitu.</span><span class="sxs-lookup"><span data-stu-id="35386-101">Identity: SignInAsync throws exception for unauthenticated identity</span></span>

<span data-ttu-id="35386-102">Ve výchozím nastavení `SignInAsync` vyvolá výjimku pro objekty zabezpečení/identity, ve kterých `IsAuthenticated` je `false`.</span><span class="sxs-lookup"><span data-stu-id="35386-102">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="35386-103">Představená verze</span><span class="sxs-lookup"><span data-stu-id="35386-103">Version introduced</span></span>

<span data-ttu-id="35386-104">3.0</span><span class="sxs-lookup"><span data-stu-id="35386-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="35386-105">Staré chování</span><span class="sxs-lookup"><span data-stu-id="35386-105">Old behavior</span></span>

<span data-ttu-id="35386-106">`SignInAsync` akceptuje všechny objekty zabezpečení a identity, včetně identit, ve kterých `IsAuthenticated` `false`.</span><span class="sxs-lookup"><span data-stu-id="35386-106">`SignInAsync` accepts any principals / identities, including identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="35386-107">Nové chování</span><span class="sxs-lookup"><span data-stu-id="35386-107">New behavior</span></span>

<span data-ttu-id="35386-108">Ve výchozím nastavení `SignInAsync` vyvolá výjimku pro objekty zabezpečení/identity, ve kterých `IsAuthenticated` je `false`.</span><span class="sxs-lookup"><span data-stu-id="35386-108">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span> <span data-ttu-id="35386-109">Pro potlačení tohoto chování je k dispozici nový příznak, ale došlo ke změně výchozího chování.</span><span class="sxs-lookup"><span data-stu-id="35386-109">There's a new flag to suppress this behavior, but the default behavior has changed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="35386-110">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="35386-110">Reason for change</span></span>

<span data-ttu-id="35386-111">Původní chování bylo problematické, protože ve výchozím nastavení se tyto objekty zabezpečení zamítly `[Authorize]` @ no__t-1 @ no__t-2.</span><span class="sxs-lookup"><span data-stu-id="35386-111">The old behavior was problematic because, by default, these principals were rejected by `[Authorize]` / `RequireAuthenticatedUser()`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="35386-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="35386-112">Recommended action</span></span>

<span data-ttu-id="35386-113">V ASP.NET Core 3,0 Preview 6 existuje příznak `RequireAuthenticatedSignIn` v `AuthenticationOptions`, který je ve výchozím nastavení `true`.</span><span class="sxs-lookup"><span data-stu-id="35386-113">In ASP.NET Core 3.0 Preview 6, there's a `RequireAuthenticatedSignIn` flag on `AuthenticationOptions` that is `true` by default.</span></span> <span data-ttu-id="35386-114">Nastavením tohoto příznaku `false` obnovte původní chování.</span><span class="sxs-lookup"><span data-stu-id="35386-114">Set this flag to `false` to restore the old behavior.</span></span>

#### <a name="category"></a><span data-ttu-id="35386-115">Kategorie</span><span class="sxs-lookup"><span data-stu-id="35386-115">Category</span></span>

<span data-ttu-id="35386-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="35386-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="35386-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="35386-117">Affected APIs</span></span>

<span data-ttu-id="35386-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="35386-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
