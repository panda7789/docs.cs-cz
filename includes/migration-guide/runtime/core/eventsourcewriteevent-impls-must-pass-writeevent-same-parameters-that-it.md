---
ms.openlocfilehash: 662c140f019add66ff6605d47ad1f32c3f50d711
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619975"
---
### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a>EventSource. WriteEvent impls musí předat WriteEvent stejné parametry (plus ID).

#### <a name="details"></a>Podrobnosti

Modul runtime nyní vynutil kontrakt, který určuje následující: třída odvozená z <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> , která definuje metodu události ETW, musí volat metodu základní třídy <code>EventSource.WriteEvent</code> s ID události následovaný stejnými argumenty, které byla metoda události ETW úspěšná.

#### <a name="suggestion"></a>Návrh

<xref:System.IndexOutOfRangeException?displayProperty=fullName>Výjimka je vyvolána, pokud je <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> v procesu načtena data pro zdroj události, který je v rozporu s touto smlouvou.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.5.1|
|Typ|Modul runtime|
