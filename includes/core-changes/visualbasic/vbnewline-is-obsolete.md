---
ms.openlocfilehash: e476039ff9c8d33f54a2f7e4371dc09a3be557c7
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237323"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft. VisualBasic. konstanty. vbNewLine je zastaralá.

Konstanta <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> je označena jako [zastaralá](xref:System.ObsoleteAttribute) od verze .net Core 3,0 Preview 8.

#### <a name="version-introduced"></a>Představená verze

3,0 Preview 8

#### <a name="change-description"></a>Změnit popis

Počínaje verzí .NET Core 3,0 Preview 8 byl [zastaralý](xref:System.ObsoleteAttribute) atribut použit na konstantu <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>. Použití konstanty generuje upozornění kompilátoru. V předchozích verzích rozhraní .NET Core a .NET Framework nebyla označena jako zastaralá.

Tato změna byla provedena za účelem podpory Visual Basic jako jazyka pro vývoj pro více platforem. Konstanta `vbNewLine` je ekvivalentem `\r\n`, sekvence znaků nového řádku ve Windows. V počítačích se systémem UNIX je znak nového řádku `\n`.
 
#### <a name="recommended-action"></a>Doporučená akce

[Zastaralá](xref:System.ObsoleteAttribute) zpráva atributu pro `vbNewLine` zahrnuje následující doporučení:

> Pro návrat na začátek řádku a pro posun řádku použijte [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf). V případě nového řádku aktuální platformy použijte <xref:System.Environment.NewLine?displayProperty=nameWithType>.

#### <a name="category"></a>Category

Visual Basic

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
