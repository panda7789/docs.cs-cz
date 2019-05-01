---
ms.openlocfilehash: 39a329597ef28e002242103a247515d94761676a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62088472"
---
### <a name="resolveassemblyreference-task-now-warns-of-dependencies-with-the-wrong-architecture"></a>Resolveassemblyreference – úloha teď upozorňuje na závislosti pomocí nesprávného architektury

|   |   |
|---|---|
|Podrobnosti|Úloha vysílá varování, MSB3270, což znamená, že odkaz nebo některá z jejích závislostí neodpovídá architektuře aplikace. Například dochází k tomu, který byl zkompilován pomocí aplikace <code>AnyCPU</code> x x86 zahrnuje možnost odkaz. Takový scénář může vést k selhání aplikace za běhu (v tomto případě v případě, že je aplikace nasazená jako x x64 proces).|
|Doporučení|Existují dvě oblasti dopad na chod firmy:<ul><li>Rekompilace generuje upozornění, která se neobjevil při kompilaci aplikace v předchozí verzi nástroje MSBuild. Ale vzhledem k tomu, že toto upozornění identifikuje stávají možným zdrojem chyby, ji by měl být prozkoumat a zákazníky a vyřešené.</li><li>Pokud jsou upozornění zpracována jako chyby, aplikace se nepodaří zkompilovat.</li></ul>|
|Rozsah|Vedlejší|
|Version|4.5.1|
|Type|Změna cílení|
