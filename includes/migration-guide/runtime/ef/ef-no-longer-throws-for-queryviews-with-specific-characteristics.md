---
ms.openlocfilehash: c6c897c13c84ce4b2be21da18e5702365518f286
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620026"
---
### <a name="ef-no-longer-throws-for-queryviews-with-specific-characteristics"></a>EF již nevyvolává pro QueryViews s konkrétními charakteristikami

#### <a name="details"></a>Podrobnosti

Entity Framework už nevyvolává <xref:System.StackOverflowException?displayProperty=fullName> výjimku, když aplikace spustí dotaz, který zahrnuje QueryView s vlastností navigace 0.. 1, která se pokusí zahrnout související entity jako součást dotazu. Například voláním metody <code>.Include(e =&gt; e.RelatedNavProp)</code> .

#### <a name="suggestion"></a>Návrh

Tato změna má vliv pouze na kód, který používá QueryViews s 1 – 0.. 1 relacemi při spouštění dotazů, které volají. Připojit. Zlepšuje spolehlivost a měla by být transparentní pro téměř všechny aplikace. Pokud ale dojde k neočekávanému chování, můžete ho zakázat přidáním následujícího záznamu do <code>&lt;appSettings&gt;</code> části konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyUserSpecifiedViews&quot; value=&quot;false&quot; /&gt;&#13;&#10;</code></pre>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5.2|
|Typ|Modul runtime|
