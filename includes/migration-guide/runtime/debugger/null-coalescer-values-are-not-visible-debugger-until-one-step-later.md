---
ms.openlocfilehash: 22f8e3bb1ba72379b3f5fc87a077e5fe57f89bf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858841"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a>Hodnoty null coalescer nejsou viditelné v ladicím programu až o krok později

|   |   |
|---|---|
|Podrobnosti|Chyba v rozhraní .NET Framework 4.5 způsobí, že hodnoty nastavené prostřednictvím operace null coalescing nebudou viditelné v ladicím programu ihned po spuštění operace přiřazení při spuštění v 64bitové verzi rozhraní Framework.|
|Návrh|Krokování jeden další čas v ladicím programu způsobí, že hodnota místní/pole správně aktualizovány. Tento problém byl také vyřešen v rozhraní .NET Framework 4.6; upgrade na tuto verzi rozhraní Framework by měl problém vyřešit.|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|
