---
ms.openlocfilehash: 6ff23bbe8c48235770d39cb7d35a1df7de6c5201
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68440259"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a>.NET COM úspěšně zařazování parametrů ByRef SafeArray u událostí

|   |   |
|---|---|
|Podrobnosti|V .NET Framework 4.7.2 a dřívějších verzích se parametr ByRef [SAFEARRAY](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) v události com nepodaří zařazovat zpátky do nativního kódu.  V této změně je nyní řazení [SAFEARRAY](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) úspěšně zařazování.<ul><li>[x] Quirked</li></ul>|
|Doporučení|Pokud správně zařadíte parametry SafeArray typu ByRef u událostí modelu COM, které přeruší provádění, můžete tento kód zakázat přidáním následujícího konfiguračního přepínače do konfigurace aplikace:<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Scope|Vedlejší|
|Version|4.8|
|type|Modul runtime|
