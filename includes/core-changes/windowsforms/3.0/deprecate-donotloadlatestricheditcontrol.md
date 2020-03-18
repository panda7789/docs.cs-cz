---
ms.openlocfilehash: 3f0e8fb4d0d727b40cff5de7cfdc7529bf32dac4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937057"
---
### <a name="donotloadlatestricheditcontrol-compatibility-switch-not-supported"></a>Přepínač kompatibility DoNotLoadLatestRichEditControl není podporován.

Přepínač `Switch.System.Windows.Forms.UseLegacyImages` kompatibility, který byl zaveden v rozhraní .NET Framework 4.7.1, není ve formulářích Windows v rozhraní .NET Core 3.0 podporován.

#### <a name="change-description"></a>Popis změny

V rozhraní .NET Framework 4.6.2 a <xref:System.Windows.Forms.RichTextBox> předchozí verze ovládací prvek by vytvořit instanci Ovládací prvek Win32 RichEdit v3.0 <xref:System.Windows.Forms.RichTextBox> a pro aplikace, které se zaměřují na rozhraní .NET Framework 4.7.1, by ovládací prvek vytvořit instanci RichEdit v4.1 (v *msftedit.dll*). Přepínač `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` kompatibility byl zaveden, aby aplikace, které cílí na rozhraní .NET Framework 4.7.1 a novější verze, odhlásily nový ovládací prvek RichEdit v4.1 a místo toho použily starý ovládací prvek RichEdit v3.

V rozhraní .NET `Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl` Core není přepínač podporován. Podporovány jsou pouze <xref:System.Windows.Forms.RichTextBox> nové verze ovládacího prvku.

#### <a name="version-introduced"></a>Zavedená verze

3.0 Náhled 9

#### <a name="recommended-action"></a>Doporučená akce

Odstraňte spínač. Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Windows.Forms.RichTextBox?displayProperty=nameWithType>

<!-- 

### Affected APIs

-  `T:System.Windows.Forms.RichTextBox` 

-->
