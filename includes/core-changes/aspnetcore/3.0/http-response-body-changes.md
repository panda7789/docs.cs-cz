---
ms.openlocfilehash: cd66317bc93343e03a73dec74dff534776ca42e4
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198400"
---
### <a name="http-response-body-infrastructure-changes"></a><span data-ttu-id="a347f-101">HTTP: změny infrastruktury textu odpovědi</span><span class="sxs-lookup"><span data-stu-id="a347f-101">HTTP: Response body infrastructure changes</span></span>

<span data-ttu-id="a347f-102">Infrastruktura, která přestala text odpovědi HTTP, se změnila.</span><span class="sxs-lookup"><span data-stu-id="a347f-102">The infrastructure backing an HTTP response body has changed.</span></span> <span data-ttu-id="a347f-103">Pokud používáte `HttpResponse` přímo, neměli byste dělat žádné změny kódu.</span><span class="sxs-lookup"><span data-stu-id="a347f-103">If you're using `HttpResponse` directly, you shouldn't need to make any code changes.</span></span> <span data-ttu-id="a347f-104">Pokud zabalíte nebo nahrazujete `HttpResponse.Body` nebo máte přístup k `HttpContext.Features`, přečtěte si další informace.</span><span class="sxs-lookup"><span data-stu-id="a347f-104">Read further if you're wrapping or replacing `HttpResponse.Body` or accessing `HttpContext.Features`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a347f-105">Představená verze</span><span class="sxs-lookup"><span data-stu-id="a347f-105">Version introduced</span></span>

<span data-ttu-id="a347f-106">3.0</span><span class="sxs-lookup"><span data-stu-id="a347f-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a347f-107">Staré chování</span><span class="sxs-lookup"><span data-stu-id="a347f-107">Old behavior</span></span>

<span data-ttu-id="a347f-108">K tělo odpovědi HTTP bylo přidruženo tři rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="a347f-108">There were three APIs associated with the HTTP response body:</span></span>

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a><span data-ttu-id="a347f-109">Nové chování</span><span class="sxs-lookup"><span data-stu-id="a347f-109">New behavior</span></span>

<span data-ttu-id="a347f-110">Pokud nahradíte `HttpResponse.Body`, nahradí se celý `IHttpResponseBodyFeature` obálkou kolem daného datového proudu pomocí `StreamResponseBodyFeature` pro poskytování výchozích implementací pro všechna očekávaná rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="a347f-110">If you replace `HttpResponse.Body`, it replaces the entire `IHttpResponseBodyFeature` with a wrapper around your given stream using `StreamResponseBodyFeature` to provide default implementations for all of the expected APIs.</span></span> <span data-ttu-id="a347f-111">Nastavení vrátit původní datový proud vrátí tuto změnu.</span><span class="sxs-lookup"><span data-stu-id="a347f-111">Setting back the original stream reverts this change.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a347f-112">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="a347f-112">Reason for change</span></span>

<span data-ttu-id="a347f-113">Motivací je kombinování rozhraní API těla odpovědi do jednoho nového rozhraní funkce.</span><span class="sxs-lookup"><span data-stu-id="a347f-113">The motivation is to combine the response body APIs into a single new feature interface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a347f-114">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="a347f-114">Recommended action</span></span>

<span data-ttu-id="a347f-115">Použijte `IHttpResponseBodyFeature`, kde jste dříve používali `IHttpResponseFeature.Body`, `IHttpSendFileFeature` nebo `IHttpBufferingFeature`.</span><span class="sxs-lookup"><span data-stu-id="a347f-115">Use `IHttpResponseBodyFeature` where you previously were using `IHttpResponseFeature.Body`, `IHttpSendFileFeature`, or `IHttpBufferingFeature`.</span></span>

#### <a name="category"></a><span data-ttu-id="a347f-116">Kategorie</span><span class="sxs-lookup"><span data-stu-id="a347f-116">Category</span></span>

<span data-ttu-id="a347f-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a347f-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a347f-118">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="a347f-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature`
- `P:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body`
- `T:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature`

-->
