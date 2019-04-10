---
ms.openlocfilehash: 1687b1b9a1a6861f9569a0e29426de7f32ffc32b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234390"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a>IL není povolena v oblasti, zkuste vrácená hodnota:

|   |   |
|---|---|
|Podrobnosti|Na rozdíl od kompilátor just-in-time JIT64 komponentách RyuJIT (používá se v rozhraní .NET Framework 4.6) neumožňuje IL staré instrukce v oblasti try. Návrat z oblasti try se nepovoluje specifikací ECMA-335 a žádné známé spravovaný kompilátor vygeneruje taková IL. Však kompilátor JIT64 se spustí tyto IL je generována pomocí operace reflection emit.|
|Doporučení|Pokud aplikace generuje IL, který obsahuje operační kód ret v oblasti, zkuste, aplikace mohou být zaměřeny na rozhraní .NET Framework 4.5 používat staré JIT a vyhnout se této přerušení. Alternativně může být aktualizován IL generovaný vrátit zkuste oblasti.|
|Rozsah|Edge|
|Version|4.6|
|Type|Změna cílení|
