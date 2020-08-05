---
ms.openlocfilehash: 3fb8807a9b6f0bb0d2bc746f5e89eaa8a81d6aa8
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556159"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a>Přepínač kompatibility DoNotSupportSelectAllShortcutInMultilineTextBox se nepodporuje.

`Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`Přepínač kompatibility, který byl představen v .NET Framework 4.6.1, není podporován v model Windows Forms v rozhraní .NET Core a .net 5,0 a novějším.

#### <a name="change-description"></a>Popis změny

Počínaje .NET Framework 4.6.1 vyberete <kbd>klávesovou zkratku CTRL</kbd>  +  <kbd>A</kbd> v <xref:System.Windows.Forms.TextBox> ovládacím prvku vybraný veškerý text. V .NET Framework 4,6 a předchozích verzích se při výběru <kbd>klávesy CTRL</kbd>  +  <kbd>a</kbd> klávesové zkratky nepovedlo vybrat veškerý text, pokud by vlastnost [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) a <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> Properties byla obě nastavená na `true` . `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`Přepínač kompatibility byl představen v .NET Framework 4.6.1 za účelem zachování původního chování. Další informace naleznete zde <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.

V rozhraní .NET Core a .NET 5,0 a novějších verzích není `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` přepínač podporován.

#### <a name="version-introduced"></a>Představená verze

3.0

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
