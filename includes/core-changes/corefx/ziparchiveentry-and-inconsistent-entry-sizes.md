---
ms.openlocfilehash: 748e7f484227b6a60a2309bde185079b30fe19de
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117170"
---
### <a name="ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes"></a>ZipArchiveEntry už nezpracovává archivy s nekonzistentními velikostmi záznamů.

Archivy zip uvádějí komprimovanou velikost i nekomprimovanou velikost v centrálním adresáři a v místní hlavičce.  Samotná data samotného záznamu také označují jeho velikost.  V .NET Core 2,2 a dřívějších verzích se tyto hodnoty nikdy nekontrolovaly konzistence. Počínaje .NET Core 3,0 jsou teď.

#### <a name="change-description"></a>Změnit popis

V .NET Core 2,2 a starších verzích se <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> aplikace zdaří i v případě, že místní hlavička odsouhlasí s centrálním hlavičkou souboru ZIP. Data se dekomprimuje, dokud se nedosáhne konce zkomprimovaného datového proudu, a to i v případě, že jeho délka přesáhne velikost nekomprimovaného souboru, která je uvedená v centrálním adresáři/místní hlavičce.

Počínaje rozhraním .NET Core 3,0 <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> metoda kontroluje, zda se místní hlavička a centrální hlavička dohodnou na komprimovaných a nekomprimovaných velikostech položky.  Pokud ne, metoda vyvolá <xref:System.IO.InvalidDataException> výjimku, pokud místní hlavička nebo seznam popisovačů dat archivu, které nesouhlasí s centrálním adresářem souboru ZIP. Při čtení položky se dekomprimovaná data zkrátí na nekomprimovaný soubor, který je uveden v hlavičce.

Tato změna byla provedena, aby se zajistilo, že <xref:System.IO.Compression.ZipArchiveEntry> správně představuje velikost svých dat a že je čteno pouze množství dat.

#### <a name="version-introduced"></a>Představená verze

3.0

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

