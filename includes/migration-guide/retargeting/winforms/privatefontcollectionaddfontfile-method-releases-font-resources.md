---
ms.openlocfilehash: f5d93d76ab3409d4d4c1870cfef94cac59f9475c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59233954"
---
### <a name="privatefontcollectionaddfontfile-method-releases-font-resources"></a>Metoda PrivateFontCollection.AddFontFile uvolní prostředky písma

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.7.1 a předchozí verze <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> třídy neuvolní prostředků písem GDI + po <xref:System.Drawing.Text.PrivateFontCollection> uvolnění pro <xref:System.Drawing.Font> objekty, které se přidají do této kolekce pomocí <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)> metoda. V rozhraní .NET Framework 4.7.2 a později <xref:System.Drawing.Text.FontCollection.Dispose%2A> aktualizací, které byly přidány do kolekce jako soubory písem GDI +.|
|Doporučení|<strong>Jak aktivování nebo zrušení těchto změn</strong>aby aplikace využívat tyto změny, musíte spustit na rozhraní .NET Framework 4.7.2 nebo novější. Aplikace mohou těžit z těchto změn v některém z následujících způsobů:<ul><li>Ji znovu zkompilovat cíleny na rozhraní.NET Framework 4.7.2. Tato změna je ve výchozím nastavení cíleny na rozhraní.NET Framework 4.7.2 aplikací Windows Forms pro povolená nebo novější.</li><li>Cílí na rozhraní .NET Framework 4.7.1 nebo starší verzi a výslovný chování starších verzí usnadnění přidáním následujícího kódu [přepínač AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) k <code>&lt;runtime&gt;</code> část souboru app.config a nastavíte ho na <code>false</code>, jak ukazuje následující příklad.</li></ul><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Drawing.Text.DoNotRemoveGdiFontsResourcesFromFontCollection=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Aplikace, které se zaměřují na rozhraní .NET Framework 4.7.2 nebo novější a chcete zachovat starší chování se mohou přihlásit a explicitním nastavením na tento přepínač AppContext vydané zdroje písma <code>true</code>.|
|Rozsah|Edge|
|Version|4.7.2|
|Type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType></li><li><xref:System.Drawing.Text.FontCollection.Dispose?displayProperty=nameWithType></li></ul>|
