---
ms.openlocfilehash: 81b104d8e5a9ccc8e790c3b16e4837cfa0c0def5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858924"
---
### <a name="serialport-background-thread-exceptions"></a>Výjimky vlákna na pozadí SerialPort

|   |   |
|---|---|
|Podrobnosti|Vlákna na <xref:System.IO.Ports.SerialPort> pozadí vytvořená pomocí datových proudů již neukončí proces při vyvolání výjimek operačního režimu. <br/>V aplikacích, které cílí na rozhraní .NET Framework 4.7 a starší verze, je proces ukončen, když je vyvolána výjimka operačního systému na vlákno na pozadí vytvořené mno stvím datového <xref:System.IO.Ports.SerialPort> proudu. <br/>V aplikacích, které cílí na rozhraní .NET Framework 4.7.1 nebo novější verzi, vlákna na pozadí čekají na události operačního systému související s aktivním sériovým portem a v některých případech mohou dojít k chybě, například náhlé odebrání sériového portu.|
|Návrh|U aplikací, které cílí na rozhraní .NET Framework 4.7.1, můžete odhlásit zpracování <code>&lt;runtime&gt;</code> výjimek, <code>app.config</code> pokud to není žádoucí přidáním následujícího textu do části souboru:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>U aplikací, které cílí na starší verze rozhraní .NET Framework, ale běží v rozhraní .NET Framework 4.7.1 nebo novějším, se můžete přihlásit ke zpracování výjimek přidáním následujících položek do <code>&lt;runtime&gt;</code> části <code>app.config</code> souboru:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.1|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.IO.Ports.SerialPort?displayProperty=nameWithType></li></ul>|
