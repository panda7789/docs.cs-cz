---
ms.openlocfilehash: 2b88ab7cfdd7a0a0a770b305ecd0200afd9a9b4b
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441544"
---
### <a name="authorization-resource-in-endpoint-routing-is-httpcontext"></a><span data-ttu-id="53641-101">Autorizace: prostředek ve směrování koncového bodu je HttpContext</span><span class="sxs-lookup"><span data-stu-id="53641-101">Authorization: Resource in endpoint routing is HttpContext</span></span>

<span data-ttu-id="53641-102">Při použití směrování koncových bodů v ASP.NET Core 3,1 prostředek, který se používá pro autorizaci, je koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="53641-102">When using endpoint routing in ASP.NET Core 3.1, the resource used for authorization is the endpoint.</span></span> <span data-ttu-id="53641-103">Tento přístup nebyl dostatečný pro získání přístupu k datům trasy ( <xref:Microsoft.AspNetCore.Routing.RouteData> ).</span><span class="sxs-lookup"><span data-stu-id="53641-103">This approach was insufficient for gaining access to the route data (<xref:Microsoft.AspNetCore.Routing.RouteData>).</span></span> <span data-ttu-id="53641-104">Dříve v MVC <xref:Microsoft.AspNetCore.Http.HttpContext> byl předán prostředek, který umožňuje přístup ke koncovému bodu ( <xref:Microsoft.AspNetCore.Http.Endpoint> ) i k datům směrování.</span><span class="sxs-lookup"><span data-stu-id="53641-104">Previously in MVC, an <xref:Microsoft.AspNetCore.Http.HttpContext> resource was passed in, which allows access to both the endpoint (<xref:Microsoft.AspNetCore.Http.Endpoint>) and the route data.</span></span> <span data-ttu-id="53641-105">Tato změna zajistí, že prostředek předaný autorizaci je vždy `HttpContext` .</span><span class="sxs-lookup"><span data-stu-id="53641-105">This change ensures that the resource passed to authorization is always the `HttpContext`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="53641-106">Představená verze</span><span class="sxs-lookup"><span data-stu-id="53641-106">Version introduced</span></span>

<span data-ttu-id="53641-107">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="53641-107">5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="53641-108">Staré chování</span><span class="sxs-lookup"><span data-stu-id="53641-108">Old behavior</span></span>

<span data-ttu-id="53641-109">Při použití směrování koncových bodů a atributů middleware autorizace ( <xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware> ) nebo [[autorizovat]](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) je prostředek předaný do autorizace shodný s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="53641-109">When using endpoint routing and the authorization middleware (<xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware>) or [[Authorize]](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) attributes, the resource passed to authorization is the matching endpoint.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="53641-110">Nové chování</span><span class="sxs-lookup"><span data-stu-id="53641-110">New behavior</span></span>

<span data-ttu-id="53641-111">Směrování koncového bodu projde `HttpContext` k autorizaci.</span><span class="sxs-lookup"><span data-stu-id="53641-111">Endpoint routing passes the `HttpContext` to authorization.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="53641-112">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="53641-112">Reason for change</span></span>

<span data-ttu-id="53641-113">Ke koncovému bodu se můžete dostat z `HttpContext` .</span><span class="sxs-lookup"><span data-stu-id="53641-113">You can get to the endpoint from the `HttpContext`.</span></span> <span data-ttu-id="53641-114">Neexistoval ale žádný způsob, jak z koncového bodu získat data, jako jsou data o trasách.</span><span class="sxs-lookup"><span data-stu-id="53641-114">However, there was no way to get from the endpoint to things like the route data.</span></span> <span data-ttu-id="53641-115">Došlo ke ztrátě funkčnosti od směrování mimo koncový bod.</span><span class="sxs-lookup"><span data-stu-id="53641-115">There was a loss in functionality from non-endpoint routing.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="53641-116">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="53641-116">Recommended action</span></span>

<span data-ttu-id="53641-117">Pokud vaše aplikace používá prostředek koncového bodu, zavolejte na, <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> `HttpContext` aby se pokračovalo v přístupu ke koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="53641-117">If your app uses the endpoint resource, call <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> on the `HttpContext` to continue accessing the endpoint.</span></span>

<span data-ttu-id="53641-118">V ASP.NET Core 5,0 Preview 8 a novějších verzích se můžete vrátit k původnímu chování pomocí <xref:System.AppContext.SetSwitch%2A> .</span><span class="sxs-lookup"><span data-stu-id="53641-118">In ASP.NET Core 5.0 Preview 8 and later, you can revert to the old behavior with <xref:System.AppContext.SetSwitch%2A>.</span></span> <span data-ttu-id="53641-119">Příklad:</span><span class="sxs-lookup"><span data-stu-id="53641-119">For example:</span></span>

```csharp
AppContext.SetSwitch(
    "Microsoft.AspNetCore.Authorization.SuppressUseHttpContextAsAuthorizationResource",
    isEnabled: true);
```

#### <a name="category"></a><span data-ttu-id="53641-120">Kategorie</span><span class="sxs-lookup"><span data-stu-id="53641-120">Category</span></span>

<span data-ttu-id="53641-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="53641-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="53641-122">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="53641-122">Affected APIs</span></span>

<span data-ttu-id="53641-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="53641-123">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
