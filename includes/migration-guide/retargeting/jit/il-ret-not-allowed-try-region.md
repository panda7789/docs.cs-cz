---
ms.openlocfilehash: 1687b1b9a1a6861f9569a0e29426de7f32ffc32b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804493"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a>IL ret není povoleno v oblasti try

|   |   |
|---|---|
|Podrobnosti|Na rozdíl od kompilátoru just-in-time JIT64 RyuJIT (používaný v rozhraní .NET Framework 4.6) neumožňuje instrukce IL ret v oblasti try. Vrácení z oblasti try je zakázáno specifikací ECMA-335 a žádný známý spravovaný kompilátor negeneruje takové IL. Kompilátor JIT64 však provede takové IL, pokud je generován pomocí odrazem emit.|
|Návrh|Pokud aplikace generuje IL, který obsahuje ret opcode v oblasti try, aplikace může cílit .NET Framework 4.5 použít staré JIT a vyhnout se této přestávce. Alternativně generované IL může být aktualizován vrátit po try oblasti.|
|Rozsah|Edge|
|Version|4.6|
|Typ|Změna cílení|
