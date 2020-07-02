---
ms.openlocfilehash: 148312743dd274728b178951548889dc3a680528
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614468"
---
### <a name="change-in-path-separator-character-in-fullname-property-of-ziparchiveentry-objects"></a>Změna v znaku oddělovače cesty ve vlastnosti FullName objektů ZipArchiveEntry

#### <a name="details"></a>Podrobnosti

U aplikací, které cílí na .NET Framework 4.6.1 a novější verze, se znak oddělovače cesty změnil z zpětného lomítka (" \" ) na lomítko ("/") ve <xref:System.IO.Compression.ZipArchiveEntry.FullName> vlastnosti <xref:System.IO.Compression.ZipArchiveEntry> objektů vytvořených přetížením <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A> metody. Tato změna přináší implementaci rozhraní .NET do souladu s oddílem 4.4.17.1 [. Specifikace formátu souboru ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) a umožňuje. Archivy ZIP, které se mají dekomprimovat v systémech jiných než Windows<br />Dekomprimace souboru ZIP vytvořeného aplikací, která cílí na předchozí verzi .NET Framework v operačních systémech jiných než Windows, jako je například Macintosh, se nepodařilo zachovat adresářovou strukturu. Například v počítači Macintosh vytvoří sadu souborů, jejichž název souboru zřetězí cestu k adresáři, spolu se znakem zpětného lomítka ("") a názvem souboru. V důsledku toho není zachována adresářová struktura dekomprimovaných souborů.

#### <a name="suggestion"></a>Návrh

Dopad této změny na. Soubory ZIP, které jsou v operačním systému Windows dekomprimovány pomocí rozhraní API v <xref:System.IO?displayProperty=nameWithType> oboru názvů .NET Framework, by měly být minimální, protože tato rozhraní API můžou hladě zpracovávat lomítka ("/") nebo zpětné lomítko (" \" ) jako znak oddělovače cesty.<br />Pokud je tato změna nežádoucí, můžete ji odhlásit přidáním nastavení konfigurace do [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace. Následující příklad ukazuje jak `<runtime>` oddíl, tak přepínač pro `Switch.System.IO.Compression.ZipFile.UseBackslash` výslovný souhlas:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />
</runtime>
```

Kromě toho aplikace, které cílí na předchozí verze .NET Framework, ale běží v .NET Framework 4.6.1 a novějších verzích se můžou k tomuto chování vyjádřit přidáním nastavení konfigurace do [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace. Následující příklad ukazuje `<runtime>` oddíl i `Switch.System.IO.Compression.ZipFile.UseBackslash` přepínač pro výslovný souhlas.

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />
</runtime>
```

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.6.1       |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean)?displayProperty=nameWithType>
- <xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean,System.Text.Encoding)?displayProperty=nameWithType>
