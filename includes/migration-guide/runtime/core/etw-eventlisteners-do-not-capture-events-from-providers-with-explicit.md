---
ms.openlocfilehash: eab476a1d3f275e851e5af4198c30b60ad0c17b8
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858502"
---
### <a name="etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a>Trasování událostí pro Windows EventListeners nezachytí události od poskytovatelů s explicitní klíčová slova (stejně jako zprostředkovatel TPL)

|   |   |
|---|---|
|Podrobnosti|EventListeners trasování událostí pro Windows s maskou prázdné – klíčové slovo nezachytí správně události od poskytovatelů s explicitní klíčová slova. V rozhraní .NET Framework 4.5 zprostředkovatel TPL začal poskytuje explicitní klíčová slova a aktivuje tento problém. V rozhraní .NET Framework 4.6 EventListeners aktualizované na už nebude mít tento problém.|
|Doporučení|Chcete-li tento problém vyřešit, nahraďte volání <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> s voláními EnableEvents přetížení, které explicitně určuje &quot;klíčová slova&quot; maska: <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code>. Tento problém nebo chyba byla opravena v rozhraní .NET Framework 4.6 a může vyřešit upgradem na verzi rozhraní .NET Framework.|
|Scope|Edge|
|Version|4.5|
|type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li></ul>|

