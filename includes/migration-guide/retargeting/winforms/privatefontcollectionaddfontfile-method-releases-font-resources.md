---
ms.openlocfilehash: 53ded5ae6e5a025fc7992da099c3481587bb6f31
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614580"
---
### <a name="privatefontcollectionaddfontfile-method-releases-font-resources"></a>Metoda PrivateFontCollection. AddFontFile uvolní prostředky písma.

#### <a name="details"></a>Podrobnosti

V .NET Framework 4.7.1 a předchozích verzích <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> Třída neuvolní prostředky písma GDI+ po <xref:System.Drawing.Text.PrivateFontCollection> uvolnění pro <xref:System.Drawing.Font> objekty, které jsou přidány do této kolekce pomocí <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)> metody. Ve .NET Framework 4.7.2 a novější <xref:System.Drawing.Text.FontCollection.Dispose%2A> verze vydává písma GDI+, která byla přidána do kolekce jako soubory.

#### <a name="suggestion"></a>Návrh

**Jak vyjádřit nebo odhlásit tyto změny** Aby aplikace mohla tyto změny využívat, musí běžet na .NET Framework 4.7.2 nebo novějším. Aplikace může tyto změny využít v jednom z následujících způsobů:

- Zkompiluje se znovu a zacílí na .NET Framework 4.7.2. Tato změna je ve výchozím nastavení povolená v aplikacích model Windows Forms, které cílí na .NET Framework 4.7.2 nebo novějším.
- Cílí na .NET Framework 4.7.1 nebo dřívější verzi a výslovný ze staršího chování přístupnosti přidáním následujícího [přepínače AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) do `<runtime>` oddílu app.config souboru a jeho nastavením na `false` , jak ukazuje následující příklad.

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Drawing.Text.DoNotRemoveGdiFontsResourcesFromFontCollection=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

Aplikace, které cílí na .NET Framework 4.7.2 nebo novější a chtějí zachovat starší verze chování, se můžou rozhodnout, že neuvolní prostředky písma explicitním nastavením tohoto přepínače AppContext na `true` .

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.7.2       |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType>
- <xref:System.Drawing.Text.FontCollection.Dispose?displayProperty=nameWithType>
