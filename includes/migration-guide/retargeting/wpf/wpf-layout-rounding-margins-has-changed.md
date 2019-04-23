---
ms.openlocfilehash: 73096e5f61e5257e062df9743cae0f5464892357
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803649"
---
### <a name="wpf-layout-rounding-of-margins-has-changed"></a>Rozložení WPF zaokrouhlení okraje došlo ke změně

|   |   |
|---|---|
|Podrobnosti|Způsob, ve kterém jsou zaokrouhleny okraje a ohraničení a pozadí uvnitř jejich změnil. V důsledku této změny:<ul><li>Šířka nebo výška prvků může zvětšovat a zmenšovat podle maximálně jeden pixel.</li><li>Umístění objektu lze přesunout maximálně jeden pixel.</li><li>Elementy na střed lze vertikálně nebo horizontálně vypnout Centrum maximálně jeden pixel.</li></ul>Ve výchozím nastavení je toto nové rozložení povoleny pouze pro aplikace, které cílí rozhraní .NET Framework 4.6.|
|Doporučení|Vzhledem k tomu, že tato změna se obvykle Chcete-li odstranit výstřižek pravé nebo dolní ovládacích prvků WPF na vysokou dpi, aplikace, které jsou cíleny na starší verze rozhraní .NET Framework, ale jsou spuštěny v rozhraní .NET Framework 4.6 můžete začít používat toto nové chování tak, že přidáte následující řádek, který <code>&lt;runtime&gt;</code> část souboru app.config:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false&quot; /&gt;&#39;&#13;&#10;</code></pre>Aplikace, které cílí rozhraní .NET Framework 4.6, ale chcete ovládacích prvků WPF k vykreslení pomocí algoritmu předchozí rozložení můžete udělat tak, že přidáte následující řádek, který <code>&lt;runtime&gt;</code> část souboru app.config:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true&quot; /&gt;&#39;.&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.6|
|Type|Změna cílení|
