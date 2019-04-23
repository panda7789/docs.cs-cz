---
ms.openlocfilehash: 22f8e3bb1ba72379b3f5fc87a077e5fe57f89bf8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981615"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a>Hodnoty Null coalescer nejsou viditelné v ladicím programu až do jednoho kroku později

|   |   |
|---|---|
|Podrobnosti|Chyby v rozhraní .NET Framework 4.5 způsobí, že hodnoty nastavené přes operaci sloučení null nebude viditelné v ladicím programu okamžitě po provedení operace přiřazení je spuštěná v 64bitové verzi rozhraní Framework.|
|Doporučení|Krokování další jednou v ladicím programu způsobí, že místní/hodnoty tohoto pole správně aktualizovat. Navíc tento problém byl vyřešen v rozhraní .NET Framework 4.6; upgrade na tuto verzi rozhraní Framework by mělo vyřešit problém.|
|Rozsah|Edge|
|Version|4.5|
|Type|Modul runtime|
