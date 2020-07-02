---
ms.openlocfilehash: c53fe57f3278741a927a2f00b11af6e26dafce66
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619927"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>ASP.NET MVC teď řídí mezery v řetězcích předaných přes parametry směrování.

#### <a name="details"></a>Podrobnosti

Aby bylo možné odpovídat specifikaci RFC 2396, jsou nyní při naplňování parametrů akce z trasy řídicí prostory v cestách tras. Takže, zatímco <code>/controller/action/some data</code> by dřív odpovídal trase <code>/controller/action/{data}</code> a poskytovala <code>some data</code> jako datový parametr, teď <code>some%20data</code> místo toho poskytne.

#### <a name="suggestion"></a>Návrh

Kód by měl být aktualizován na parametry řetězce z trasy. Pokud je nutný původní identifikátor URI, lze k němu přistupovat pomocí <xref:System.Net.HttpWebRequest.RequestUri> . Rozhraní OriginalString API.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.5.2|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)></li></ul>|
