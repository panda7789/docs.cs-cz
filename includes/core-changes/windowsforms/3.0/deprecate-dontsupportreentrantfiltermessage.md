---
ms.openlocfilehash: cb72e1b92172b8989ce99b47181c13561a7ccd76
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644003"
---
### <a name="switchsystemwindowsformsdontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a>Přepínač kompatibility. System. Windows. Forms. DontSupportReentrantFilterMessage není podporovaný.

V model Windows Forms .NET Core 3,0 není podporován přepínač kompatibility `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`, který byl představen v .NET Framework 4.6.1.

#### <a name="change-description"></a>Změnit popis

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
