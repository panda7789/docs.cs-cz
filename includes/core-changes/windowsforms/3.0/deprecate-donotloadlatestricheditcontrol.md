---
ms.openlocfilehash: e10b5168d59edd56ff549a3a1e3a09d023fe5e28
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556154"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a>Přepínač kompatibility DoNotLoadLatestRichEditControl se nepodporuje.

`Switch.System.Windows.Forms.UseLegacyImages`Přepínač kompatibility, který byl představen v .NET Framework 4.7.1, není podporován v model Windows Forms v rozhraní .NET Core nebo .net 5,0 a novějším.

#### <a name="change-description"></a>Popis změny

V .NET Framework 4.6.2 a předchozích verzích <xref:System.Windows.Forms.RichTextBox> řídí ovládací prvek Win32 RichEdit Control v 3.0 a pro aplikace, které cílí na .NET Framework 4.7.1, <xref:System.Windows.Forms.RichTextBox> ovládací prvek vytváří instance RichEdit v 4.1 (v *msftedit.dll*). `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl`Byl zaveden přepínač kompatibility, který umožňuje aplikacím, které cílí na .NET Framework 4.7.1 a novějších verzí, odhlásit nový ovládací prvek RichEdit v 4.1 a místo toho použít starý ovládací prvek RichEdit v3.

V rozhraní .NET Core a .NET 5,0 a novějších verzích není `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` přepínač podporován. Jsou podporovány pouze nové verze tohoto <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.

#### <a name="version-introduced"></a>Představená verze

3.0

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
