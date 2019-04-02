---
ms.openlocfilehash: db8eb017bdf166b0f1a241f5a8f7db9b9430898a
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760211"
---
### <a name="throttle-concurrent-requests-per-session"></a>Omezení souběžných požadavků na relaci

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6.2 a starší, ASP.NET postupně provede žádosti se stejným ID relace a technologie ASP.NET vždy vyvolá Sessionid pomocí souborů cookie ve výchozím nastavení. Pokud stránka trvá dlouhou dobu reagovat, se bude výrazně snížit výkon serveru pouze stisknutím klávesy F5 v prohlížeči. Opravy přidali jsme čítače pro sledování požadavků zařazených do fronty a ukončit požadavky, když se překročí určený limit. Výchozí hodnota je 50. Pokud dosáhnete limitu zaprotokoluje upozornění v případě, že protokol a odpověď HTTP 500 mohou být zaznamenány v protokolu služby IIS.|
|Doporučení|Chcete-li obnovit původní chování, můžete přidat následující nastavení do souboru web.config se odhlásit ze nové chování.<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;aspnet:RequestQueueLimitPerSession&quot; value=&quot;2147483647&quot;/&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7|
|Type|Změna cílení|

