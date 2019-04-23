---
ms.openlocfilehash: 1148d040aa3b292d5c37eb50224413b6ddd202e2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803711"
---
### <a name="servicebase-doesnt-propagate-onstart-exceptions"></a>ServiceBase – nebude šířit OnStart výjimky

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.7 a dřívějších verzích výjimky vyvolané při spuštění služby nejsou šířeny do volajícího <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>.<br/>Počínaje aplikací určených pro rozhraní .NET Framework 4.7.1, modul runtime rozšíří výjimky <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> pro služby, které nejde spustit.|
|Doporučení|Při spuštění služby pokud dojde k výjimce, tato výjimka se rozšíří. Toto by mělo pomoci diagnostikovat případy, kdy služeb nezdaří. <br/>Pokud toto chování nežádoucí, můžete zrušit jeho přidáním následujícího kódu &lt;AppContextSwitchOverrides&gt; elementu &lt;runtime&gt; oddílu konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceProcess.DontThrowExceptionsOnStart=true&quot; /&gt;&#13;&#10;</code></pre>Pokud vaše aplikace cílí na starší verzi než 4.7.1, ale budete chtít mít toto chování, přidejte následující &lt;AppContextSwitchOverrides&gt; elementu &lt;runtime&gt; části vaší aplikace konfigurační soubor:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceProcess.DontThrowExceptionsOnStart=false&quot; /&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.1|
|Type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase)?displayProperty=nameWithType></li><li><xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase[])?displayProperty=nameWithType></li></ul>|
