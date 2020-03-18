---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394352"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a><span data-ttu-id="1bcd1-101">Identita: SignInAsync vyvolá výjimku pro neověřenou identitu</span><span class="sxs-lookup"><span data-stu-id="1bcd1-101">Identity: SignInAsync throws exception for unauthenticated identity</span></span>

<span data-ttu-id="1bcd1-102">Ve výchozím `SignInAsync` nastavení vyvolá výjimku pro objekty `IsAuthenticated` `false`zabezpečení / identity, ve kterém je .</span><span class="sxs-lookup"><span data-stu-id="1bcd1-102">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1bcd1-103">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="1bcd1-103">Version introduced</span></span>

<span data-ttu-id="1bcd1-104">3.0</span><span class="sxs-lookup"><span data-stu-id="1bcd1-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="1bcd1-105">Staré chování</span><span class="sxs-lookup"><span data-stu-id="1bcd1-105">Old behavior</span></span>

<span data-ttu-id="1bcd1-106">`SignInAsync`přijímá všechny objekty / identity, včetně `IsAuthenticated` `false`identit, ve kterých je .</span><span class="sxs-lookup"><span data-stu-id="1bcd1-106">`SignInAsync` accepts any principals / identities, including identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="1bcd1-107">Nové chování</span><span class="sxs-lookup"><span data-stu-id="1bcd1-107">New behavior</span></span>

<span data-ttu-id="1bcd1-108">Ve výchozím `SignInAsync` nastavení vyvolá výjimku pro objekty `IsAuthenticated` `false`zabezpečení / identity, ve kterém je .</span><span class="sxs-lookup"><span data-stu-id="1bcd1-108">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span> <span data-ttu-id="1bcd1-109">Je nový příznak potlačit toto chování, ale výchozí chování se změnilo.</span><span class="sxs-lookup"><span data-stu-id="1bcd1-109">There's a new flag to suppress this behavior, but the default behavior has changed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1bcd1-110">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="1bcd1-110">Reason for change</span></span>

<span data-ttu-id="1bcd1-111">Staré chování bylo problematické, protože ve výchozím nastavení `[Authorize]`  /  `RequireAuthenticatedUser()`byly tyto objekty odmítnuty .</span><span class="sxs-lookup"><span data-stu-id="1bcd1-111">The old behavior was problematic because, by default, these principals were rejected by `[Authorize]` / `RequireAuthenticatedUser()`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1bcd1-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="1bcd1-112">Recommended action</span></span>

<span data-ttu-id="1bcd1-113">V ASP.NET Core 3.0 Preview 6 `RequireAuthenticatedSignIn` je `AuthenticationOptions` ve `true` výchozím nastavení příznak.</span><span class="sxs-lookup"><span data-stu-id="1bcd1-113">In ASP.NET Core 3.0 Preview 6, there's a `RequireAuthenticatedSignIn` flag on `AuthenticationOptions` that is `true` by default.</span></span> <span data-ttu-id="1bcd1-114">Nastavte tento `false` příznak obnovit staré chování.</span><span class="sxs-lookup"><span data-stu-id="1bcd1-114">Set this flag to `false` to restore the old behavior.</span></span>

#### <a name="category"></a><span data-ttu-id="1bcd1-115">Kategorie</span><span class="sxs-lookup"><span data-stu-id="1bcd1-115">Category</span></span>

<span data-ttu-id="1bcd1-116">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="1bcd1-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1bcd1-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="1bcd1-117">Affected APIs</span></span>

<span data-ttu-id="1bcd1-118">Žádný</span><span class="sxs-lookup"><span data-stu-id="1bcd1-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
