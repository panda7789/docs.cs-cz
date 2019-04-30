---
ms.openlocfilehash: cbe1b32fa40e509f620845866c7a584e37f49a80
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664410"
---
### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a>TargetFrameworkName výchozí domény aplikace už výchozí hodnota je null, pokud není nastavena

|   |   |
|---|---|
|Podrobnosti|<xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> Byla dříve null ve výchozí doméně aplikace, pokud explicitně nastaven. Počínaje 4.6, <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> vlastnost pro výchozí doméně aplikace bude mít výchozí hodnotu odvozený od TargetFrameworkAttribute (Pokud je k dispozici). Domén nestandardní aplikace budou i nadále dědit jejich <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> z výchozí doméně aplikace (které se ve výchozím nastavení hodnotu null v 4.6) Pokud není explicitně přepsána.|
|Doporučení|Kód se musí aktualizovat na nezávisí na <xref:System.AppDomainSetup.TargetFrameworkName> jako výchozí se použije na hodnotu null. Pokud se vyžaduje, aby tato vlastnost i nadále vyhodnotit na hodnotu null, můžete explicitně nastavit na tuto hodnotu.|
|Rozsah|Edge|
|Version|4.6|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType></li></ul>|
