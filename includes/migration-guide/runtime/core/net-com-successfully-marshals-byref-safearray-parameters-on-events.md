---
ms.openlocfilehash: d5768a0c25bcd0880cbffde9e57ca9fe7a81cf06
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59982277"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a>.NET COM úspěšně zařazuje parametry ByRef SafeArray událostí

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.7.2 a předchozími verzemi, ByRef [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) parametru u události COM selže k zařazování zpět do nativního kódu.  Díky této změně [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) je nyní zařazeno úspěšně.<ul><li>[x] quirked</li></ul>|
|Doporučení|Pokud správně zařazování SafeArray typu ByRef parametrů v události COM přeruší provádění, můžete zakázat tento kód tak, že přidáte následující konfigurační přepínač do konfigurace vaší aplikace:<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.8|
|Type|Modul runtime|
