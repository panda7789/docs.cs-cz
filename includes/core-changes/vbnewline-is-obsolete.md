---
ms.openlocfilehash: 2a0ebcf61fd96df6d2235962c1f1e9cac3fb22e6
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988505"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft. VisualBasic. konstanty. vbNewLine je zastaralá.

Konstanta je označena jako [zastaralá](xref:System.ObsoleteAttribute) v .NET Framework, ale v knihovně .NET Core 3,0 se předtím chyběl atribut. <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

#### <a name="version-introduced"></a>Představená verze

.NET Core 3,0 Preview 8

#### <a name="details"></a>Podrobnosti

Počínaje verzí .NET Core 3,0 Preview 8 byl [zastaralý](xref:System.ObsoleteAttribute) atribut použit na <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> `vbNewLine` konstantu, aby odpovídal v .NET Framework. `vbNewLine` Použití konstanty generuje upozornění kompilátoru. 

V předchozích verzích .NET Core `vbNewLine` nevzniklo upozornění kompilátoru.

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

