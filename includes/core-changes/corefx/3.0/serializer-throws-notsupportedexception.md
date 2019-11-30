---
ms.openlocfilehash: e6e10b2ec451c07bf397cbdcac51ef57c29dab47
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568088"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a>Typ výjimky serializátoru JSON se změnil z `JsonException` na `NotSupportedException`

V .NET Core 3,0 Preview 6 až 8 by serializátor vyvolal <xref:System.Text.Json.JsonException>, když narazil na nepodporovaný odvozený typ kolekce. Počínaje rozhraním .NET Core 3,0 Preview 9 vyvolá serializátor místo toho <xref:System.NotSupportedException>.

#### <a name="change-description"></a>Změnit popis

V .NET Core 3,0 Preview 6 až Preview 8 by serializátor vyvolal <xref:System.Text.Json.JsonException>, když narazil na nepodporovaný odvozený typ kolekce. *Nepodporovaný typ odvozené kolekce* je libovolný typ kolekce, který není možné přiřadit k jednomu z následujících typů:

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [Řetězec IDictionary\<, T >](xref:System.Collections.Generic.IDictionary%602)

Počínaje rozhraním .NET Core 3,0 Preview 9 vyvolá serializátor při zjištění nepodporovaného typu kolekce <xref:System.NotSupportedException>. Nový typ výjimky lépe odráží důvod selhání operace deserializace.

#### <a name="version-introduced"></a>Představená verze

3,0 Preview 9

#### <a name="recommended-action"></a>Doporučená akce

Pokud při deserializaci zachytíte <xref:System.Text.Json.JsonException>, možná budete chtít zvážit také zachytávání <xref:System.NotSupportedException>.

#### <a name="category"></a>Kategorie

CoreFx

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
