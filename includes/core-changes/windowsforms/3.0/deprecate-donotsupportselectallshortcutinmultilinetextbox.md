---
ms.openlocfilehash: a9d0fe3516ade04bc38b804268a9d989f6891d80
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643989"
---
### <a name="switchsystemwindowsformsdonotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a>Přepínač kompatibility. System. Windows. Forms. DoNotSupportSelectAllShortcutInMultilineTextBox není podporovaný.

V model Windows Forms .NET Core 3,0 není podporován přepínač kompatibility `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`, který byl představen v .NET Framework 4.6.1.

#### <a name="change-description"></a>Změnit popis

Počínaje .NET Framework 4.6.1 vybere <kbd>klávesu Ctrl</kbd> <kbd> + </kbd> klávesovou zkratku v ovládacím prvku <xref:System.Windows.Forms.TextBox> vybraný veškerý text. V .NET Framework 4,6 a předchozích verzích se při výběru <kbd>klávesy Ctrl</kbd> <kbd> + klávesové</kbd> zkratky nepodařilo vybrat veškerý text, pokud jsou vlastnosti [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) a <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> nastaveny na `true`. Přepínač kompatibility `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` byl představen v .NET Framework 4.6.1 za účelem zachování původního chování. Další informace najdete v tématu <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.

V rozhraní .NET Core není přepínač `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` podporován.

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
