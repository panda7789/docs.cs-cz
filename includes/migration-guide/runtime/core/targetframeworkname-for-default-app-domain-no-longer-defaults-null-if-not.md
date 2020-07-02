---
ms.openlocfilehash: f955e270f709ddf6eea2e44bbcf386e372b9f6e3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621136"
---
### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a>Hodnota vlastnosti TargetFramework pro výchozí doménu aplikace už není nastavená na hodnotu null.

#### <a name="details"></a>Podrobnosti

<xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName>Dříve byla ve výchozí doméně aplikace null, pokud nebyla explicitně nastavena. Počínaje 4,6 <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> bude mít vlastnost pro výchozí doménu aplikace výchozí hodnotu odvozenou od TargetFrameworkAttribute (Pokud je k dispozici). Domény aplikací, které nejsou výchozí, budou nadále dědit <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> z výchozí domény aplikace (nejedná se o výchozí hodnotu null v 4,6), pokud není explicitně přepsána.

#### <a name="suggestion"></a>Návrh

Kód by měl být aktualizován na nezávisle na <xref:System.AppDomainSetup.TargetFrameworkName> výchozím nastavení na hodnotu null. Pokud je nutné, aby se tato vlastnost i nadále vyhodnotila na hodnotu null, může být explicitně nastavena na tuto hodnotu.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.6|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType></li></ul>|
