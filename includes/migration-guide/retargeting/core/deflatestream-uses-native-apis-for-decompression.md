---
ms.openlocfilehash: 7e42a294b151d07a6fdc61308cdf92df7a31a1d6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614485"
---
### <a name="deflatestream-uses-native-apis-for-decompression"></a>DeflateStream používá nativní rozhraní API pro dekompresi

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4.7.2 se implementace dekomprese ve `T:System.IO.Compression.DeflateStream` třídě změnila tak, aby ve výchozím nastavení používala nativní rozhraní API systému Windows. Obvykle to vede k výraznému zlepšení výkonu. Všechny aplikace .NET cílené na .NET Framework verze 4.7.2 nebo vyšší používají nativní implementaci. Tato změna může mít za následek určité rozdíly v chování, mezi které patří:

- Zprávy výjimek se mohou lišit. Typ vyvolané výjimky však zůstává stejný.
- Některé zvláštní situace, jako je například nedostatek paměti k dokončení operace, mohou být zpracovány jinak.
- Existují známé rozdíly pro analýzu hlavičky gzip (Poznámka: `GZipStream` je ovlivněna pouze sada pro dekompresi):
- Výjimky při analýze neplatných hlaviček mohou být vyvolány v různých časech.
- Nativní implementace vynucuje, že hodnoty pro některé vyhrazené příznaky v hlavičce gzip (tj. [FLG](http://www.zlib.org/rfc-gzip.html#header-trailer)) jsou nastaveny podle specifikace, což může způsobit výjimku, pokud byly dříve neplatné hodnoty ignorovány.

#### <a name="suggestion"></a>Návrh

Pokud dekomprese s nativními rozhraními API negativně ovlivnila chování vaší aplikace, můžete tuto funkci odhlásit přidáním `Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression` přepínače do `runtime` části souboru app.config a nastavením na `true` :

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=true" />
  </runtime>
</configuration>
```

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.7.2       |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.IO.Compression.DeflateStream?displayProperty=nameWithType>
- <xref:System.IO.Compression.GZipStream?displayProperty=nameWithType>
