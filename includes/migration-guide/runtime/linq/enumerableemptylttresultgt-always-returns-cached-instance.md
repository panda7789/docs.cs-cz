---
ms.openlocfilehash: 9131c91b34f4c24653dea37ea39af6be6e072287
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620032"
---
### <a name="enumerableemptylttresultgt-always-returns-cached-instance"></a>Vyčíslitelné. Empty &lt; TResult &gt; vždycky vrátí instanci uloženou v mezipaměti

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4,5 <xref:System.Linq.Enumerable.Empty%60%601> vždy vrátí interní instanci uloženou v mezipaměti <xref:System.Collections.Generic.IEnumerable%601> . Dřív <xref:System.Linq.Enumerable.Empty%60%601> by do mezipaměti bylo v <xref:System.Collections.Generic.IEnumerable%601> době volání rozhraní API prázdné, což znamená, že v některých podmínkách, které <xref:System.Linq.Enumerable.Empty%60%601> byly volány rychle a souběžně, mohou být vráceny různé instance typu pro různá volání rozhraní API.

#### <a name="suggestion"></a>Návrh

Vzhledem k tomu, že předchozí chování nebylo deterministické, je pravděpodobné, že na něm závisí kód. Nicméně v nepravděpodobném případě, že jsou vypočítány prázdné výčty a očekává se, že jsou někdy stejné, explicitní prázdná pole by měla být vytvořena ( <code>new T[0]</code> ) namísto použití <xref:System.Linq.Enumerable.Empty%60%601> .

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Linq.Enumerable.Empty%60%601?displayProperty=nameWithType></li></ul>|
