---
ms.openlocfilehash: 5ef785f476b795a9c53e511d51b2683b99e6da05
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181980"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft. VisualBasic. konstanty. vbNewLine je zastaralá.

Konstanta je označena jako [zastaralá](xref:System.ObsoleteAttribute) od verze .NET Core 3,0 Preview 8. <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

#### <a name="version-introduced"></a>Představená verze

.NET Core 3,0 Preview 8

#### <a name="details"></a>Podrobnosti

Počínaje verzí .NET Core 3,0 Preview 8 byl [zastaralý](xref:System.ObsoleteAttribute) atribut použit na <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> konstantu. Použití konstanty generuje upozornění kompilátoru. V předchozích verzích rozhraní .NET Core a .NET Framework nebyla označena jako zastaralá.

Tato změna byla provedena za účelem podpory Visual Basic jako jazyka pro vývoj pro více platforem. Konstanta je `\r\n`ekvivalentem, sekvence znaků nového řádku ve Windows. `vbNewLine` V systémech UNIX je `\n`znak nového řádku.
 
#### <a name="recommended-action"></a>Doporučená akce

[Zastaralá](xref:System.ObsoleteAttribute) zpráva atributu `vbNewLine` pro zahrnuje následující doporučení:

> Pro návrat na začátek řádku a pro posun řádku použijte [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf). Pro nový řádek aktuální platformy použijte <xref:System.Environment.NewLine?displayProperty=nameWithType>.

#### <a name="category"></a>Kategorie

Visual Basic

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-- >

