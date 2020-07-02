---
ms.openlocfilehash: 77e9d28d79a92cf1523e4ef5779d78394b00ae80
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621987"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a>.NET COM úspěšně zařazování parametrů ByRef SafeArray u událostí

#### <a name="details"></a>Podrobnosti

V .NET Framework 4.7.2 a dřívějších verzích se parametr ByRef [SAFEARRAY](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) v události com nepodaří zařazovat zpátky do nativního kódu.  V této změně je nyní řazení [SAFEARRAY](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) úspěšně zařazování.<ul><li>[x] Quirked</li></ul>

#### <a name="suggestion"></a>Návrh

Pokud správně zařadíte parametry SafeArray typu ByRef u událostí modelu COM, které přeruší provádění, můžete tento kód zakázat přidáním následujícího konfiguračního přepínače do konfigurace aplikace:<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4,8|
|Typ|Modul runtime|
