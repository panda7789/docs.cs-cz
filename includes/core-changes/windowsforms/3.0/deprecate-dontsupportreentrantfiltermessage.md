---
ms.openlocfilehash: 3272dc562981269b868df4ca9d3a5806918aba5f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937070"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a>Přepínač kompatibility DontSupportReentrantFilterMessage není podporován.

Přepínač `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` kompatibility, který byl zaveden v rozhraní .NET Framework 4.6.1, není ve formulářích Windows v rozhraní .NET Core 3.0 podporován.

#### <a name="change-description"></a>Popis změny

Počínaje rozhraním .NET Framework 4.6.1, `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` přepínač <xref:System.IndexOutOfRangeException> kompatibility <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> řeší možné výjimky <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> při volání zprávy s vlastní implementací. Další informace naleznete [v tématu Mitigation: Custom IMessageFilter.PreFilterMessageMessage Implementations](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).

V rozhraní .NET `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` Core není přepínač podporován.

#### <a name="version-introduced"></a>Zavedená verze

3.0 Náhled 9

#### <a name="recommended-action"></a>Doporučená akce

Odstraňte spínač. Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
