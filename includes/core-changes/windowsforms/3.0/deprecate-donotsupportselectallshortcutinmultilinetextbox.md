---
ms.openlocfilehash: 9631e64bb403a3fe7b1b91e8ac592b57ce8068d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937081"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a>Přepínač kompatibility DoNotSupportSelectAllShortcutInMultilineTextBox se nepodporuje.

Přepínač `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` kompatibility, který byl představen v .NET Framework 4.6.1, není podporován v model Windows Forms .net Core 3,0.

#### <a name="change-description"></a>Popis změny

Počínaje .NET Framework 4.6.1 vyberete <kbd>klávesovou</kbd> + <kbd>zkratku</kbd> CTRL v <xref:System.Windows.Forms.TextBox> ovládacím prvku vybraný veškerý text. V .NET Framework 4,6 a předchozích verzích se při výběru <kbd>klávesy CTRL</kbd> + <kbd>a klávesové zkratky</kbd> nepovedlo vybrat veškerý text, pokud by vlastnost <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) a Properties `true`byla obě nastavená na. Přepínač `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` kompatibility byl představen v .NET Framework 4.6.1 za účelem zachování původního chování. Další informace naleznete zde <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.

V rozhraní .NET Core není `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` přepínač podporován.

#### <a name="version-introduced"></a>Představená verze

3,0 Preview 9

#### <a name="recommended-action"></a>Doporučená akce

Odeberte přepínač. Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- Žádné

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
