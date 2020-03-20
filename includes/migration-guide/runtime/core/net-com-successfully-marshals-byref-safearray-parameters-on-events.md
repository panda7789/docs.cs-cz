---
ms.openlocfilehash: 6ff23bbe8c48235770d39cb7d35a1df7de6c5201
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "68440259"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a>.NET COM úspěšně zařazuje parametry ByRef SafeArray na události

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.7.2 a starších verzích by parametr ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) při události com selhal při zařazování zpět do nativního kódu.  S touto změnou [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) je nyní seřazené úspěšně.<ul><li>[x] Nevychaný</li></ul>|
|Návrh|Pokud správně zařazování Parametrů ByRef SafeArray na události modelu COM přeruší spuštění, můžete zakázat tento kód přidáním následujícího přepínače konfigurace konfigurace aplikace:<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.8|
|Typ|Modul runtime|
