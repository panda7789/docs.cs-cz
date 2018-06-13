---
title: Číselné a relační operátory
ms.date: 03/30/2017
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
ms.openlocfilehash: a1ce13225d72b4286982434d52998a1913814abb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352178"
---
# <a name="numeric-and-comparison-operators"></a>Číselné a relační operátory
Porovnání a aritmetické operátory fungovat podle očekávání v common language runtime (CLR) s výjimkou následujícím způsobem:  
  
-   SQL nepodporuje operátor numerického zbytku na čísla s plovoucí desetinnou čárkou.  
  
-   SQL nepodporuje aritmetické nezaškrtnuté.  
  
-   Operátory přírůstku a snížení způsobit vedlejší účinky, když je budete používat ve výrazech, které nelze replikovat v systému SQL a, proto nejsou podporovány.  
  
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
  
-   Operátory porovnání základní:  
  
    -   Visual Basic `=` a C# `==`  
  
    -   Visual Basic `<>` a C# `!=`  
  
    -   Visual Basic `Is/IsNot`  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## <a name="see-also"></a>Viz také  
 [Datové typy a funkce](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)  
 [Operátory jazyka C#](http://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43)  
 [Operátory](../../../../../visual-basic/language-reference/operators/index.md)
