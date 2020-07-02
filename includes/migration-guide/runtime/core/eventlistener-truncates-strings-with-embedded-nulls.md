---
ms.openlocfilehash: 6f5c1ecead4e2f74e621354058aab70bfa1cccb6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619966"
---
### <a name="eventlistener-truncates-strings-with-embedded-nulls"></a>Naslouchacího procesu událostí zkrátí řetězce o vložené hodnoty null.

#### <a name="details"></a>Podrobnosti

<xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName>zkrátí řetězce na vložené hodnoty null. Třída nepodporuje znaky null <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> . Tato změna ovlivní pouze aplikace, které používají <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> ke čtení <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> dat v procesu a které používají jako oddělovače znaky null.

#### <a name="suggestion"></a>Návrh

<xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName>data by se měla aktualizovat, pokud je to možné, aby se vložené znaky null nepoužívaly.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5.1|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Diagnostics.Tracing.EventListener.%23ctor></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})?displayProperty=nameWithType></li></ul>|
