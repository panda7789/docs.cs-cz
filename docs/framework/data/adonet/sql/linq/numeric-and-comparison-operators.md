---
title: Číselné a porovnávací operátory
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: e2bdc55cd6c2203bc96d0766e5e53a57294d4d7e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554709"
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
  
    -   Visual Basic `=` and C# `==`  
  
    -   Visual Basic `<>` and C# `!=`  
  
    -   Visual Basic `Is/IsNot`  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## <a name="see-also"></a>Viz také:
- [Datové typy a funkce](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
- [Operátory jazyka C#](../../../../../../docs/csharp/language-reference/operators/index.md)
- [Operátory](../../../../../visual-basic/language-reference/operators/index.md)
