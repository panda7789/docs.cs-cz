---
ms.openlocfilehash: c8a6870a9d34889dd8f5305035744bfc63be6af6
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760720"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a>Podpora speciální relativní identifikátor URI notation při kódování Unicode je k dispozici

|   |   |
|---|---|
|Podrobnosti|<xref:System.Uri> se už přepis nespustí <xref:System.NullReferenceException> při volání metody <xref:System.Uri.TryCreate%2A> na určité relativní identifikátory URI obsahující Unicode.The reprodukci nejjednodušší <xref:System.NullReferenceException> je následující dva příkazy jsou ekvivalentní:<pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre>Chcete-li reprodukovat <xref:System.NullReferenceException>, musí platit následující položky:<ul><li>Identifikátor URI musí být určena jako relativní ji předřazení "http:" a ne za pomocí "/ /".</li><li>Identifikátor URI musí obsahovat procentuálně zakódovaný ve formátu Unicode nebo nevyhrazenou symboly.</li></ul>|
|Doporučení|Uživatelé v závislosti na toto chování zakázat relativní identifikátory URI by měl místo toho zadejte <xref:System.UriKind.Absolute?displayProperty=nameWithType> při vytváření identifikátor URI.|
|Rozsah|Edge|
|Version|4.7.2|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|

