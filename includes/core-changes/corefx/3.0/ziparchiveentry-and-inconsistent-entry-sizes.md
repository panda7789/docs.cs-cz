---
ms.openlocfilehash: 9520f8c6b6671917f5694bc602293a00e2dab82d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568074"
---
### <a name="ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes"></a>ZipArchiveEntry již zpracovává archivy s nekonzistentními velikostmi položek

Zip archivy seznam jak komprimované velikosti a nekomprimované velikosti v centrálním adresáři a místní záhlaví.  Vstupní data sama také označuje jeho velikost.  V rozhraní .NET Core 2.2 a starších verzích nebyly tyto hodnoty nikdy kontrolovány na konzistenci. Počínaje rozhraním .NET Core 3.0 nyní jsou.

#### <a name="change-description"></a>Popis změny

V rozhraní .NET Core 2.2 <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> a starších verzích se daří i v případě, že místní záhlaví nesouhlasí s centrální záhlaví souboru zip. Data jsou dekomprimována až do dosažení konce komprimovaného datového proudu, a to i v případě, že jejich délka přesahuje velikost nekomprimovaného souboru uvedenou v centrálním adresáři nebo místní hlavičce.

Počínaje rozhraním .NET Core <xref:System.IO.Compression.ZipArchiveEntry.Open?displayProperty=nameWithType> 3.0 metoda kontroluje, zda se místní hlavička a centrální hlavička dohodnou na komprimovaných a nekomprimovaných velikostech položky.  Pokud tomu tak není, metoda <xref:System.IO.InvalidDataException> vyvolá pokud je místní záhlaví nebo velikosti seznamu popisovačů dat, které nesouhlasí s centrálním adresářem souboru zip. Při čtení položky jsou dekomprimovaná data zkrácena na nekomprimovanou velikost souboru uvedenou v záhlaví.

Tato změna byla provedena, <xref:System.IO.Compression.ZipArchiveEntry> aby bylo zajištěno, že správně představuje velikost jeho dat a že je přečteno pouze toto množství dat.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Přebalit všechny zip archiv, který vykazuje tyto problémy.

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
