---
ms.openlocfilehash: 4d410811095786b33580d25f6c6eab3ac2f27148
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616045"
---
### <a name="resolveassemblyreference-task-now-warns-of-dependencies-with-the-wrong-architecture"></a>Úloha ResolveAssemblyReference – teď upozorňuje na závislosti s nesprávnou architekturou.

#### <a name="details"></a>Podrobnosti

Úkol vygeneruje upozornění, MSB3270, což indikuje, že odkaz nebo kterákoli z jeho závislostí neodpovídá architektuře aplikace. Například k tomu dochází, pokud aplikace, která byla zkompilována s `AnyCPU` možností, obsahuje odkaz x86. Takový scénář může způsobit selhání aplikace v době běhu (v tomto případě, pokud je aplikace nasazená jako proces x64).

#### <a name="suggestion"></a>Návrh

Existují dvě oblasti dopadu:

- Opětovná kompilace generuje upozornění, která se nezobrazí, když byla aplikace zkompilována v předchozí verzi nástroje MSBuild. Vzhledem k tomu, že upozornění identifikuje možný zdroj selhání za běhu, mělo by se prozkoumat a vyřešit.
- Pokud jsou upozornění považována za chyby, aplikace se nepodaří zkompilovat.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.5.1       |
| Typ    | Změna cílení |
