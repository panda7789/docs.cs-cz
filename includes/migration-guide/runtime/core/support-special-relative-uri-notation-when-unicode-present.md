---
ms.openlocfilehash: 841cb06bf94844d9f4da9dc33e60bad0d43dcd84
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70997585"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a>Podporuje zápis zvláštního relativního identifikátoru URI, pokud je k dispozici Unicode

|   |   |
|---|---|
|Podrobnosti|<xref:System.Uri>již nebude <xref:System.NullReferenceException> při volání <xref:System.Uri.TryCreate%2A> na určité relativní identifikátory URI obsahující kódování Unicode vyvolána. Nejjednodušší reprodukce <xref:System.NullReferenceException> je níže, přičemž dva příkazy jsou ekvivalentní:<pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre>Aby bylo možné reprodukování <xref:System.NullReferenceException>, musí být splněny následující položky:<ul><li>Identifikátor URI musí být zadaný jako relativní k tomu, aby byl s http: a za ním nenásleduje znakem//.</li><li>Identifikátor URI musí obsahovat znaky Unicode nebo nevyhrazené symboly zakódované v procentech.</li></ul>|
|Doporučení|Uživatelé by měli v závislosti na tomto chování zakázat relativní identifikátory URI místo <xref:System.UriKind.Absolute?displayProperty=nameWithType> toho zadat při vytváření identifikátoru URI.|
|Scope|Edge|
|Version|4.7.2|
|type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|
