---
ms.openlocfilehash: 08ad6fd4ccb6d5ddbbb4fa7ef1b325ce30689748
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621124"
---
### <a name="appdomainsetupdynamicbase-is-no-longer-randomized-by-userandomizedstringhashalgorithm"></a>AppDomainSetup. DynamicBase již není vyrandomizované pomocí UseRandomizedStringHashAlgorithm

#### <a name="details"></a>Podrobnosti

Před .NET Framework 4,6 hodnota <xref:System.AppDomainSetup.DynamicBase> by byla náhodné mezi doménami aplikace nebo mezi procesy, pokud byl UseRandomizedStringHashAlgorithm v konfiguračním souboru aplikace povolen. Počínaje .NET Framework 4,6 <xref:System.AppDomainSetup.DynamicBase> se vrátí stabilní výsledek mezi různými instancemi aplikace spuštěné a mezi různými doménami aplikace. Dynamické základny se pořád pro různé aplikace liší. Tato změna odebírá pouze náhodný element pojmenovávání pro různé instance stejné aplikace.

#### <a name="suggestion"></a>Návrh

Mějte na paměti, že povolení <code>UseRandomizedStringHashAlgorithm</code> nebude mít za následek <xref:System.AppDomainSetup.DynamicBase> náhodné. Pokud je třeba náhodný základ, musí být vytvořen v kódu vaší aplikace, nikoli prostřednictvím tohoto rozhraní API.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.6|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.AppDomainSetup.DynamicBase?displayProperty=nameWithType></li></ul>|
