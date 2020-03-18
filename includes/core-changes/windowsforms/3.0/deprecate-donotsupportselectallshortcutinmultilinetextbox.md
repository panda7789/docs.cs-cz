---
ms.openlocfilehash: 9631e64bb403a3fe7b1b91e8ac592b57ce8068d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937081"
---
### <a name="donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported"></a>Přepínač kompatibility DoNotSupportSelectAllShortcutInMultilineTextBox není podporován

Přepínač `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` kompatibility, který byl zaveden v rozhraní .NET Framework 4.6.1, není ve formulářích Windows v rozhraní .NET Core 3.0 podporován.

#### <a name="change-description"></a>Popis změny

Počínaje rozhraním .NET Framework 4.6.1 vyberte klávesovou zkratku <kbd>Ctrl</kbd> + <kbd>A</kbd> v ovládacím prvku vybraný <xref:System.Windows.Forms.TextBox> veškerý text. V rozhraní .NET Framework 4.6 a předchozích verzích se výběru klávesové zkratky <kbd>Ctrl</kbd> + <kbd>A</kbd> nepodařilo `true`vybrat veškerý text, pokud byly obě [vlastnosti Textbox.ShortcutsEnabled](xref:System.Windows.Forms.TextBoxBase.ShortcutsEnabled) a <xref:System.Windows.Forms.TextBox.Multiline?displayProperty=nameWithType> vlastnosti nastaveny na . Přepínač `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` kompatibility byl zaveden v rozhraní .NET Framework 4.6.1 zachovat původní chování. Další informace naleznete zde <xref:System.Windows.Forms.TextBox.ProcessCmdKey%2A?displayProperty=nameWithType>.

V rozhraní .NET `Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox` Core není přepínač podporován.

#### <a name="version-introduced"></a>Zavedená verze

3.0 Náhled 9

#### <a name="recommended-action"></a>Doporučená akce

Odstraňte spínač. Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- Žádný

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
