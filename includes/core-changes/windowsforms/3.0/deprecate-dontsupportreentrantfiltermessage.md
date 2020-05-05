---
ms.openlocfilehash: 3272dc562981269b868df4ca9d3a5806918aba5f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937070"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a>Přepínač kompatibility DontSupportReentrantFilterMessage se nepodporuje.

Přepínač `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` kompatibility, který byl představen v .NET Framework 4.6.1, není podporován v model Windows Forms .net Core 3,0.

#### <a name="change-description"></a>Popis změny

`Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` Počínaje .NET Framework 4.6.1, přepínač kompatibility řeší možné <xref:System.IndexOutOfRangeException> výjimky při volání <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> zprávy s vlastní <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementací. Další informace naleznete v tématu [zmírňující rizika: Custom IMessageFilter. PreFilterMessage Implements](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).

V rozhraní .NET Core není `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` přepínač podporován.

#### <a name="version-introduced"></a>Představená verze

3,0 Preview 9

#### <a name="recommended-action"></a>Doporučená akce

Odeberte přepínač. Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
