---
ms.openlocfilehash: f75a652f15be6b0d184db20dc5cd8aafd80539fe
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614581"
---
### <a name="winforms-domain-upbutton-and-downbutton-actions-are-in-sync-now"></a>DataGridView a akce DownButton v doméně se teď synchronizují.

#### <a name="details"></a>Podrobnosti

V .NET Framework 4.7.1 a předchozích verzích <xref:System.Windows.Forms.DomainUpDown> se akce ovládacího prvku <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> ignoruje, když je přítomen text ovládacího prvku a vývojář je <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> před použitím akce nutný k použití akce na ovládacím prvku <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> . Počínaje .NET Framework 4.7.2 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> akce a pracují nezávisle v tomto scénáři a zůstanou synchronizované.

#### <a name="suggestion"></a>Návrh

Aby aplikace mohla tyto změny využívat, musí běžet na .NET Framework 4.7.2 nebo novějším. Aplikace může tyto změny využít v jednom z následujících způsobů:

- Zkompiluje se znovu a zacílí na .NET Framework 4.7.2. Tato změna je ve výchozím nastavení povolená v aplikacích model Windows Forms, které cílí na .NET Framework 4.7.2 nebo novějším.
- Výslovný se starším chováním posouvání přidáním následujícího [přepínače AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) do `<runtime>` oddílu konfiguračního souboru aplikace a jeho nastavením na `false` , jak ukazuje následující příklad.

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.7.2       |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
