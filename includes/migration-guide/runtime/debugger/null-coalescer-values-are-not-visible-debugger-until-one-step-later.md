---
ms.openlocfilehash: c1a2d76b4e596acc395da6cefed008078e57a336
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858841"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a>Hodnoty Null coalescer nejsou viditelné v ladicím programu až do jednoho kroku později

|   |   |
|---|---|
|Podrobnosti|Chyby v rozhraní .NET Framework 4.5 způsobí, že hodnoty nastavené přes operaci sloučení null nebude viditelné v ladicím programu okamžitě po provedení operace přiřazení je spuštěná v 64bitové verzi rozhraní Framework.|
|Doporučení|Krokování další jednou v ladicím programu způsobí, že místní/hodnoty tohoto pole správně aktualizovat. Navíc tento problém byl vyřešen v rozhraní .NET Framework 4.6; upgrade na tuto verzi rozhraní Framework by mělo vyřešit problém.|
|Scope|Edge|
|Version|4.5|
|type|Modul runtime|

