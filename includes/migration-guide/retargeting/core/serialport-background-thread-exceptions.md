---
ms.openlocfilehash: 448a6160bd64143000c00d21a9ddecdc61b53475
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858924"
---
### <a name="serialport-background-thread-exceptions"></a>SerialPort výjimky vlákna na pozadí

|   |   |
|---|---|
|Podrobnosti|Na pozadí podprocesů, které jsou vytvořené pomocí <xref:System.IO.Ports.SerialPort> datové proudy už ukončit proces při vyvolávání výjimek operačního systému. <br/>V aplikacích, které jsou cíleny na rozhraní .NET Framework 4.7 a starší verze, proces je ukončen po operačního systému se vyvolá výjimka ve vlákně na pozadí vytvořen s <xref:System.IO.Ports.SerialPort> datového proudu. <br/>V aplikacích, cílové rozhraní .NET Framework 4.7.1 nebo novější verze, vláken na pozadí počkejte OS události související s aktivní sériového portu a mohlo dojít k selhání v některých případech, například i s náhlými odebrání sériového portu.|
|Doporučení|Pro aplikace, které cílí .NET Framework 4.7.1, můžete zrušit zpracování výjimek, pokud není žádoucí, přidáním následujícího <code>&lt;runtime&gt;</code> část vaší <code>app.config</code> souboru:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Pro aplikace, které cílí dřívějších verzích rozhraní .NET Framework ale spustit v rozhraní .NET Framework 4.7.1 nebo později, mohou přihlásit a přidejte následující příkaz pro zpracování výjimek <code>&lt;runtime&gt;</code> část vaší <code>app.config</code> souboru:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Scope|Vedlejší|
|Version|4.7.1|
|type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.IO.Ports.SerialPort?displayProperty=nameWithType></li></ul>|

