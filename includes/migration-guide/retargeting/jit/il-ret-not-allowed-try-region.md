---
ms.openlocfilehash: 060da3ebc60057554fd572bd2569652afee6bd0f
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804493"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a>IL není povolena v oblasti, zkuste vrácená hodnota:

|   |   |
|---|---|
|Podrobnosti|Na rozdíl od kompilátor just-in-time JIT64 komponentách RyuJIT (používá se v rozhraní .NET Framework 4.6) neumožňuje IL staré instrukce v oblasti try. Návrat z oblasti try se nepovoluje specifikací ECMA-335 a žádné známé spravovaný kompilátor vygeneruje taková IL. Však kompilátor JIT64 se spustí tyto IL je generována pomocí operace reflection emit.|
|Doporučení|Pokud aplikace generuje IL, který obsahuje operační kód ret v oblasti, zkuste, aplikace mohou být zaměřeny na rozhraní .NET Framework 4.5 používat staré JIT a vyhnout se této přerušení. Alternativně může být aktualizován IL generovaný vrátit zkuste oblasti.|
|Scope|Edge|
|Version|4.6|
|type|Změna cílení|

