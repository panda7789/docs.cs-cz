---
ms.openlocfilehash: ae5a5fbf97ed4a03de7d35b9d5d5ca8de3aebc39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394342"
---
### <a name="caching-responsecaching-pubternal-types-changed-to-internal"></a><span data-ttu-id="6f99c-101">Ukládání do mezipaměti: ResponseCaching "pubternal" typy změněny na vnitřní</span><span class="sxs-lookup"><span data-stu-id="6f99c-101">Caching: ResponseCaching "pubternal" types changed to internal</span></span>

<span data-ttu-id="6f99c-102">V ASP.NET Core 3.0, "pubternal" typy v `ResponseCaching` byly změněny na `internal`.</span><span class="sxs-lookup"><span data-stu-id="6f99c-102">In ASP.NET Core 3.0, "pubternal" types in `ResponseCaching` have been changed to `internal`.</span></span>

<span data-ttu-id="6f99c-103">Kromě toho výchozí implementace `IResponseCachingPolicyProvider` `IResponseCachingKeyProvider` a již nejsou přidány do `AddResponseCaching` služeb jako součást metody.</span><span class="sxs-lookup"><span data-stu-id="6f99c-103">In addition, default implementations of `IResponseCachingPolicyProvider` and `IResponseCachingKeyProvider` are no longer added to services as part of the `AddResponseCaching` method.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6f99c-104">Popis změny</span><span class="sxs-lookup"><span data-stu-id="6f99c-104">Change description</span></span>

<span data-ttu-id="6f99c-105">V ASP.NET Core jsou typy "pubternal" deklarovány jako, `public` ale `.Internal`jsou umístěny v oboru názvů suffixed s .</span><span class="sxs-lookup"><span data-stu-id="6f99c-105">In ASP.NET Core, "pubternal" types are declared as `public` but reside in a namespace suffixed with `.Internal`.</span></span> <span data-ttu-id="6f99c-106">Zatímco tyto typy jsou veřejné, nemají žádné zásady podpory a jsou předmětem změny.</span><span class="sxs-lookup"><span data-stu-id="6f99c-106">While these types are public, they have no support policy and are subject to breaking changes.</span></span> <span data-ttu-id="6f99c-107">Bohužel náhodné použití těchto typů bylo běžné, což má za následek porušení změn těchto projektů a omezení schopnosti udržovat rámec.</span><span class="sxs-lookup"><span data-stu-id="6f99c-107">Unfortunately, accidental use of these types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6f99c-108">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="6f99c-108">Version introduced</span></span>

<span data-ttu-id="6f99c-109">3.0</span><span class="sxs-lookup"><span data-stu-id="6f99c-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6f99c-110">Staré chování</span><span class="sxs-lookup"><span data-stu-id="6f99c-110">Old behavior</span></span>

<span data-ttu-id="6f99c-111">Tyto typy byly veřejně viditelné, ale nepodporované.</span><span class="sxs-lookup"><span data-stu-id="6f99c-111">These types were publicly visible, but unsupported.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="6f99c-112">Nové chování</span><span class="sxs-lookup"><span data-stu-id="6f99c-112">New behavior</span></span>

<span data-ttu-id="6f99c-113">Tyto typy `internal`jsou nyní .</span><span class="sxs-lookup"><span data-stu-id="6f99c-113">These types are now `internal`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6f99c-114">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="6f99c-114">Reason for change</span></span>

<span data-ttu-id="6f99c-115">Obor `internal` lépe odráží nepodporované zásady.</span><span class="sxs-lookup"><span data-stu-id="6f99c-115">The `internal` scope better reflects the unsupported policy.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6f99c-116">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="6f99c-116">Recommended action</span></span>

<span data-ttu-id="6f99c-117">Zkopírujte typy, které používá vaše aplikace nebo knihovna.</span><span class="sxs-lookup"><span data-stu-id="6f99c-117">Copy types that are used by your app or library.</span></span>

#### <a name="category"></a><span data-ttu-id="6f99c-118">Kategorie</span><span class="sxs-lookup"><span data-stu-id="6f99c-118">Category</span></span>

<span data-ttu-id="6f99c-119">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6f99c-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6f99c-120">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="6f99c-120">Affected APIs</span></span>

- `Microsoft.AspNetCore.ResponseCaching.Internal.CachedResponse`
- `Microsoft.AspNetCore.ResponseCaching.Internal.CachedVaryByRules`
- `Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCache`
- `Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCacheEntry`
- `Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingKeyProvider`
- `Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingPolicyProvider`
- `Microsoft.AspNetCore.ResponseCaching.Internal.MemoryResponseCache`
- `Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingContext`
- `Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingKeyProvider`
- `Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingPolicyProvider`
- <xref:Microsoft.AspNetCore.ResponseCaching.ResponseCachingMiddleware.%23ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.ResponseCaching.ResponseCachingOptions},Microsoft.Extensions.Logging.ILoggerFactory,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingPolicyProvider,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCache,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingKeyProvider)?displayProperty=fullName>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.ResponseCaching.Internal.CachedResponse`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.CachedVaryByRules`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCache`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCacheEntry`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingKeyProvider`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingPolicyProvider`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.MemoryResponseCache`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingContext`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingKeyProvider`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingPolicyProvider`
- `M:Microsoft.AspNetCore.ResponseCaching.ResponseCachingMiddleware.#ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.ResponseCaching.ResponseCachingOptions},Microsoft.Extensions.Logging.ILoggerFactory,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingPolicyProvider,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCache,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingKeyProvider)",
"nameWithType": "ResponseCachingMiddleware.ResponseCachingMiddleware(RequestDelegate, IOptions<ResponseCachingOptions>, ILoggerFactory, IResponseCachingPolicyProvider, IResponseCache, IResponseCachingKeyProvider)`

-->
