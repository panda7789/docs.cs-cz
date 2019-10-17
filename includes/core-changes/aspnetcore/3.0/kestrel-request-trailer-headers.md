---
ms.openlocfilehash: b0e1d6d720a1c9b827fb4585606e64b545d395d7
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394126"
---
### <a name="kestrel-request-trailer-headers-moved-to-new-collection"></a><span data-ttu-id="ab074-101">Kestrel: hlavičky přípojných vozidel žádosti přesunuté do nové kolekce</span><span class="sxs-lookup"><span data-stu-id="ab074-101">Kestrel: Request trailer headers moved to new collection</span></span>

<span data-ttu-id="ab074-102">V předchozích verzích Kestrel přidal do kolekce hlaviček požadavků hlavičky přípojného bodu HTTP/1.1, když byl text požadavku přečtený na konci.</span><span class="sxs-lookup"><span data-stu-id="ab074-102">In prior versions, Kestrel added HTTP/1.1 chunked trailer headers into the request headers collection when the request body was read to the end.</span></span> <span data-ttu-id="ab074-103">Toto chování způsobilo obavy z nejednoznačnosti mezi hlavičkami a přípojnými vozidly.</span><span class="sxs-lookup"><span data-stu-id="ab074-103">This behavior caused concerns about ambiguity between headers and trailers.</span></span> <span data-ttu-id="ab074-104">Rozhodnutí o přesunutí přípojných vozidel do nové kolekce bylo provedeno.</span><span class="sxs-lookup"><span data-stu-id="ab074-104">The decision was made to move the trailers to a new collection.</span></span>

<span data-ttu-id="ab074-105">V ASP.NET Core 2,2 nejsou dostupné přípojné ovladače HTTP/2, ale teď jsou v této nové kolekci dostupné taky v ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="ab074-105">HTTP/2 request trailers were unavailable in ASP.NET Core 2.2 but are now also available in this new collection in ASP.NET Core 3.0.</span></span>

<span data-ttu-id="ab074-106">Pro přístup k těmto přípojným vozidlům byly přidány nové metody rozšíření žádosti.</span><span class="sxs-lookup"><span data-stu-id="ab074-106">New request extension methods have been added to access these trailers.</span></span>

<span data-ttu-id="ab074-107">Po načtení celého textu žádosti jsou k dispozici Přípojná místa HTTP/1.1.</span><span class="sxs-lookup"><span data-stu-id="ab074-107">HTTP/1.1 trailers are available once the entire request body has been read.</span></span>

<span data-ttu-id="ab074-108">Po přijetí od klienta jsou k dispozici Přípojná místa HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="ab074-108">HTTP/2 trailers are available once they're received from the client.</span></span> <span data-ttu-id="ab074-109">Klient nepošle přípojná vozidla, dokud celý text žádosti nebude alespoň ukládán do vyrovnávací paměti serverem.</span><span class="sxs-lookup"><span data-stu-id="ab074-109">The client won't send the trailers until the entire request body has been at least buffered by the server.</span></span> <span data-ttu-id="ab074-110">Možná budete muset přečíst text žádosti, abyste uvolnili místo ve vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="ab074-110">You may need to read the request body to free up buffer space.</span></span> <span data-ttu-id="ab074-111">Pokud přečtete text žádosti na konec, jsou k dispozici vždy.</span><span class="sxs-lookup"><span data-stu-id="ab074-111">Trailers are always available if you read the request body to the end.</span></span> <span data-ttu-id="ab074-112">Přípojná vozidla označují konec těla.</span><span class="sxs-lookup"><span data-stu-id="ab074-112">The trailers mark the end of the body.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ab074-113">Představená verze</span><span class="sxs-lookup"><span data-stu-id="ab074-113">Version introduced</span></span>

<span data-ttu-id="ab074-114">3.0</span><span class="sxs-lookup"><span data-stu-id="ab074-114">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="ab074-115">Staré chování</span><span class="sxs-lookup"><span data-stu-id="ab074-115">Old behavior</span></span>

<span data-ttu-id="ab074-116">Do kolekce `HttpRequest.Headers` by se přidaly hlavičky žádosti o přípojné vozidlo.</span><span class="sxs-lookup"><span data-stu-id="ab074-116">Request trailer headers would be added to the `HttpRequest.Headers` collection.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="ab074-117">Nové chování</span><span class="sxs-lookup"><span data-stu-id="ab074-117">New behavior</span></span>

<span data-ttu-id="ab074-118">V kolekci `HttpRequest.Headers` **nejsou k dispozici** záhlaví přípojných vozidel.</span><span class="sxs-lookup"><span data-stu-id="ab074-118">Request trailer headers **aren't present** in the `HttpRequest.Headers` collection.</span></span> <span data-ttu-id="ab074-119">Pro přístup k nim použijte následující metody rozšíření `HttpRequest`:</span><span class="sxs-lookup"><span data-stu-id="ab074-119">Use the following extension methods on `HttpRequest` to access them:</span></span>

- <span data-ttu-id="ab074-120">`GetDeclaredTrailers()` – načte hlavičku Request "přívěs", která obsahuje seznam přípojných vozidel, která se mají po tělo očekávat.</span><span class="sxs-lookup"><span data-stu-id="ab074-120">`GetDeclaredTrailers()` - Gets the request "Trailer" header that lists which trailers to expect after the body.</span></span>
- <span data-ttu-id="ab074-121">`SupportsTrailers()` – určuje, zda požadavek podporuje příjem hlaviček přípojných vozidel.</span><span class="sxs-lookup"><span data-stu-id="ab074-121">`SupportsTrailers()` - Indicates if the request supports receiving trailer headers.</span></span>
- <span data-ttu-id="ab074-122">`CheckTrailersAvailable()` – určuje, zda požadavek podporuje Přípojná místa, a pokud jsou k dispozici pro čtení.</span><span class="sxs-lookup"><span data-stu-id="ab074-122">`CheckTrailersAvailable()` - Determines if the request supports trailers and if they're available for reading.</span></span>
- <span data-ttu-id="ab074-123">`GetTrailer(string trailerName)` – Získá požadovanou ukončovací hlavičku z odpovědi.</span><span class="sxs-lookup"><span data-stu-id="ab074-123">`GetTrailer(string trailerName)` - Gets the requested trailing header from the response.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ab074-124">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="ab074-124">Reason for change</span></span>

<span data-ttu-id="ab074-125">Přípojná vozidla jsou klíčovou funkcí ve scénářích, jako je gRPC.</span><span class="sxs-lookup"><span data-stu-id="ab074-125">Trailers are a key feature in scenarios like gRPC.</span></span> <span data-ttu-id="ab074-126">Sloučení přípojných vozidel v nástroji do hlaviček požadavků bylo matoucí pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="ab074-126">Merging the trailers in to request headers was confusing to users.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ab074-127">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="ab074-127">Recommended action</span></span>

<span data-ttu-id="ab074-128">Pro přístup k přípojným vozidlům použijte metody rozšíření související s přívěsem na `HttpRequest`.</span><span class="sxs-lookup"><span data-stu-id="ab074-128">Use the trailer-related extension methods on `HttpRequest` to access trailers.</span></span>

#### <a name="category"></a><span data-ttu-id="ab074-129">Kategorie</span><span class="sxs-lookup"><span data-stu-id="ab074-129">Category</span></span>

<span data-ttu-id="ab074-130">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ab074-130">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ab074-131">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="ab074-131">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.HttpRequest.Headers?displayProperty=nameWithType>

<!--

#### Affected APIs

`P:Microsoft.AspNetCore.Http.HttpRequest.Headers`

-->
