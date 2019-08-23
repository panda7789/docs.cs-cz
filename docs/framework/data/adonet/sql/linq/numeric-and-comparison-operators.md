---
title: Číselné a porovnávací operátory
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: ff54856a66ad5e9c0362c013f8df5f1147055cd0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915712"
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

- [Datové typy a funkce](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
- [Operátory jazyka C#](../../../../../csharp/language-reference/operators/index.md)
- [Operátory](../../../../../visual-basic/language-reference/operators/index.md)
