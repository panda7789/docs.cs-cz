---
ms.openlocfilehash: cb72e1b92172b8989ce99b47181c13561a7ccd76
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181867"
---
### <a name="switchsystemwindowsformsdontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a>Přepínač kompatibility. System. Windows. Forms. DontSupportReentrantFilterMessage není podporovaný.

Přepínač `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` kompatibility, který byl představen v .NET Framework 4.6.1, není podporován v model Windows Forms .NET Core 3,0.

#### <a name="change-description"></a>Změnit popis

Počínaje .NET Framework 4.6.1 `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` , přepínač kompatibility řeší možné <xref:System.IndexOutOfRangeException> výjimky při <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> volání zprávy s vlastní <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementací. Další informace najdete v tématu [zmírnění rizika: Vlastní implementace](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)IMessageFilter. PreFilterMessage.

V rozhraní .NET Core `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` není přepínač podporován.

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
