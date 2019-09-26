---
ms.openlocfilehash: a35439efce25db94e70420fc6aeaf04816525758
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71263326"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a>Typ výjimky serializátoru JSON se `JsonException` změnil z na.`NotSupportedException`

V .NET Core 3,0 Preview 6 až 8, serializátor vyvolá výjimku <xref:System.Text.Json.JsonException> , když zjistila nepodporovaný odvozený typ kolekce. Počínaje rozhraním .NET Core 3,0 Preview 9 vyvolá <xref:System.NotSupportedException> serializátor místo toho.

#### <a name="change-description"></a>Změnit popis

V .NET Core 3,0 Preview 6 až Preview 8, serializátor vyvolá výjimku <xref:System.Text.Json.JsonException> , když narazil na nepodporovaný odvozený typ kolekce. *Nepodporovaný typ odvozené kolekce* je libovolný typ kolekce, který není možné přiřadit k jednomu z následujících typů:

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>`
- <xref:System.Collections.IDictionary>
- [Řetězec\<IDictionary, T >](xref:System.Collections.Generic.IDictionary%602)

Počínaje rozhraním .NET Core 3,0 Preview 9 vyvolá <xref:System.NotSupportedException> serializátor při zjištění nepodporovaného typu kolekce. Nový typ výjimky lépe odráží důvod selhání operace deserializace.

#### <a name="version-introduced"></a>Představená verze

3,0 Preview 9

#### <a name="recommended-action"></a>Doporučená akce

Pokud při deserializaci <xref:System.Text.Json.JsonException> zachytíte, možná budete chtít zvážit také jejich <xref:System.NotSupportedException>zachycení.

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
