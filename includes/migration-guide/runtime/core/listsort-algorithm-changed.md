---
ms.openlocfilehash: 9dada93c3330331064b7a944d97d61edb4dea299
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619981"
---
### <a name="listsort-algorithm-changed"></a>List. Sort – algoritmus se změnil.

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4,5 se <xref:System.Collections.Generic.List%601?displayProperty=fullName> algoritmus řazení změnil (aby bylo řazení introspective místo rychlého řazení). <xref:System.Collections.Generic.List%601?displayProperty=fullName>řazení nikdy nebylo stabilní, ale tato změna může způsobit nestabilní způsoby řazení různých scénářů. To jednoduše znamená, že ekvivalentní položky mohou být seřazeny v různých objednávkách v následných voláních rozhraní API.

#### <a name="suggestion"></a>Návrh

Vzhledem k tomu, že starý algoritmus řazení byl také nestabilní (ale mírně různými způsoby), neměl by být žádný kód, který závisí na ekvivalentních položkách, vždy řadit v určitém pořadí. Pokud existují instance kódu v závislosti na tom, že se štěstí se starým chováním, měl by se tento kód aktualizovat, aby se použila porovnávací položka, která bude deterministické seřazení položek v požadovaném pořadí.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Průhlednost|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Collections.Generic.List%601.Sort?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Comparison{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li></ul>|
