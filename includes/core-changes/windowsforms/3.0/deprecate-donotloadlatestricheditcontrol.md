---
ms.openlocfilehash: 265fc5bea97bf85bcb9cc8111f915e14297d9957
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643982"
---
### <a name="switchsystemwindowsformsdonotloadlatestricheditcontrol-compatibility-switch-not-supported"></a>Přepínač kompatibility. System. Windows. Forms. DoNotLoadLatestRichEditControl není podporovaný.

V model Windows Forms .NET Core 3,0 není podporován přepínač kompatibility `Switch.System.Windows.Forms.UseLegacyImages`, který byl představen v .NET Framework 4.7.1.

#### <a name="change-description"></a>Změnit popis

V .NET Framework 4.6.2 a předchozích verzích by ovládací prvek <xref:System.Windows.Forms.RichTextBox> vytvořil instanci Win32 RichEdit Control v 3.0 a pro aplikace, které cílí .NET Framework 4.7.1, by měl ovládací prvek <xref:System.Windows.Forms.RichTextBox> vytvořit instanci RichEdit v 4.1 (v *Msftedit. dll*). Byl zaveden přepínač kompatibility `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl`, který umožňuje aplikacím, které cílí na .NET Framework 4.7.1 a novějších verzích, odhlásit nový ovládací prvek RichEdit v 4.1 a místo toho použít starý ovládací prvek RichEdit v3.

V rozhraní .NET Core není přepínač `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` podporován. Jsou podporovány pouze nové verze <xref:System.Windows.Forms.RichTextBox>ho ovládacího prvku.

#### <a name="version-introduced"></a>Představená verze

3,0 Preview 9

#### <a name="recommended-action"></a>Doporučená akce

Odeberte přepínač. Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
