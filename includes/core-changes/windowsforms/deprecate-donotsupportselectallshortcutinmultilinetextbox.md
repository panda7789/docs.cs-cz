---
ms.openlocfilehash: a9d0fe3516ade04bc38b804268a9d989f6891d80
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181767"
---
### <a name="switchsystemwindowsformsdonotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a>Přepínač kompatibility. System. Windows. Forms. DoNotSupportSelectAllShortcutInMultilineTextBox není podporovaný.

Přepínač `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` kompatibility, který byl představen v .NET Framework 4.6.1, není podporován v model Windows Forms .NET Core 3,0.

#### <a name="change-description"></a>Změnit popis

Počínaje .NET Framework 4.6.1 vyberete <kbd>klávesovou</kbd> + <kbd>zkratku</kbd> CTRL v <xref:System.Windows.Forms.TextBox> ovládacím prvku vybraný veškerý text. V .NET Framework 4,6 a předchozích verzích se při výběru <kbd>klávesy CTRL</kbd> + <kbd>a klávesové zkratky</kbd> nepovedlo vybrat veškerý text, pokud by vlastnost <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> [TextBox. ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) a Properties `true`byla obě nastavená na. Přepínač `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` kompatibility byl představen v .NET Framework 4.6.1 za účelem zachování původního chování. Další informace najdete v <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>tématu.

V rozhraní .NET Core `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` není přepínač podporován.

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
