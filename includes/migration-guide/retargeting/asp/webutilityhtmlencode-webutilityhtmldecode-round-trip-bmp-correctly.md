---
ms.openlocfilehash: ca662b57fae9b1d0d41290f3052f71bca66e9bf3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234663"
---
### <a name="webutilityhtmlencode-and-webutilityhtmldecode-round-trip-bmp-correctly"></a>WebUtility.HtmlEncode a odezvy BMP WebUtility.HtmlDecode správně

|   |   |
|---|---|
|Podrobnosti|Pro aplikace, které jsou cíleny rozhraní .NET Framework 4.5, znaky, které jsou mimo zpátečního převodu základní vícejazyčné roviny (BMP) správně, když jsou předány <xref:System.Net.WebUtility.HtmlDecode(System.String)> metody.|
|Doporučení|Tato změna by měl mít žádný vliv na aktuální aplikace, ale chcete-li obnovit původní chování, nastavte <code>targetFramework</code> atribut <code>&lt;httpRuntime&gt;</code> na řetězec jiný než &quot;4.5&quot;. Můžete také nastavit <code>unicodeEncodingConformance</code> a <code>unicodeDecodingConformance</code> atributy <code>&lt;webUtility&gt;</code> konfiguračního prvku a řídit tak toto chování nezávisle na cílové verzi rozhraní .NET Framework.|
|Rozsah|Edge|
|Version|4.5|
|Type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Net.WebUtility.HtmlEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlEncode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li></ul>|
