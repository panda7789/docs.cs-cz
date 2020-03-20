---
ms.openlocfilehash: 1ef31202d7c072ca27c21fc22db102aafa6b8de7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858502"
---
### <a name="etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a>ETW EventListeners nezachycují události od poskytovatelů s explicitníklíčová slova (jako poskytovatel TPL)

|   |   |
|---|---|
|Podrobnosti|ETW EventListeners s prázdnou maskou klíčového slova nezachycují události od zprostředkovatelů pomocí explicitních klíčových slov. V rozhraní .NET Framework 4.5 začal poskytovatel TPL poskytovat explicitní klíčová slova a spustil tento problém. V rozhraní .NET Framework 4.6 eventlisteners byly aktualizovány, aby již tento problém.|
|Návrh|Chcete-li tento problém <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> vyřešit, nahraďte volání s volání &quot;enableEvents&quot; přetížení, <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>které explicitně určuje všechny klíčová slova masku použít: . Alternativně tento problém byl opraven v rozhraní .NET Framework 4.6 a může být vyřešen upgradem na tuto verzi rozhraní .NET Framework.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li></ul>|
