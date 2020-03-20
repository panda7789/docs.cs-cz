---
ms.openlocfilehash: 73096e5f61e5257e062df9743cae0f5464892357
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804599"
---
### <a name="wpf-layout-rounding-of-margins-has-changed"></a>WPF rozložení zaokrouhlení okrajů se změnilo

|   |   |
|---|---|
|Podrobnosti|Změnil se způsob, jakým jsou okraje zaoblené a ohraničení a pozadí uvnitř nich. V důsledku této změny:<ul><li>Šířka nebo výška prvků může zvětšit nebo zmenšit maximálně o jeden pixel.</li><li>Umístění objektu se může pohybovat maximálně o jeden pixel.</li><li>Vystředěné prvky mohou být svisle nebo vodorovně mimo střed maximálně o jeden pixel.</li></ul>Ve výchozím nastavení je toto nové rozložení povoleno pouze pro aplikace, které cílí na rozhraní .NET Framework 4.6.|
|Návrh|Vzhledem k tomu, že tato změna má tendenci eliminovat oříznutí pravé nebo dolní části ovládacích prvků WPF při vysokých dpi, aplikace, které cílí na starší <code>&lt;runtime&gt;</code> verze rozhraní .NET Framework, ale jsou spuštěny v rozhraní .NET Framework 4.6, se mohou přihlásit do tohoto nového chování přidáním následujícího řádku do části souboru app.config:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false&quot; /&gt;&#39;&#13;&#10;</code></pre>Aplikace, které cílí na rozhraní .NET Framework 4.6, ale chtějí, aby se <code>&lt;runtime&gt;</code> ovládací prvky WPF vykreslovali pomocí předchozího algoritmu rozložení, tak mohou provést přidáním následujícího řádku do části souboru app.config:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true&quot; /&gt;&#39;.&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|Změna cílení|
