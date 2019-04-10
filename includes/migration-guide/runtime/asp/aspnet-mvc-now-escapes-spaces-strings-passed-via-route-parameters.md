---
ms.openlocfilehash: 2278d82d5362fe217ca4bce02a052d4b440843c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236651"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a>ASP.NET MVC řídicí sekvence nyní mezery v řetězcích předaný prostřednictvím parametry trasy

|   |   |
|---|---|
|Podrobnosti|Aby bylo možné v souladu s RFC 2396 mezery v trasy cesty jsou nyní uvozeny řídicími znaky při naplňování parametry akce z trasy. Tak že <code>/controller/action/some data</code> dříve odpovídá trase <code>/controller/action/{data}</code> a poskytují <code>some data</code> jako parametr data, se teď poskytují <code>some%20data</code> místo.|
|Doporučení|Kód by měl aktualizovat, aby unescape parametry řetězce z trasy. V případě potřeby původní identifikátor URI lze přistupovat pomocí <xref:System.Net.HttpWebRequest.RequestUri>. OriginalString rozhraní API.|
|Rozsah|Vedlejší|
|Version|4.5.2|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)?displayProperty=nameWithType></li></ul>|
