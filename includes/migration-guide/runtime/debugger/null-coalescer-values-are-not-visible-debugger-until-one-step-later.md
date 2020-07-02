---
ms.openlocfilehash: 907c4aa5573c392a68afad0a4d937eadcd556440
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620008"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a>Hodnoty null coalescer nejsou v ladicím programu viditelné, dokud jeden krok později

#### <a name="details"></a>Podrobnosti

Chyba v .NET Framework 4,5 způsobí, že hodnoty nastavené prostřednictvím operace sloučení s hodnotou null nejsou viditelné v ladicím programu ihned po provedení operace přiřazení, pokud je spuštěná v 64 bitové verzi rozhraní .NET Framework.

#### <a name="suggestion"></a>Návrh

Krokování jednoho dalšího času v ladicím programu způsobí, že hodnota místního/pole bude správně aktualizována. Tento problém se také vyřešil v .NET Framework 4,6; upgrade na tuto verzi rozhraní by měl vyřešit tento problém.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime|
