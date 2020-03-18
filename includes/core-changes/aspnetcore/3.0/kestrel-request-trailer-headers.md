---
ms.openlocfilehash: b0e1d6d720a1c9b827fb4585606e64b545d395d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394126"
---
### <a name="kestrel-request-trailer-headers-moved-to-new-collection"></a><span data-ttu-id="5a8b3-101">Poštolka: Žádost trailer záhlaví přesunuta do nové kolekce</span><span class="sxs-lookup"><span data-stu-id="5a8b3-101">Kestrel: Request trailer headers moved to new collection</span></span>

<span data-ttu-id="5a8b3-102">V předchozích verzích Kestrel přidal hlavičky přívěsu HTTP/1.1 chunked do kolekce hlavičky požadavku, když bylo tělo požadavku přečteno až do konce.</span><span class="sxs-lookup"><span data-stu-id="5a8b3-102">In prior versions, Kestrel added HTTP/1.1 chunked trailer headers into the request headers collection when the request body was read to the end.</span></span> <span data-ttu-id="5a8b3-103">Toto chování způsobilo obavy z nejednoznačnosti mezi záhlavími a přívěsy.</span><span class="sxs-lookup"><span data-stu-id="5a8b3-103">This behavior caused concerns about ambiguity between headers and trailers.</span></span> <span data-ttu-id="5a8b3-104">Bylo rozhodnuto přesunout přívěsy do nové kolekce.</span><span class="sxs-lookup"><span data-stu-id="5a8b3-104">The decision was made to move the trailers to a new collection.</span></span>

<span data-ttu-id="5a8b3-105">HTTP/2 požadavek přívěsy nebyly k dispozici v ASP.NET Core 2.2, ale jsou nyní k dispozici také v této nové kolekci v ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="5a8b3-105">HTTP/2 request trailers were unavailable in ASP.NET Core 2.2 but are now also available in this new collection in ASP.NET Core 3.0.</span></span>

<span data-ttu-id="5a8b3-106">Pro přístup k těmto přípojkovým vozidlům byly přidány nové metody rozšíření požadavků.</span><span class="sxs-lookup"><span data-stu-id="5a8b3-106">New request extension methods have been added to access these trailers.</span></span>

<span data-ttu-id="5a8b3-107">Přívěsy HTTP/1.1 jsou k dispozici po přečtení celého těla požadavku.</span><span class="sxs-lookup"><span data-stu-id="5a8b3-107">HTTP/1.1 trailers are available once the entire request body has been read.</span></span>

<span data-ttu-id="5a8b3-108">Upoutávky HTTP/2 jsou k dispozici po přijetí od klienta.</span><span class="sxs-lookup"><span data-stu-id="5a8b3-108">HTTP/2 trailers are available once they're received from the client.</span></span> <span data-ttu-id="5a8b3-109">Klient nebude posílat přívěsy, dokud celý tělo požadavku byl alespoň do vyrovnávací paměti serverem.</span><span class="sxs-lookup"><span data-stu-id="5a8b3-109">The client won't send the trailers until the entire request body has been at least buffered by the server.</span></span> <span data-ttu-id="5a8b3-110">Možná budete muset přečíst tělo požadavku uvolnit vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="5a8b3-110">You may need to read the request body to free up buffer space.</span></span> <span data-ttu-id="5a8b3-111">Přívěsy jsou vždy k dispozici, pokud čtete tělo požadavku až do konce.</span><span class="sxs-lookup"><span data-stu-id="5a8b3-111">Trailers are always available if you read the request body to the end.</span></span> <span data-ttu-id="5a8b3-112">Přívěsy označují konec karoserie.</span><span class="sxs-lookup"><span data-stu-id="5a8b3-112">The trailers mark the end of the body.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5a8b3-113">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="5a8b3-113">Version introduced</span></span>

