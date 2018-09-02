---
title: Číselné a porovnávací operátory
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: a7a455730860e2b11a5ceff5a70934502b312e19
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401912"
---
# <a name="numeric-and-comparison-operators"></a>Číselné a porovnávací operátory
Aritmetické operace a porovnání operátory fungovat podle očekávání v modulu common language runtime (CLR) s výjimkou následujícím způsobem:  
  
-   SQL nepodporuje operátor numerického zbytku na čísla s plovoucí desetinnou čárkou.  
  
-   SQL nepodporuje Nekontrolovaná aritmetické operace.  
  
-   Operátory přírůstku a snížení způsobit vedlejší účinky při použití ve výrazech, které nelze replikovat v SQL a, proto nejsou podporovány.  
  
## <a name="supported-operators"></a>Podporované operátory  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] podporuje následující operátory.  
  
-   Základní aritmetické operátory:  
  
    -   `+`  
  
    -   `-` (odčítání)  
  
    -   `*`  
  
    -   `/`  
  
    -   Dělení celého čísla v jazyce Visual Basic (`\`)  
  
    -   `%` (Visual Basic `Mod`)  
  
    -   `<<`  
  
    -   `>>`  
  
    -   `-` (unární negace)  
  
-   Základní relační operátory:  
  
    -   Visual Basic `=` a C# `==`  
  
    -   Visual Basic `<>` a C# `!=`  
  
    -   Visual Basic `Is/IsNot`  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## <a name="see-also"></a>Viz také  
 [Datové typy a funkce](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)  
 [Operátory jazyka C#](https://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43)  
 [Operátory](../../../../../visual-basic/language-reference/operators/index.md)
