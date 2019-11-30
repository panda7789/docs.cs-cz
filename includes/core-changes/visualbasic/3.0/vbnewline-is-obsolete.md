---
ms.openlocfilehash: 86cdb845c436f424bbcc70e0736568031143b204
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567404"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft. VisualBasic. konstanty. vbNewLine je zastaralá.

<xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>ová konstanta je označena jako [zastaralá](xref:System.ObsoleteAttribute) od verze .net Core 3,0 Preview 8.

#### <a name="version-introduced"></a>Představená verze

3,0 Preview 8

#### <a name="change-description"></a>Změnit popis

Počínaje verzí .NET Core 3,0 Preview 8 byl [zastaralý](xref:System.ObsoleteAttribute) atribut použit na <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> konstanta. Použití konstanty generuje upozornění kompilátoru. V předchozích verzích rozhraní .NET Core a .NET Framework nebyla označena jako zastaralá.

Tato změna byla provedena za účelem podpory Visual Basic jako jazyka pro vývoj pro více platforem. `vbNewLine` konstanta je ekvivalentem `\r\n`, sekvence znaků nového řádku ve Windows. V systémech UNIX je znak nového řádku `\n`.

#### <a name="recommended-action"></a>Doporučená akce

[Zastaralá](xref:System.ObsoleteAttribute) zpráva atributu pro `vbNewLine` obsahuje následující doporučení:

> Pro návrat na začátek řádku a pro posun řádku použijte [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf). V případě nového řádku aktuální platformy použijte <xref:System.Environment.NewLine?displayProperty=nameWithType>.

#### <a name="category"></a>Kategorie

Visual Basic

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
