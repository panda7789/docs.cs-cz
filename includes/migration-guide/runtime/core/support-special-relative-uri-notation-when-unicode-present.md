---
ms.openlocfilehash: 841cb06bf94844d9f4da9dc33e60bad0d43dcd84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "70997585"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a>Podpora zvláštního relativního zápisu identifikátoru URI, pokud je k dispozici unicode

|   |   |
|---|---|
|Podrobnosti|<xref:System.Uri>již vyvolá při <xref:System.NullReferenceException> volání <xref:System.Uri.TryCreate%2A> na určité relativní IDENTIFIKÁTORY URI obsahující Unicode. Nejjednodušší reprodukce <xref:System.NullReferenceException> je níže, přičemž dva příkazy jsou rovnocenné:<pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre>Chcete-li <xref:System.NullReferenceException>reprodukovat , musí být pravdivé následující položky:<ul><li>Identifikátor URI musí být určen jako relativní tak, že jej předběžně nastoupíte pomocí http:' a nezaníme jej pomocí '//'.</li><li>Identifikátor URI musí obsahovat symboly Unicode s procenty nebo nevyhrazené symboly.</li></ul>|
|Návrh|Uživatelé v závislosti na tomto chování zakázat <xref:System.UriKind.Absolute?displayProperty=nameWithType> relativní identifikátory URI by měl místo toho určit při vytváření identifikátoru URI.|
|Rozsah|Edge|
|Version|4.7.2|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|
