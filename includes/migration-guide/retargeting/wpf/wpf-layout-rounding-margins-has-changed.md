---
ms.openlocfilehash: f907cb1939e111c586d68243e6b8a8e291974e36
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615720"
---
### <a name="wpf-layout-rounding-of-margins-has-changed"></a>Změnilo se zaokrouhlování rozložení WPF pro okraje.

#### <a name="details"></a>Podrobnosti

Způsob, jakým jsou zaoblené okraje zaokrouhleny a ohraničení a pozadí uvnitř nich bylo změněno. V důsledku této změny:

- Šířka nebo výška prvků může být zvětšena nebo zmenšena o jeden pixel.
- Umístění objektu lze přesunout o jeden pixel.
- Centrované elementy můžou být svisle nebo vodorovně mimo střed o jeden pixel.
Ve výchozím nastavení je toto nové rozložení povolené jenom pro aplikace, které cílí na .NET Framework 4,6.

#### <a name="suggestion"></a>Návrh

Vzhledem k tomu, že tato změna je v úmyslu zabránit tomu, aby se vyloučilo oříznutí pravé nebo dolní části ovládacích prvků WPF s vysokou dpi, aplikace, které cílí na starší verze .NET Framework, ale jsou spuštěné v .NET Framework 4,6, se můžou na toto nové chování zúčastnit přidáním následujícího řádku do `<runtime>` oddílu app.config souboru:

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false&quot; /&gt;&#39;&#13;&#10;</code></pre>

Aplikace cílené na .NET Framework 4,6, ale chcete, aby ovládací prvky WPF vykreslují pomocí předchozího algoritmu rozložení, mohou tak učinit přidáním následujícího řádku do `<runtime>` části app.config souboru:

<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true&quot; /&gt;&#39;.&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.6         |
| Typ    | Změna cílení |
