---
ms.openlocfilehash: 39d1b2dba8077bf9bf998775f8967d455f36b549
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119280"
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
