---
ms.openlocfilehash: cbe1b32fa40e509f620845866c7a584e37f49a80
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858614"
---
### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a>TargetFrameworkName pro výchozí doménu aplikace již není výchozí hodnotou null, pokud není nastavena

|   |   |
|---|---|
|Podrobnosti|Dříve <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> byla null ve výchozí doméně aplikace, pokud nebyla explicitně nastavena. Počínaje 4.6, <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> vlastnost pro výchozí doméně aplikace bude mít výchozí hodnotu odvozenou z TargetFrameworkAttribute (pokud je k dispozici). Domény aplikací, které nejsou výchozí, <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> budou nadále dědit své domény z výchozí domény aplikace (která nebude ve výchozím nastavení null v 4.6), pokud není explicitně přepsána.|
|Návrh|Kód by měl být <xref:System.AppDomainSetup.TargetFrameworkName> aktualizován tak, aby nezávisel na výchozí hodnotě null. Pokud je požadováno, aby tato vlastnost nadále vyhodnocovat na hodnotu null, může být explicitně nastavena na tuto hodnotu.|
|Rozsah|Edge|
|Version|4.6|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType></li></ul>|
