---
ms.openlocfilehash: 705e1a22b8a5791c1103dd374a8bab19356cadfb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803252"
---
### <a name="ef-no-longer-throws-for-queryviews-with-specific-characteristics"></a>EF již vyvolá pro QueryViews se specifickými charakteristikami

|   |   |
|---|---|
|Podrobnosti|Entity Framework již vyvolá <xref:System.StackOverflowException?displayProperty=name> výjimku, když aplikace spustí dotaz, který zahrnuje QueryView s vlastností navigace 0..1, která se pokusí zahrnout související entity jako součást dotazu. Například voláním <code>.Include(e =&gt; e.RelatedNavProp)</code>.|
|Návrh|Tato změna ovlivní pouze kód, který používá QueryViews se vztahy 1-0..1 při spouštění dotazů, které volají . Zahrnout. Zvyšuje spolehlivost a měl by být transparentní pro téměř všechny aplikace. Pokud však způsobí neočekávané chování, můžete ho zakázat <code>&lt;appSettings&gt;</code> přidáním následující položky do části konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyUserSpecifiedViews&quot; value=&quot;false&quot; /&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.5.2|
|Typ|Modul runtime|
