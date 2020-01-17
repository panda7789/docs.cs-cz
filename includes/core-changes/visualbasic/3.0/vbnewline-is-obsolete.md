---
ms.openlocfilehash: 95a4c807f5c1077cf52f54b196e904ebc98c32f8
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116347"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft. VisualBasic. konstanty. vbNewLine je zastaralá.

<xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> konstanta je označena jako [\[Zastaralá\]](xref:System.ObsoleteAttribute) od verze .net Core 3,0 Preview 8.

#### <a name="version-introduced"></a>Představená verze

3,0 Preview 8

#### <a name="change-description"></a>Popis změny

Počínaje verzí .NET Core 3,0 Preview 8 byl [zastaralý](xref:System.ObsoleteAttribute) atribut použit na <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> konstanta. Použití konstanty generuje upozornění kompilátoru. V .NET Framework a předchozích verzích rozhraní .NET Core nebyla označena jako zastaralá.

Tato změna byla provedena za účelem podpory Visual Basic jako jazyka pro vývoj pro více platforem. <xref:Microsoft.VisualBasic.Constants.vbNewLine> konstanta je ekvivalentem `\r\n`, sekvence znaků nového řádku ve Windows. V systémech UNIX je znak nového řádku `\n`.

#### <a name="recommended-action"></a>Doporučená akce

[Zastaralá](xref:System.ObsoleteAttribute) zpráva atributu pro <xref:Microsoft.VisualBasic.Constants.vbNewLine> obsahuje následující doporučení:

U návratového a řádkového kanálu použijte <xref:Microsoft.VisualBasic.Constants.vbCrLf>. V případě nového řádku aktuální platformy použijte <xref:System.Environment.NewLine?displayProperty=nameWithType>.

#### <a name="category"></a>Kategorie

Visual Basic

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
