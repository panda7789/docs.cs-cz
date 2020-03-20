---
ms.openlocfilehash: 1148d040aa3b292d5c37eb50224413b6ddd202e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858921"
---
### <a name="servicebase-doesnt-propagate-onstart-exceptions"></a>ServiceBase nerozšíří výjimky OnStart

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.7 a starších verzích nejsou výjimky vyzývané při spuštění služby šířeny volajícímu aplikace <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>.<br/>Počínaje aplikacemi, které cílí na rozhraní .NET Framework 4.7.1, program runtime šíří výjimky <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> pro služby, které se nepodaří spustit.|
|Návrh|Při spuštění služby, pokud existuje výjimka, bude tato výjimka rozšířena. To by mělo pomoci diagnostikovat případy, kdy se služby nespustí. <br/>Pokud je toto chování nežádoucí, můžete se z &lt;něj odhlásit&gt; přidáním &lt;následujícího prvku AppContextSwitchOverrides do části runtime&gt; konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceProcess.DontThrowExceptionsOnStart=true&quot; /&gt;&#13;&#10;</code></pre>Pokud vaše aplikace cílí na starší verzi než 4.7.1, &lt;ale chcete mít&gt; toto &lt;chování, přidejte následující prvek AppContextSwitchOverrides do sekce runtime&gt; konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceProcess.DontThrowExceptionsOnStart=false&quot; /&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.1|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase)?displayProperty=nameWithType></li><li><xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase[])?displayProperty=nameWithType></li></ul>|
