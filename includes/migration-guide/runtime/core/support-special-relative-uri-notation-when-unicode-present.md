---
ms.openlocfilehash: 08a9292c5a41e7b9b7c1bcc18ec96460de19863f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621070"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a>Podporuje zápis zvláštního relativního identifikátoru URI, pokud je k dispozici Unicode

#### <a name="details"></a>Podrobnosti

<xref:System.Uri>již nebude <xref:System.NullReferenceException> při volání <xref:System.Uri.TryCreate%2A> na určité relativní identifikátory URI obsahující kódování Unicode vyvolána. Nejjednodušší reprodukce <xref:System.NullReferenceException> je níže, přičemž dva příkazy jsou ekvivalentní:<pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre>Aby bylo možné reprodukování <xref:System.NullReferenceException> , musí být splněny následující položky:<ul><li>Identifikátor URI musí být zadaný jako relativní k tomu, aby byl s http: a za ním nenásleduje znakem//.</li><li>Identifikátor URI musí obsahovat znaky Unicode nebo nevyhrazené symboly zakódované v procentech.</li></ul>

#### <a name="suggestion"></a>Návrh

Uživatelé by měli v závislosti na tomto chování zakázat relativní identifikátory URI místo toho zadat <xref:System.UriKind.Absolute?displayProperty=nameWithType> při vytváření identifikátoru URI.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.7.2|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|
