---
ms.openlocfilehash: 0246f325a6274082b7fb0d5590cec7c80687ae85
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720182"
---
### <a name="uri-recognition-of-unc-paths-on-unix"></a>Rozpoznání identifikátoru URI cest UNC v systému UNIX

<xref:System.Uri>Třída teď rozpoznává řetězce, které začínají dvěma lomítky ( `//` ) jako cesty UNC (Universal Naming Convention) v operačních systémech UNIX. Tato změna způsobí, že chování pro tyto řetězce je konzistentní napříč všemi platformami.

#### <a name="change-description"></a>Popis změny

V předchozích verzích rozhraní .NET <xref:System.Uri> Třída rozpoznává řetězce, které začínají se dvěma lomítky, například `//contoso` jako absolutní cesty k souborům v operačních systémech UNIX. Ve Windows se ale tyto řetězce rozpoznávají jako cesty UNC.

Počínaje rozhraním .NET 5,0 <xref:System.Uri> Třída rozpoznává řetězce, které začínají se dvěma lomítky jako cesty UNC na všech platformách, včetně systému UNIX. Kromě toho se vlastnosti chovají podle sémantiky UNC:

- <xref:System.Uri.IsUnc?displayProperty=nameWithType> Vrátí `true` .
- Zpětná lomítka v cestě jsou nahrazena lomítky. Například `//first\second` se bude jednat o `//first/second` .
- <xref:System.Uri.LocalPath?displayProperty=nameWithType> Nejedná se o procentuální kódování znaků. Například `//first/\uFFF0` není převeden na *not* `//first/%EF%BF%B0` .

#### <a name="version-introduced"></a>Představená verze

5,0

#### <a name="recommended-action"></a>Doporučená akce

V rámci vývojáře není vyžadována žádná akce.

#### <a name="category"></a>Kategorie

Knihovny Core .NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Uri`

-->
