---
ms.openlocfilehash: 9c72bc686e014a0bffdf272e3813358d1b29cc66
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65198921"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a>.NET COM úspěšně zařazuje parametry ByRef SafeArray událostí

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.7.2 a předchozími verzemi, ByRef [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) parametru u události COM selže k zařazování zpět do nativního kódu.  Díky této změně [SafeArray](https://docs.microsoft.com/en-us/windows/desktop/api/oaidl/ns-oaidl-safearray) je teď úspěšně zařazené.<ul><li>[x] quirked</li></ul>|
|Doporučení|Pokud správně zařazování SafeArray typu ByRef parametrů v události COM přeruší provádění, můžete zakázat tento kód tak, že přidáte následující konfigurační přepínač do konfigurace vaší aplikace:<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Scope|Vedlejší|
|Version|4.8|
|Type|Modul runtime|
