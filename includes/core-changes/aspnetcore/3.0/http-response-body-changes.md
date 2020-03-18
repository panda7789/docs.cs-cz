---
ms.openlocfilehash: cd66317bc93343e03a73dec74dff534776ca42e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198400"
---
### <a name="http-response-body-infrastructure-changes"></a>HTTP: Změny infrastruktury těla odezvy

Infrastruktura podporující tělo odpovědi HTTP se změnila. Pokud používáte `HttpResponse` přímo, neměli byste muset provádět žádné změny kódu. Přečtěte si další informace, `HttpResponse.Body` pokud balíte, nahrazujete nebo přistupujete k aplikaci `HttpContext.Features`.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="old-behavior"></a>Staré chování

K tělu odpovědi HTTP byla přidružena tři řešení API:

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a>Nové chování

Pokud nahradíte `HttpResponse.Body`, nahradí `IHttpResponseBodyFeature` celý obálku kolem daného `StreamResponseBodyFeature` datového proudu pomocí poskytnout výchozí implementace pro všechny očekávané api. Nastavení původního datového proudu vrátí tuto změnu.

#### <a name="reason-for-change"></a>Důvod změny

Motivací je kombinovat rozhraní API těla odezvy do jednoho rozhraní nové funkce.

#### <a name="recommended-action"></a>Doporučená akce

Místo `IHttpResponseBodyFeature` použití dříve `IHttpResponseFeature.Body`používali `IHttpSendFileFeature`, `IHttpBufferingFeature`nebo .

#### <a name="category"></a>Kategorie

Jádro ASP.NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature`
- `P:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body`
- `T:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature`

-->
