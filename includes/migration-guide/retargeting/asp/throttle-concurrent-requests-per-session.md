---
ms.openlocfilehash: 9c3eedb7f7d4cd030a12c141b8630876c1ffdb4d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803730"
---
### <a name="throttle-concurrent-requests-per-session"></a>Omezení souběžných požadavků na relaci

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6.2 a starší, ASP.NET postupně provede žádosti se stejným ID relace a technologie ASP.NET vždy vyvolá Sessionid pomocí souborů cookie ve výchozím nastavení. Pokud stránka trvá dlouhou dobu reagovat, se bude výrazně snížit výkon serveru pouze stisknutím klávesy F5 v prohlížeči. Opravy přidali jsme čítače pro sledování požadavků zařazených do fronty a ukončit požadavky, když se překročí určený limit. Výchozí hodnota je 50. Pokud dosáhnete limitu zaprotokoluje upozornění v případě, že protokol a odpověď HTTP 500 mohou být zaznamenány v protokolu služby IIS.|
|Doporučení|Chcete-li obnovit původní chování, můžete přidat následující nastavení do souboru web.config se odhlásit ze nové chování.<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;aspnet:RequestQueueLimitPerSession&quot; value=&quot;2147483647&quot;/&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7|
|Type|Změna cílení|
