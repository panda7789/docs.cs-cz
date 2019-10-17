---
ms.openlocfilehash: 22ef5d0f91a4f61ca75203f677bcc14e91d77dc1
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394321"
---
### <a name="http-response-body-infrastructure-changes"></a>HTTP: změny infrastruktury textu odpovědi

Infrastruktura, která přestala text odpovědi HTTP, se změnila. Pokud používáte `HttpResponse` přímo, neměli byste dělat žádné změny kódu. Pokud zabalíte nebo nahrazujete `HttpResponse.Body` nebo máte přístup k `HttpContext.Features`, přečtěte si další informace.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="old-behavior"></a>Staré chování

K tělo odpovědi HTTP bylo přidruženo tři rozhraní API:

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a>Nové chování

Pokud nahradíte `HttpResponse.Body`, nahradí se celý `IHttpResponseBodyFeature` obálkou kolem daného datového proudu pomocí `StreamResponseBodyFeature` pro poskytování výchozích implementací pro všechna očekávaná rozhraní API. Nastavení vrátit původní datový proud vrátí tuto změnu.

#### <a name="reason-for-change"></a>Důvod změny

Motivací je kombinování rozhraní API těla odpovědi do jednoho nového rozhraní funkce.

#### <a name="recommended-action"></a>Doporučená akce

Použijte `IHttpResponseBodyFeature`, kde jste dříve používali `IHttpResponseFeature.Body`, `IHttpSendFileFeature` nebo `IHttpBufferingFeature`.

#### <a name="category"></a>Kategorie

ASP.NET Core

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
