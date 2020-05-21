---
ms.openlocfilehash: cb8c0532bb2bcfbcd619cd382f3d236b431c3480
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721723"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a>Přepínač kompatibility DoNotLoadLatestRichEditControl se nepodporuje.

`Switch.System.Windows.Forms.UseLegacyImages`Přepínač kompatibility, který byl představen v .NET Framework 4.7.1, není podporován v model Windows Forms .NET Core 3,0.

#### <a name="change-description"></a>Popis změny

V .NET Framework 4.6.2 a předchozích verzích může <xref:System.Windows.Forms.RichTextBox> ovládací prvek vytvořit instanci systému Win32 RichEdit Control v 3.0 a pro aplikace, které cílí na .NET Framework 4.7.1, <xref:System.Windows.Forms.RichTextBox> by měl ovládací prvek vytvořit instanci RichEdit v 4.1 (v *Msftedit. dll*). `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl`Byl zaveden přepínač kompatibility, který umožňuje aplikacím, které cílí na .NET Framework 4.7.1 a novějších verzí, odhlásit nový ovládací prvek RichEdit v 4.1 a místo toho použít starý ovládací prvek RichEdit v3.

V rozhraní .NET Core není `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` přepínač podporován. Jsou podporovány pouze nové verze tohoto <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.

#### <a name="version-introduced"></a>Představená verze

3,0 Preview 9

#### <a name="recommended-action"></a>Doporučená akce

Odeberte přepínač. Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

#### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
