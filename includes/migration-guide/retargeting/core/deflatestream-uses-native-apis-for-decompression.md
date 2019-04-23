---
ms.openlocfilehash: 897bb0b0650c633b87a792516c62566f491ec3fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981814"
---
### <a name="deflatestream-uses-native-apis-for-decompression"></a>DeflateStream využívá nativní rozhraní API pro dekompresi

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.7.2, provádění dekomprese v <code>T:System.IO.Compression.DeflateStream</code> došlo ke změně třídy používat nativní rozhraní API Windows ve výchozím nastavení. Obvykle to vede k zlepšení výkonu. Cílení na verzi rozhraní .NET Framework 4.7.2 nebo vyšší pomocí nativní implementaci všech aplikací .NET. Tato změna může vést k určité rozdíly v chování, mezi které patří:<ul><li>Zprávy o výjimkách, může být jiný. Typ výjimky vyvolané, ale zůstává stejná.</li><li>Některých speciálních situacích, například nemá dostatek paměti k dokončení operace, mohou být zpracovány jinak.</li><li>Jsou známy rozdíly pro analýzu hlavičce gzip (Poznámka: pouze <code>GZipStream</code> nastavení pro dekompresi ovlivňuje):</li><li>Výjimky při analýze neplatné záhlaví mohou být vyvolány v různých časech.</li><li>Nativní implementaci vynutí, že nebylo vyhrazeno hodnoty některých příznaků v hlavičce gzip (to znamená [FLG](http://www.zlib.org/rfc-gzip.html#header-trailer)) jsou nastavené podle specifikace, což může způsobit, že ji vyvolá výjimku, kde již dříve byly ignorovány neplatné hodnoty.</li></ul>|
|Doporučení|Pokud dekomprese pomocí nativních rozhraní API má negativně ovlivněn chování vaší aplikace, můžete se rozhodnout tuto funkci tak, že přidáte <code>Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression</code> přepněte <code>runtime</code> část souboru app.config a nastavíte ho na <code>true</code>:<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot; ?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.2|
|Type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.IO.Compression.DeflateStream?displayProperty=nameWithType></li><li><xref:System.IO.Compression.GZipStream?displayProperty=nameWithType></li></ul>|
