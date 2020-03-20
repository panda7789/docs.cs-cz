---
ms.openlocfilehash: 3f553f95941eaf36cf335e9765a670a05bd157f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858478"
---
### <a name="appdomainsetupdynamicbase-is-no-longer-randomized-by-userandomizedstringhashalgorithm"></a>Soubor AppDomainSetup.DynamicBase již není randomizován pomocí metody UseRandomizedStringHashAlgorithm

|   |   |
|---|---|
|Podrobnosti|Před rozhraním .NET Framework 4.6 <xref:System.AppDomainSetup.DynamicBase> by byla hodnota randomizována mezi aplikačními doménami nebo mezi procesy, pokud byl v konfiguračním souboru aplikace povolen apovolen. Počínaje rozhraním .NET Framework <xref:System.AppDomainSetup.DynamicBase> 4.6 vrátí stabilní výsledek mezi různými instancemi spuštěné aplikace a mezi různými doménami aplikací. Dynamické základy se budou pro různé aplikace stále lišit; Tato změna odebere pouze náhodný prvek pojmenování pro různé instance stejné aplikace.|
|Návrh|Uvědomte si, že <code>UseRandomizedStringHashAlgorithm</code> <xref:System.AppDomainSetup.DynamicBase> povolení nebude mít za následek randomizované. Pokud je potřeba náhodná základna, musí být vytvořena v kódu vaší aplikace, nikoli prostřednictvím tohoto rozhraní API.|
|Rozsah|Edge|
|Version|4.6|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.AppDomainSetup.DynamicBase?displayProperty=nameWithType></li></ul>|
