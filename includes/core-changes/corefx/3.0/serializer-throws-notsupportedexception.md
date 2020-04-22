---
ms.openlocfilehash: cc3251e3b31143bd95793b407e50cf76e0e30142
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021644"
---
### <a name="json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception"></a>Typ výjimky serializátoru Json byl změněn z `JsonException` na`NotSupportedException`

V .NET Core 3.0 Náhled 6 až 8 <xref:System.Text.Json.JsonException> serializátor by vyvolat, když došlo k nepodporované odvozené kolekce typu. Počínaje .NET Core 3.0 Náhled 9 serializátor vyvolá <xref:System.NotSupportedException> místo.

#### <a name="change-description"></a>Popis změny

V .NET Core 3.0 Náhled 6 až Náhled <xref:System.Text.Json.JsonException> 8 serializátor by vyvolat, když došlo k nepodporované odvozené kolekce typu. Nepodporovaný *typ odvozené kolekce* je libovolný typ kolekce, který nelze přiřadit jednomu z následujících typů:

- <xref:System.Collections.IList>
- <xref:System.Collections.Generic.ICollection%601>
- <xref:System.Collections.Generic.Stack%601>
- <xref:System.Collections.Generic.Queue%601>
- <xref:System.Collections.IDictionary>
- [Řetězec IDictionary,t\<>](xref:System.Collections.Generic.IDictionary%602)

Počínaje .NET Core 3.0 Náhled 9 serializátor vyvolá <xref:System.NotSupportedException> Při výskytu nepodporovaný typ kolekce. Nový typ výjimky lépe odráží, proč operace deserializace selhává.

#### <a name="version-introduced"></a>Zavedená verze

3.0 Náhled 9

#### <a name="recommended-action"></a>Doporučená akce

Pokud jste chytání <xref:System.Text.Json.JsonException> při deserializaci, možná budete <xref:System.NotSupportedException>chtít, aby zvážila také chytání .

#### <a name="category"></a>Kategorie

Základní knihovny .NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