<span data-ttu-id="5a8b3-114">3.0</span><span class="sxs-lookup"><span data-stu-id="5a8b3-114">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="5a8b3-115">Staré chování</span><span class="sxs-lookup"><span data-stu-id="5a8b3-115">Old behavior</span></span>

<span data-ttu-id="5a8b3-116">Žádost trailer záhlaví by být `HttpRequest.Headers` přidány do kolekce.</span><span class="sxs-lookup"><span data-stu-id="5a8b3-116">Request trailer headers would be added to the `HttpRequest.Headers` collection.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="5a8b3-117">Nové chování</span><span class="sxs-lookup"><span data-stu-id="5a8b3-117">New behavior</span></span>

<span data-ttu-id="5a8b3-118">V `HttpRequest.Headers` ynopačních hlavičkách request **trailer nejsou k dispozici.**</span><span class="sxs-lookup"><span data-stu-id="5a8b3-118">Request trailer headers **aren't present** in the `HttpRequest.Headers` collection.</span></span> <span data-ttu-id="5a8b3-119">Pro přístup `HttpRequest` k nim použijte následující metody rozšíření:</span><span class="sxs-lookup"><span data-stu-id="5a8b3-119">Use the following extension methods on `HttpRequest` to access them:</span></span>

- <span data-ttu-id="5a8b3-120">`GetDeclaredTrailers()`- Dostane žádost "Trailer" záhlaví, které uvádí, které přívěsy očekávat po těle.</span><span class="sxs-lookup"><span data-stu-id="5a8b3-120">`GetDeclaredTrailers()` - Gets the request "Trailer" header that lists which trailers to expect after the body.</span></span>
- <span data-ttu-id="5a8b3-121">`SupportsTrailers()`- Označuje, zda požadavek podporuje příjem záhlaví přívěsu.</span><span class="sxs-lookup"><span data-stu-id="5a8b3-121">`SupportsTrailers()` - Indicates if the request supports receiving trailer headers.</span></span>
- <span data-ttu-id="5a8b3-122">`CheckTrailersAvailable()`- Určuje, zda žádost podporuje přívěsy a zda jsou k dispozici pro čtení.</span><span class="sxs-lookup"><span data-stu-id="5a8b3-122">`CheckTrailersAvailable()` - Determines if the request supports trailers and if they're available for reading.</span></span>
- <span data-ttu-id="5a8b3-123">`GetTrailer(string trailerName)`- Získá požadované koncové hlavičky z odpovědi.</span><span class="sxs-lookup"><span data-stu-id="5a8b3-123">`GetTrailer(string trailerName)` - Gets the requested trailing header from the response.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="5a8b3-124">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="5a8b3-124">Reason for change</span></span>

<span data-ttu-id="5a8b3-125">Upoutávky jsou klíčovou funkcí ve scénářích, jako je gRPC.</span><span class="sxs-lookup"><span data-stu-id="5a8b3-125">Trailers are a key feature in scenarios like gRPC.</span></span> <span data-ttu-id="5a8b3-126">Sloučení přívěsů do požádat záhlaví bylo matoucí pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="5a8b3-126">Merging the trailers in to request headers was confusing to users.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5a8b3-127">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="5a8b3-127">Recommended action</span></span>

<span data-ttu-id="5a8b3-128">Pro přístup k přípojovým vozidlům použijte metody rozšíření týkající se přívěsu. `HttpRequest`</span><span class="sxs-lookup"><span data-stu-id="5a8b3-128">Use the trailer-related extension methods on `HttpRequest` to access trailers.</span></span>

#### <a name="category"></a><span data-ttu-id="5a8b3-129">Kategorie</span><span class="sxs-lookup"><span data-stu-id="5a8b3-129">Category</span></span>

<span data-ttu-id="5a8b3-130">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5a8b3-130">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5a8b3-131">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5a8b3-131">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.HttpRequest.Headers?displayProperty=nameWithType>

<!--

#### Affected APIs

`P:Microsoft.AspNetCore.Http.HttpRequest.Headers`

-->
