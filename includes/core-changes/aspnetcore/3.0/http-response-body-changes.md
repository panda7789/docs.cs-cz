---
ms.openlocfilehash: cd66317bc93343e03a73dec74dff534776ca42e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198400"
---
### <a name="http-response-body-infrastructure-changes"></a><span data-ttu-id="912e5-101">HTTP: Změny infrastruktury těla odezvy</span><span class="sxs-lookup"><span data-stu-id="912e5-101">HTTP: Response body infrastructure changes</span></span>

<span data-ttu-id="912e5-102">Infrastruktura podporující tělo odpovědi HTTP se změnila.</span><span class="sxs-lookup"><span data-stu-id="912e5-102">The infrastructure backing an HTTP response body has changed.</span></span> <span data-ttu-id="912e5-103">Pokud používáte `HttpResponse` přímo, neměli byste muset provádět žádné změny kódu.</span><span class="sxs-lookup"><span data-stu-id="912e5-103">If you're using `HttpResponse` directly, you shouldn't need to make any code changes.</span></span> <span data-ttu-id="912e5-104">Přečtěte si další informace, `HttpResponse.Body` pokud balíte, nahrazujete nebo přistupujete k aplikaci `HttpContext.Features`.</span><span class="sxs-lookup"><span data-stu-id="912e5-104">Read further if you're wrapping or replacing `HttpResponse.Body` or accessing `HttpContext.Features`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="912e5-105">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="912e5-105">Version introduced</span></span>

<span data-ttu-id="912e5-106">3.0</span><span class="sxs-lookup"><span data-stu-id="912e5-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="912e5-107">Staré chování</span><span class="sxs-lookup"><span data-stu-id="912e5-107">Old behavior</span></span>

<span data-ttu-id="912e5-108">K tělu odpovědi HTTP byla přidružena tři řešení API:</span><span class="sxs-lookup"><span data-stu-id="912e5-108">There were three APIs associated with the HTTP response body:</span></span>

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a><span data-ttu-id="912e5-109">Nové chování</span><span class="sxs-lookup"><span data-stu-id="912e5-109">New behavior</span></span>

<span data-ttu-id="912e5-110">Pokud nahradíte `HttpResponse.Body`, nahradí `IHttpResponseBodyFeature` celý obálku kolem daného `StreamResponseBodyFeature` datového proudu pomocí poskytnout výchozí implementace pro všechny očekávané api.</span><span class="sxs-lookup"><span data-stu-id="912e5-110">If you replace `HttpResponse.Body`, it replaces the entire `IHttpResponseBodyFeature` with a wrapper around your given stream using `StreamResponseBodyFeature` to provide default implementations for all of the expected APIs.</span></span> <span data-ttu-id="912e5-111">Nastavení původního datového proudu vrátí tuto změnu.</span><span class="sxs-lookup"><span data-stu-id="912e5-111">Setting back the original stream reverts this change.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="912e5-112">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="912e5-112">Reason for change</span></span>

<span data-ttu-id="912e5-113">Motivací je kombinovat rozhraní API těla odezvy do jednoho rozhraní nové funkce.</span><span class="sxs-lookup"><span data-stu-id="912e5-113">The motivation is to combine the response body APIs into a single new feature interface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="912e5-114">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="912e5-114">Recommended action</span></span>

<span data-ttu-id="912e5-115">Místo `IHttpResponseBodyFeature` použití dříve `IHttpResponseFeature.Body`používali `IHttpSendFileFeature`, `IHttpBufferingFeature`nebo .</span><span class="sxs-lookup"><span data-stu-id="912e5-115">Use `IHttpResponseBodyFeature` where you previously were using `IHttpResponseFeature.Body`, `IHttpSendFileFeature`, or `IHttpBufferingFeature`.</span></span>

#### <a name="category"></a><span data-ttu-id="912e5-116">Kategorie</span><span class="sxs-lookup"><span data-stu-id="912e5-116">Category</span></span>

<span data-ttu-id="912e5-117">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="912e5-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="912e5-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="912e5-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature`
- `P:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body`
- `T:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature`

-->
