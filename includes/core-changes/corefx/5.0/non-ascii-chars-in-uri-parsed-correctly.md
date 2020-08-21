---
ms.openlocfilehash: faf9459ab9002e6149560e2a3452265fa246bf6b
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720184"
---
### <a name="uri-paths-with-non-ascii-characters-parse-correctly-on-unix"></a>Cesty URI bez znaků, které nejsou ASCII, se v systému UNIX analyzují správně

Ve třídě byla opravena chyba <xref:System.Uri?displayProperty=fullName> tak, že absolutní cesty URI, které obsahují znaky jiné než ASCII, se teď na platformách UNIX analyzují správně.

#### <a name="change-description"></a>Popis změny

V předchozích verzích rozhraní .NET se absolutní cesty URI, které obsahují znaky jiné než ASCII, nesprávně analyzují na platformách UNIX a segmenty cesty jsou duplicitní. (Absolutní cesty jsou ty, které začínají znakem "/".) Problém s analýzou byl vyřešen pro .NET 5,0. Pokud přejdete z předchozí verze rozhraní .NET na .NET 5,0 nebo novější, získáte různé hodnoty vytvářené pomocí <xref:System.Uri.AbsoluteUri?displayProperty=nameWithType> , <xref:System.Uri.ToString?displayProperty=nameWithType> a dalších <xref:System.Uri> členů.

Při spuštění v systému UNIX zvažte výstup následujícího kódu.

```csharp
var myUri = new Uri("/üri");

Console.WriteLine($"AbsoluteUri: {myUri.AbsoluteUri}");
Console.WriteLine($"ToString: {myUri.ToString()}");
```

Výstup na předchozí verzi rozhraní .NET:

```text
AbsoluteUri: /%C3%BCri/%C3%BCri
ToString: /üri/üri
```

Výstup v rozhraní .NET 5,0 nebo novější verzi:

```text
AbsoluteUri: /%C3%BCri
ToString: /üri
```

#### <a name="version-introduced"></a>Představená verze

5,0

#### <a name="recommended-action"></a>Doporučená akce

Pokud máte kód, který očekává a účty pro duplicitní segmenty cesty, můžete tento kód odebrat.

#### <a name="category"></a>Kategorie

Knihovny Core .NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Uri`

-->
