---
ms.openlocfilehash: 265fc5bea97bf85bcb9cc8111f915e14297d9957
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181794"
---
### <a name="switchsystemwindowsformsdonotloadlatestricheditcontrol-compatibility-switch-not-supported"></a>Přepínač kompatibility. System. Windows. Forms. DoNotLoadLatestRichEditControl není podporovaný.

Přepínač `Switch.System.Windows.Forms.UseLegacyImages` kompatibility, který byl představen v .NET Framework 4.7.1, není podporován v model Windows Forms .NET Core 3,0.

#### <a name="change-description"></a>Změnit popis

V .NET Framework 4.6.2 a předchozích verzích <xref:System.Windows.Forms.RichTextBox> by ovládací prvek vytvořil instanci Win32 RichEdit Control v 3.0 a pro aplikace, které cílí na .NET Framework 4.7.1 <xref:System.Windows.Forms.RichTextBox> , by měl ovládací prvek vytvořit instanci RichEdit v 4.1 (v  *Msftedit. dll*). Byl zaveden přepínač kompatibility, který umožňuje aplikacím, které cílí na .NET Framework 4.7.1 a novějších verzí, odhlásit nový ovládací prvek RichEdit v 4.1 a místo toho použít starý ovládací prvek RichEdit v3. `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl`

V rozhraní .NET Core `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` není přepínač podporován. Jsou podporovány pouze nové verze <xref:System.Windows.Forms.RichTextBox> tohoto ovládacího prvku.

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
