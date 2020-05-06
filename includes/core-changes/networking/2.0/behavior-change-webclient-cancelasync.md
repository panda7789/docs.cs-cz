---
ms.openlocfilehash: 80d4bbbfe52ab9685d7ca54f21b80d4b1773da22
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859636"
---
### <a name="webclientcancelasync-doesnt-always-cancel-immediately"></a>WebClient. CancelAsync nevždycky zruší hned

Počínaje rozhraním .NET Core 2,0, <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> volání neruší žádost okamžitě, pokud se odpověď začala načíst.

#### <a name="change-description"></a>Popis změny

Dříve volání <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> zrušilo požadavek okamžitě. Počínaje rozhraním .NET Core 2,0 volání <xref:System.Net.WebClient.CancelAsync?displayProperty=nameWithType> zruší žádost okamžitě pouze v případě, že se odpověď nezačala načítat. Pokud se odpověď začala načítat, žádost se zruší až po načtení kompletní odpovědi.

Tato změna byla implementována, <xref:System.Net.WebClient> protože rozhraní API je namísto toho zastaralé <xref:System.Net.Http.HttpClient>.

#### <a name="version-introduced"></a>Představená verze

2.0

#### <a name="recommended-action"></a>Doporučená akce

Místo toho <xref:System.Net.Http.HttpClient?displayProperty=fullName> použijte třídu <xref:System.Net.WebClient?displayProperty=fullName>, která je zastaralá.

#### <a name="category"></a>Kategorie

Sítě

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Net.WebClient.CancelAsync?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Net.WebClient.CancelAsync`

-->
