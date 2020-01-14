---
ms.openlocfilehash: 3272dc562981269b868df4ca9d3a5806918aba5f
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937070"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a>Přepínač kompatibility DontSupportReentrantFilterMessage se nepodporuje.

V model Windows Forms .NET Core 3,0 není podporován přepínač kompatibility `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`, který byl představen v .NET Framework 4.6.1.

#### <a name="change-description"></a>Popis změny

Počínaje verzí .NET Framework 4.6.1 `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` přepínač kompatibility řeší možné <xref:System.IndexOutOfRangeException> výjimky při volání <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> zprávy s vlastní <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType>ou implementací. Další informace naleznete v tématu [zmírňující rizika: Custom IMessageFilter. PreFilterMessage Implements](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).

V rozhraní .NET Core není přepínač `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` podporován.

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
