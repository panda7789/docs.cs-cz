---
title: Číselné a porovnávací operátory
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: 7e7af725864aa191f092055fa32b403093321aa5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781296"
---
# <a name="numeric-and-comparison-operators"></a>Číselné a porovnávací operátory

Aritmetické a relační operátory pracují podle očekávání v modulu CLR (Common Language Runtime), s výjimkou následujících:

- SQL nepodporuje operátor dělení na číslech s plovoucí desetinnou čárkou.

- SQL nepodporuje nekontrolované aritmetické operace.

- Operátory přírůstku a snížení způsobují vedlejší účinky při jejich použití ve výrazech, které nelze replikovat v SQL a jsou proto podporovány.

## <a name="supported-operators"></a>Podporované operátory

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]podporuje následující operátory.

- Základní aritmetické operátory:

  - `+`

  - `-`odčítání

  - `*`

  - `/`

  - Visual Basic celočíselné dělení`\`()

  - `%`(Visual Basic `Mod`)

  - `<<`

  - `>>`

  - `-`(unární negace)

- Základní operátory porovnání:

  - Visual Basic `=` a C#`==`

  - Visual Basic `<>` a C#`!=`

  - Visual Basic`Is/IsNot`

  - `<`

  - `<=`

  - `>`

  - `>=`

## <a name="see-also"></a>Viz také:

- [Datové typy a funkce](data-types-and-functions.md)
- [Operátory jazyka C#](../../../../../csharp/language-reference/operators/index.md)
- [Operátory](../../../../../visual-basic/language-reference/operators/index.md)
