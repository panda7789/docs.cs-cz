---
ms.openlocfilehash: 3f0e8fb4d0d727b40cff5de7cfdc7529bf32dac4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937057"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a>Přepínač kompatibility DoNotLoadLatestRichEditControl se nepodporuje.

Přepínač `Switch.System.Windows.Forms.UseLegacyImages` kompatibility, který byl představen v .NET Framework 4.7.1, není podporován v model Windows Forms .net Core 3,0.

#### <a name="change-description"></a>Popis změny

V .NET Framework 4.6.2 a předchozích verzích může <xref:System.Windows.Forms.RichTextBox> ovládací prvek vytvořit instanci systému Win32 RichEdit Control v 3.0 a pro aplikace, které cílí na .NET Framework 4.7.1, by měl <xref:System.Windows.Forms.RichTextBox> ovládací prvek vytvořit instanci RichEdit v 4.1 (v *Msftedit. dll*). Byl `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` zaveden přepínač kompatibility, který umožňuje aplikacím, které cílí na .NET Framework 4.7.1 a novějších verzí, odhlásit nový ovládací prvek RichEdit v 4.1 a místo toho použít starý ovládací prvek RichEdit v3.

V rozhraní .NET Core není `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` přepínač podporován. Jsou podporovány pouze nové verze <xref:System.Windows.Forms.RichTextBox> tohoto ovládacího prvku.

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
