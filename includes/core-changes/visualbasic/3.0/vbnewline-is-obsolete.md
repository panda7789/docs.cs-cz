---
ms.openlocfilehash: 072ed716910e2e1f1f98dbddc56d5bd097b75acc
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555904"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft. VisualBasic. konstanty. vbNewLine je zastaralá.

<xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>Konstanta je označena jako [ \[ zastaralá \] ](xref:System.ObsoleteAttribute) od .NET Core 3,0.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="change-description"></a>Popis změny

Počínaje rozhraním .NET Core 3,0 byl [zastaralý](xref:System.ObsoleteAttribute) atribut použit na <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> konstantu. Použití konstanty generuje upozornění kompilátoru. V .NET Framework a předchozích verzích rozhraní .NET Core nebyla označena jako zastaralá.

Tato změna byla provedena za účelem podpory Visual Basic jako jazyka pro vývoj pro více platforem. <xref:Microsoft.VisualBasic.Constants.vbNewLine>Konstanta je ekvivalentem `\r\n` , sekvence znaků nového řádku ve Windows. V systémech UNIX je znak nového řádku `\n` .

#### <a name="recommended-action"></a>Doporučená akce

[Zastaralá](xref:System.ObsoleteAttribute) zpráva atributu pro <xref:Microsoft.VisualBasic.Constants.vbNewLine> zahrnuje následující doporučení:

Pro návrat na začátek řádku a pro posun řádku použijte <xref:Microsoft.VisualBasic.Constants.vbCrLf> . Pro nový řádek aktuální platformy použijte <xref:System.Environment.NewLine?displayProperty=nameWithType> .

#### <a name="category"></a>Kategorie

Visual Basic

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

#### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
