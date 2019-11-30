---
ms.openlocfilehash: 9520f8c6b6671917f5694bc602293a00e2dab82d
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568074"
---
### <a name="ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes"></a>ZipArchiveEntry už nezpracovává archivy s nekonzistentními velikostmi záznamů.

Archivy zip uvádějí komprimovanou velikost i nekomprimovanou velikost v centrálním adresáři a v místní hlavičce.  Samotná data samotného záznamu také označují jeho velikost.  V .NET Core 2,2 a dřívějších verzích se tyto hodnoty nikdy nekontrolovaly konzistence. Počínaje .NET Core 3,0 jsou teď.

#### <a name="change-description"></a>Změnit popis

V .NET Core 2,2 a starších verzích <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> úspěšná, i když místní hlavička odsouhlasí s centrálním hlavičkou souboru ZIP. Data se dekomprimuje, dokud se nedosáhne konce zkomprimovaného datového proudu, a to i v případě, že jeho délka přesáhne velikost nekomprimovaného souboru, která je uvedená v centrálním adresáři/místní hlavičce.

Počínaje rozhraním .NET Core 3,0 metoda <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> kontroluje, zda se místní hlavička a centrální hlavička dohodnou na komprimovaných a nekomprimovaných velikostech položky.  Pokud tomu tak není, vyvolá metoda <xref:System.IO.InvalidDataException>, pokud místní záhlaví a/nebo seznam popisovačů dat archivu mají velikost, která nesouhlasí s centrálním adresářem souboru ZIP. Při čtení položky se dekomprimovaná data zkrátí na nekomprimovaný soubor, který je uveden v hlavičce.

Tato změna byla provedena, aby <xref:System.IO.Compression.ZipArchiveEntry> správně představovala velikost svých dat a bylo čteno pouze množství dat.

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="recommended-action"></a>Doporučená akce

Znovu zabalit libovolný archiv zip, který tyto problémy vykazuje.

#### <a name="category"></a>Kategorie

CoreFx

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.ExtractToDirectory%2A?displayProperty=nameWithType>

<!--

### Affected APIs

`M:System.IO.Compression.ZipArchiveEntry.Open`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToDirectory%2A`
`Overload:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A`
`Overload:System.IO.Compression.ZipFile.ExtractToDirectory%2A`

-->
