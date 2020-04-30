---
ms.openlocfilehash: b3cc04d5675ea63a0a6b967e293da8a1bd79830d
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595676"
---
### <a name="uribuilder-properties-no-longer-prepend-leading-characters"></a>Vlastnosti objekt UriBuilder protokolu už neobsahují úvodní znaky.

<xref:System.UriBuilder.Fragment?displayProperty=nameWithType>již neprezentuje úvodní `#` znak a již <xref:System.UriBuilder.Query?displayProperty=nameWithType> předřadí úvodní `?` znak, pokud již existuje.

#### <a name="change-description"></a>Popis změny

<xref:System.UriBuilder.Fragment?displayProperty=nameWithType> V .NET Framework vlastnosti <xref:System.UriBuilder.Query?displayProperty=nameWithType> a vždy předřadí znak `#` nebo `?` (v uvedeném pořadí) na hodnotu, která je ukládána. Toto chování může mít za následek `#` více `?` nebo znaků v uložené hodnotě, pokud řetězec již obsahuje jeden z těchto úvodních znaků. Například hodnota <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> může být `##main`.

Počínaje rozhraním .NET Core 1,0 tyto vlastnosti již neprezentují `#` znaky `?` ani pro uloženou hodnotu, je-li již na začátku řetězce přítomen některý z nich.

#### <a name="version-introduced"></a>Představená verze

1.0

#### <a name="recommended-action"></a>Doporučená akce

Při nastavování hodnot vlastností už nemusíte explicitně odebírat žádné z těchto počátečních znaků. To je užitečné hlavně v případě, že přidáváte hodnoty, protože už nemusíte odebírat úvodní `#` nebo `?` pokaždé, když se připojujete.

Například následující fragment kódu ukazuje rozdíl chování mezi .NET Framework a .NET Core.

```csharp
var builder = new UriBuilder();
builder.Query = "one=1";
builder.Query += "&two=2";
builder.Query += "&three=3";
builder.Query += "&four=4";

Console.WriteLine(builder.Query);
```

- Ve .NET Framework je `????one=1&two=2&three=3&four=4`výstup.
- Ve výstupu .NET Core je `?one=1&two=2&three=3&four=4`výstup.

#### <a name="category"></a>Kategorie

Knihovny Core .NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.UriBuilder.Fragment?displayProperty=fullName>
- <xref:System.UriBuilder.Query?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.UriBuilder.Fragment`
- `T:System.UriBuilder.Query`

-->
