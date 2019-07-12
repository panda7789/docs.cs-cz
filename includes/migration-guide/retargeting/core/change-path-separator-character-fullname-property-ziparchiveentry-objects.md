---
ms.openlocfilehash: a786ce0908552547f996d0c299db2a9e9e14a757
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804312"
---
### <a name="change-in-path-separator-character-in-fullname-property-of-ziparchiveentry-objects"></a>Změna v znakem oddělovače cesty ve vlastnosti FullName z položky ZipArchiveEntry objektů

|   |   |
|---|---|
|Podrobnosti|Pro aplikace, které jsou cíleny na rozhraní .NET Framework 4.6.1 a novější verze, oddělovač cesty byl změněn z zpětné lomítko (&quot;\&quot;) na dopředné lomítko (&quot;/&quot;) v <xref:System.IO.Compression.ZipArchiveEntry.FullName> vlastnost <xref:System.IO.Compression.ZipArchiveEntry> objekty vytvořené pomocí přetížení <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A> metody. Tato změna přináší implementace .NET do souladu s část 4.4.17.1 [. Specifikaci formátu souboru ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) a umožňuje. Na systémech než Windows dekomprimovat archivy ZIP.<br />Dekomprese souboru zip vytvořil aplikaci, který cílí předchozí verze rozhraní .NET Framework v operačních systémech než Windows například Macintosh selže zachovat adresářovou strukturu. Například na Macintosh, vytvoří sadu souborů, jejichž název souboru zřetězí cesta k adresáři, spolu s jakékoli zpětné lomítko (&quot;&quot;) znaků a název souboru. V důsledku toho se nezachová struktura adresářů dekomprimovaných souborů.|
|Doporučení|Dopad na tuto změnu. Soubory ZIP, které jsou v operačním systému Windows dekomprimovat rozhraní API v rozhraní .NET Framework <xref:System.IO?displayProperty=nameWithType> oborem názvů musí být minimální, protože tato rozhraní API bez problémů zvládne dopředné lomítko (&quot;/&quot;) nebo zpětné lomítko (&quot;\&quot;) jako cestu oddělovací znak.<br />Pokud tuto změnu nežádoucí, můžete zrušit jej tak, že nastavení konfigurace, které přidáte [ < ](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace. Následující příklad ukazuje, jak <code>&lt;runtime&gt;</code> oddílu a <code>Switch.System.IO.Compression.ZipFile.UseBackslash</code> odhlásit přepínače:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Compression.ZipFile.UseBackslash=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Kromě toho, které cílí na předchozí verze rozhraní .NET Framework, ale jsou spuštěny v rozhraní .NET Framework 4.6.1 a novějším můžete přejít k toto chování tak, že nastavení konfigurace, které přidáte [ < ](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) část konfigurační soubor aplikace. Následující příklad zobrazuje i <code>&lt;runtime&gt;</code> oddílu a <code>Switch.System.IO.Compression.ZipFile.UseBackslash</code> přepínač vyjádřit výslovný souhlas.<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Compression.ZipFile.UseBackslash=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Scope|Edge|
|Version|4.6.1|
|type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean)?displayProperty=nameWithType></li><li><xref:System.IO.Compression.ZipFile.CreateFromDirectory(System.String,System.String,System.IO.Compression.CompressionLevel,System.Boolean,System.Text.Encoding)?displayProperty=nameWithType></li></ul>|

