---
ms.openlocfilehash: bba74f26eafd52b966928835d5003d03af1eabdc
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721403"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a>Přepínač kompatibility DoNotSupportSelectAllShortcutInMultilineTextBox se nepodporuje.

`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`Přepínač kompatibility, který byl představen v .NET Framework 4.6.1, není podporován v model Windows Forms .NET Core 3,0.

#### <a name="change-description"></a>Popis změny

Počínaje .NET Framework 4.6.1 vyberete <kbd>klávesovou zkratku CTRL</kbd>  +  <kbd>A</kbd> v <xref:System.Windows.Forms.TextBox> ovládacím prvku vybraný veškerý text. V .NET Framework 4,6 a předchozích verzích se při výběru <kbd>klávesy CTRL</kbd>  +  <kbd>a</kbd> klávesové zkratky nepovedlo vybrat veškerý text, pokud by vlastnost [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) a <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> Properties byla obě nastavená na `true` . `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`Přepínač kompatibility byl představen v .NET Framework 4.6.1 za účelem zachování původního chování. Další informace naleznete zde <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.

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

#### Affected APIs

- Not detectable via API analysis

-->
