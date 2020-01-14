---
ms.openlocfilehash: 9631e64bb403a3fe7b1b91e8ac592b57ce8068d9
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937081"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a>Přepínač kompatibility DoNotSupportSelectAllShortcutInMultilineTextBox se nepodporuje.

V model Windows Forms .NET Core 3,0 není podporován přepínač kompatibility `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox`, který byl představen v .NET Framework 4.6.1.

#### <a name="change-description"></a>Popis změny

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
