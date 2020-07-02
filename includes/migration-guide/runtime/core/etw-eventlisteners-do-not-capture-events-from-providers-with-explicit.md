---
ms.openlocfilehash: 7d50962b518c15875a5f1a82f5b89ab87a1db02e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619972"
---
### <a name="etw-eventlisteners-do-not-capture-events-from-providers-with-explicit-keywords-like-the-tpl-provider"></a>ETW EventListeners nezachycuje události od zprostředkovatelů s explicitními klíčovými slovy (jako poskytovatel TPL).

#### <a name="details"></a>Podrobnosti

ETW EventListeners s prázdnou maskou klíčového slova nezachycuje správně události od zprostředkovatelů s explicitními klíčovými slovy. V .NET Framework 4,5 poskytovatel TPL začal poskytovat explicitní klíčová slova a aktivoval tento problém. V .NET Framework 4,6 se EventListeners aktualizace, aby už nedošlo k tomuto problému.

#### <a name="suggestion"></a>Návrh

Chcete-li tento problém obejít, nahraďte volání voláním <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)> metody přetížení EnableEvents, která explicitně určuje &quot; masku klíčového slova, která &quot; se má použít: <code>EnableEvents(eventSource, level, unchecked((EventKeywords)0xFFFFffffFFFFffff))</code> . Případně byl tento problém opravený v .NET Framework 4,6 a může se řešit upgradem na verzi .NET Framework.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li></ul>|
