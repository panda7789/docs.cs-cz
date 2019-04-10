---
ms.openlocfilehash: 22f8e3bb1ba72379b3f5fc87a077e5fe57f89bf8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235219"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a>Hodnoty Null coalescer nejsou viditelné v ladicím programu až do jednoho kroku později

|   |   |
|---|---|
|Podrobnosti|Chyby v rozhraní .NET Framework 4.5 způsobí, že hodnoty nastavené přes operaci sloučení null nebude viditelné v ladicím programu okamžitě po provedení operace přiřazení je spuštěná v 64bitové verzi rozhraní Framework.|
|Doporučení|Krokování další jednou v ladicím programu způsobí, že místní/hodnoty tohoto pole správně aktualizovat. Navíc tento problém byl vyřešen v rozhraní .NET Framework 4.6; upgrade na tuto verzi rozhraní Framework by mělo vyřešit problém.|
|Rozsah|Edge|
|Version|4.5|
|Type|Modul runtime|
