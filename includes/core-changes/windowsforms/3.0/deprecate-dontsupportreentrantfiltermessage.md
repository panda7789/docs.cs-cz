---
ms.openlocfilehash: 95aa243a5790d4201c7871e617dbe4ccafb7c1a1
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556158"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a>Přepínač kompatibility DontSupportReentrantFilterMessage se nepodporuje.

`Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`Přepínač kompatibility, který byl představen v .NET Framework 4.6.1, není podporován v model Windows Forms v rozhraní .NET Core a .net 5,0 a novějším.

#### <a name="change-description"></a>Popis změny

Počínaje .NET Framework 4.6.1, `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` přepínač kompatibility řeší možné <xref:System.IndexOutOfRangeException> výjimky při <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> volání zprávy s vlastní <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementací. Další informace naleznete v tématu [zmírňující rizika: Custom IMessageFilter. PreFilterMessage Implements](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).

V rozhraní .NET Core a .NET 5,0 a novějším není `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` přepínač podporován.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Odeberte přepínač. Přepínač není podporován a nejsou k dispozici žádné alternativní funkce.

#### <a name="category"></a>Kategorie

Windows Forms

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
