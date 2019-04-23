---
ms.openlocfilehash: 1ef31202d7c072ca27c21fc22db102aafa6b8de7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803651"
---
### <a name="etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a>Trasování událostí pro Windows EventListeners nezachytí události od poskytovatelů s explicitní klíčová slova (stejně jako zprostředkovatel TPL)

|   |   |
|---|---|
|Podrobnosti|EventListeners trasování událostí pro Windows s maskou prázdné – klíčové slovo nezachytí správně události od poskytovatelů s explicitní klíčová slova. V rozhraní .NET Framework 4.5 zprostředkovatel TPL začal poskytuje explicitní klíčová slova a aktivuje tento problém. V rozhraní .NET Framework 4.6 EventListeners aktualizované na už nebude mít tento problém.|
|Doporučení|Chcete-li tento problém vyřešit, nahraďte volání <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> s voláními EnableEvents přetížení, které explicitně určuje &quot;klíčová slova&quot; maska: <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>. Tento problém nebo chyba byla opravena v rozhraní .NET Framework 4.6 a může vyřešit upgradem na verzi rozhraní .NET Framework.|
|Rozsah|Edge|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li></ul>|
