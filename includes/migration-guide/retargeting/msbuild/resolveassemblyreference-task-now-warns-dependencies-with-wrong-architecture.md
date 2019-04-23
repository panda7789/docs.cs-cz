---
ms.openlocfilehash: 39a329597ef28e002242103a247515d94761676a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774369"
---
### <a name="resolveassemblyreference-task-now-warns-of-dependencies-with-the-wrong-architecture"></a>Resolveassemblyreference – úloha teď upozorňuje na závislosti pomocí nesprávného architektury

|   |   |
|---|---|
|Podrobnosti|Úloha vysílá varování, MSB3270, což znamená, že odkaz nebo některá z jejích závislostí neodpovídá architektuře aplikace. Například dochází k tomu, který byl zkompilován pomocí aplikace <code>AnyCPU</code> x x86 zahrnuje možnost odkaz. Takový scénář může vést k selhání aplikace za běhu (v tomto případě v případě, že je aplikace nasazená jako x x64 proces).|
|Doporučení|Existují dvě oblasti dopad na chod firmy:<ul><li>Rekompilace generuje upozornění, která se neobjevil při kompilaci aplikace v předchozí verzi nástroje MSBuild. Ale vzhledem k tomu, že toto upozornění identifikuje stávají možným zdrojem chyby, ji by měl být prozkoumat a zákazníky a vyřešené.</li><li>Pokud jsou upozornění zpracována jako chyby, aplikace se nepodaří zkompilovat.</li></ul>|
|Rozsah|Vedlejší|
|Version|4.5.1|
|Type|Změna cílení|
